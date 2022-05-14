1. Table: **IPL_User**


| Column name | 	Data type |	Comments |
| --- | --- | --- |
|UserId	|VARCHAR|	Primary key|
|Password	|VARCHAR	|Not null, encrypted format|
|User_type	|VARCHAR|	Admin or Bidder. Not null|
|Remarks |	VARCHAR	|
<br>


2.	Table: IPL_Stadium

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|StadiumId|	NUMBER	|Primary key
|Stadium_name	|VARCHAR	|Unique, Not null
|City|	VARCHAR	|
|Capacity|	NUMBER	|
|Address|	VARCHAR	|
|Contact_no|	NUMBER	|

<br>

3.	Table: IPL_Team

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|PlayerId|	NUMBER	|Primary key|
|Player_name|	VARCHAR	|Unique, Not null|
|Performance|	VARCHAR	|Performance details|
|Remarks|	VARCHAR	|

<br>

4.	Table: IPL_Player

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|PlayerId	|NUMBER	|Primary key|
|Player_name	|VARCHAR	|Unique, Not null|
|Performance	|VARCHAR|	Performance details|
|Remarks	|VARCHAR	|

<br>

5.	Table: IPL_Team_players

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|TeamId	|NUMBER	|Composite Primary key|
|PlayerId	|NUMBER|	Composite Primary key|
|Player_role|	VARCHAR|	Captain, Batsman, Bowler, WK, etc.|
|Remarks	|VARCHAR	|

<br>

6.	Table: IPL_Tournament

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|TournamentId|	NUMBER|Primary key|
|Tournament_name	|VARCHAR|Not null|
|From_date	|DATE|
|To_date	|DATE|
|Team_count	|NUMBER|
|Total_matches	|NUMBER|
|Remarks|	VARCHAR|


<br>


7.	Table: IPL_Match

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|MatchId|	NUMBER	|Primary key|
|TeamId1	|NUMBER|	FK from Team table. Not null|
|TeamId2|	NUMBER	|FK from Team table. Not null|
|TossWinner	|NUMBER	|Team no. 1 or 2|
|MatchWinner|	NUMBER	|Team no. 1 or 2|
|WinDetails|	VARCHAR	|Team 1 or 2 Won by XX runs or X wickets, Match tied.|
|Remarks|	VARCHAR	|E.g. Match canceled due to rain.|

<br>

8.	Table: IPL_Match_Schedule

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|ScheduleId|	NUMBER|	Primary key|
|TournamentId|	NUMBER	|FK from Tournament table. |
|MatchId	|NUMBER|	FK from Match table. |
|Match_type	|VARCHAR	|League, Knock out, Final, etc.|
|Match_date	|DATE|	This date should be within the from and to dates of the tournament.|
|Start_time|	TIME|	
|StadiumId|	NUMBER|	FK from Stadium table|
|Status	|VARCHAR	|Scheduled, Completed, Cancelled, etc.|
|Remarks	|VARCHAR	|

<br>


9.	Table: IPL_Bidder_Details

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|BidderId|	NUMBER	|Primary key|
|UserId|	NUMBER|	FK from User table.|
|Bidder_name|	VARCHAR|	Not null|
|Contact_no|	NUMBER	|Not null|
|Emailid|	VARCHAR	|
|Remarks	|VARCHAR|	

<br>


10.	Table: IPL_Bidding_Details

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|BidderId	|NUMBER|	FK from Bidder table. Composite Primary key|
|ScheduleId*	|VARCHAR|	FK from Match_Schedule table. Composite Primary key.|
|BidTeam	|NUMBER	|One of the team ids of the match (1 or 2). Composite primary key.|
|BidDate	|DATETIME	|Exact date & time of placing the bid. Update this column if a bidder re-bids on the same team for the same match. Composite Primary key.|
|BidStatus|	VARCHAR|	Bid, Cancelled, Won, Lost|
<br>



11.	Table: IPL_Bidder_Points

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|BidderId|	NUMBER	|FK from Bidder table. Primary key|
|TournamentId|	NUMBER	|FK from Tournament table. |
|No_of_bids	|NUMBER|	Total no. of bids placed by a bidder. Updated after completion of the match on which s/he placed the bid.|
|No_of_matches|	NUMBER|	Total no. of matches on which s/he placed the bid. Updated as above.|
|Total_points|	NUMBER|	Not null. Default 0|

<br>




12.	Table: IPL_Team_Standings

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|TeamId	|NUMBER	|FK from Team table. Primary key|
|TournamentId	|NUMBER	|FK from Tournament table. |
|Matches_played|	NUMBER	|Not null. Default 0|
|Matches_won	|NUMBER	|Not null. Default 0|
|Matches_lost|	NUMBER	|Not null. Default 0|
|Matches_tied	|NUMBER|	Default 0|
|No_result|	NUMBER|	Default 0|
|Points	|NUMBER	|Not null. Default 0|
|Remarks|	VARCHAR	|
