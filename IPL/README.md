This project is about IPL bidding on an app, and I've derived the insights from the data. 

### Schema and Data

* Run [IPL Schema & Data Dump](https://github.com/d0r1h/SQL/blob/main/IPL/IPL%20Schema%20%26%20Data%20Dump.sql) script to create schema and dump data into. 
* [tables.md](https://github.com/d0r1h/SQL/blob/main/IPL/tables.md) file contains the table structure and information about the columns. 

IPL schema has following 12 tables:

1. User Table
2. Stadium
3. Team
4. Player
5. Team Players
6. Tournament
7. Match
8. Match Schedule
9. Bidder Details
10. Bidding Details
11. Bidder Points
12. Team Standings


### ER Diagram

<h3 align="center">
    <a><img src="https://github.com/d0r1h/SQL/blob/main/IPL/ER_IPL.png", width="850"></a>
</h3>

### Insights  

1. The percentage of wins of each bidder in the order of highest to lowest percentage. [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#1-the-percentage-of-wins-of-each-bidder-in-the-order-of-highest-to-lowest-percentage)
2. The number of matches conducted at each stadium with stadium name, city from the database. [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#2-the-number-of-matches-conducted-at-each-stadium-with-stadium-name-city-from-the-database)
3. In a given stadium, what is the percentage of wins by a team which has won the toss? [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#3-in-a-given-stadium-what-is-the-percentage-of-wins-by-a-team-which-has-won-the-toss)
4. The total bids along with bid team and team name. [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#4-the-total-bids-along-with-bid-team-and-team-name)
5. The team id who won the match as per the win details. [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#5-the-team-id-who-won-the-match-as-per-the-win-details)
6. Total matches played, total matches won and total matches lost by team along with its team name. [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#6-total-matches-played-total-matches-won-and-total-matches-lost-by-team-along-with-its-team-name)
7. The bowlers for Mumbai Indians team. [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#7-the-bowlers-for-mumbai-indians-team)
8. How many all-rounders are there in each team, display the teams with more than 4 all-rounder in descending order.  [Solution](https://github.com/d0r1h/SQL/blob/main/IPL/solutions.md#8-how-many-all-rounders-are-there-in-each-team-display-the-teams-with-more-than-4-all-rounder-in-descending-order)
