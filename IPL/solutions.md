1. The percentage of wins of each bidder in the order of highest to lowest percentage.

```sql
select IBD.BIDDER_ID, IBD.BIDDER_NAME, (bd_won.wins/no_of_bids)*100 as Percentage_of_Wins
from IPL_BIDDER_DETAILS IBD
inner join IPL_BIDDER_POINTS IBP
on IBD.BIDDER_ID = IBP.BIDDER_ID 
inner join (
	select BIDDER_ID, count(BID_STATUS) as wins
	from IPL_BIDDING_DETAILS 
	where BID_STATUS = 'won'
	group by BIDDER_ID ) as bd_won
on IBP.BIDDER_ID = bd_won.BIDDER_ID   
group by IBD.BIDDER_ID, IBD.BIDDER_NAME
order by Percentage_of_Wins desc;
```

2. The number of matches conducted at each stadium with stadium name, city from the database.

```sql
select STADIUM_NAME, CITY, `Count of match` from (
SELECT STADIUM_ID, count(STADIUM_ID) as `Count of match`
FROM IPL_MATCH_SCHEDULE  
group by STADIUM_ID ) t
join IPL_STADIUM as IPS
on t.STADIUM_ID  = IPS.STADIUM_ID
order by `Count of match`;
```

3. In a given stadium, what is the percentage of wins by a team which has won the toss?


```sql
select ttt.STADIUM_ID , STADIUM_NAME,MATCH_WINNER , cume_dist() over(partition by MATCH_WINNER,STADIUM_ID)
from (
select MATCh_ID1 , STADIUM_ID,
case
when MATCH_WINNER = 2 then TEAM_ID2
WHEN MATCH_WINNER = 1 then TEAM_ID1
end AS MATCH_WINNER
from (
select MATCh_ID1, TEAM_ID1, TEAM_ID2, MATCH_WINNER from (
select *,
case 
when TOSS_WINNER = MATCH_WINNER then MATCH_ID
end as MATCh_ID1
from IPL_MATCH ) t
where MATCh_ID1 is not null) tt
join IPL_MATCH_SCHEDULE as IMS
ON tt.MATCh_ID1  = IMS.MATCh_ID ) ttt
join IPL_STADIUM as `IPLS`
ON ttt.STADIUM_ID = IPLS.STADIUM_ID
order by STADIUM_ID, MATCH_WINNER;
```

4. The total bids along with bid team and team name.

```sql
select BID_TEAM,TEAM_NAME,`Total Bids`  
from (
SELECT BID_TEAM,  count(BID_TEAM) as `Total Bids`
FROM IPL_BIDDING_DETAILS as IBD
group by BID_TEAM ) as tt
join IPL_TEAM as IT 
on tt.BID_TEAM = IT.TEAM_ID;
```


5. The team id who won the match as per the win details.


```sql
select tt.TEAM_ID, IT.TEAM_NAME from (
select 
case
when MATCH_WINNER = 1 then  TEAM_ID1
when MATCH_WINNER = 2 then  TEAM_ID2
end TEAM_ID
from IPL_MATCH ) tt
join IPL_TEAM as IT
on tt.TEAM_ID = IT.TEAM_ID;
```

6. Total matches played, total matches won and total matches lost by team along with its team name.

```sql
select ITS.TEAM_ID, IT.TEAM_NAME, 
	sum(MATCHES_PLAYED) MATCHES_PLAYED, 
	sum(MATCHES_WON) MATCHES_WON, 
	sum(MATCHES_LOST) MATCHES_LOST  
from IPL_TEAM_STANDINGS AS ITS
join IPL_TEAM as IT
ON ITS.TEAM_ID = IT.TEAM_ID
group by TEAM_ID;
```


7. The bowlers for Mumbai Indians team.

```sql
select  ITP.TEAM_ID, IP.PLAYER_NAME, ITP.PLAYER_ROLE, ITP.REMARKS 
from IPL_TEAM_PLAYERS as ITP
join IPL_PLAYER as IP
on ITP.PLAYER_ID  = IP.PLAYER_ID
where PLAYER_ROLE = 'Bowler' and ITP.REMARKS = 'TEAM - MI';   
```


8. How many all-rounders are there in each team, display the teams with more than 4 all-rounder in descending order.


```sql
select tt.TEAM_ID, IT.TEAM_NAME, tt.`count` from (
select  TEAM_ID, count(PLAYER_ROLE) as `count`  from IPL_TEAM_PLAYERS 
where PLAYER_ROLE = 'All-Rounder'
group by TEAM_ID ) tt
join IPL_TEAM as IT
on tt.TEAM_ID = IT.TEAM_ID
where `count` > 4
order by `count` desc;
```
