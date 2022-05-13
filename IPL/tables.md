1. Table: **IPL_User**

<br>

| Column name | 	Data type |	Comments |
| --- | --- | --- |
|UserId	|VARCHAR|	Primary key|
|Password	|VARCHAR	|Not null, encrypted format|
|User_type	|VARCHAR|	Admin or Bidder. Not null|
|Remarks |	VARCHAR	|



2.	Table: IPL_Stadium

| Column name | 	Data type |	Comments |
| --- | --- | --- |

3.	Table: IPL_Team

| Column name | 	Data type |	Comments |
| --- | --- | --- |

4.	Table: IPL_Player

| Column name | 	Data type |	Comments |
| --- | --- | --- |

5.	Table: IPL_Team_players

| Column name | 	Data type |	Comments |
| --- | --- | --- |

6.	Table: IPL_Tournament

| Column name | 	Data type |	Comments |
| --- | --- | --- |

7.	Table: IPL_Match

| Column name | 	Data type |	Comments |
| --- | --- | --- |

8.	Table: IPL_Match_Schedule

| Column name | 	Data type |	Comments |
| --- | --- | --- |

| Column name | 	Data type |	Comments |
| --- | --- | --- |

9.	Table: IPL_Bidder_Details

| Column name | 	Data type |	Comments |
| --- | --- | --- |

10.	Table: IPL_Bidding_Details

| Column name | 	Data type |	Comments |
| --- | --- | --- |

11.	Table: IPL_Bidder_Points

| Column name | 	Data type |	Comments |
| --- | --- | --- |

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



