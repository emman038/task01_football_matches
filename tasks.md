# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
SELECT * FROM matches WHERE season = 2017;


```

2) Find all the matches featuring Barcelona.

```sql
SELECT * FROM matches WHERE hometeam = 'Barcelona' OR awayteam = 'Barcelona';


```

3) What are the names of the Scottish divisions included?

```sql
SELECT * FROM divisions WHERE country = 'Scotland';



```

4) Find the value of the `code` for the `Bundesliga` division. Use that code to find out how many matches Freiburg have played in that division. HINT: You will need to query both tables

```sql
SELECT * FROM divisions WHERE name = 'Bundesliga';
SELECT * FROM matches WHERE division_code = 'D1' AND hometeam = 'Freiburg' or awayteam = 'Freiburg';


```

5)  Find the teams which include the word "City" in their name. HINT: Not every team has been entered into the database with their full name, eg. `Norwich City` are listed as `Norwich`. If your query is correct it should return four teams.

```sql
SELECT DISTINCT hometeam FROM matches WHERE hometeam LIKE '%City%';

```

6) How many different teams have played in matches recorded in a French division?

```sql
SELECT * FROM divisions WHERE country = 'France';
SELECT COUNT(DISTINCT hometeam) FROM matches WHERE division_code = 'F1' OR division_code = 'F2';

61


```

7) Have Huddersfield played Swansea in any of the recorded matches?

```sql
SELECT * FROM matches WHERE (hometeam = 'Huddersfield' OR awayteam = 'Huddersfield') AND (hometeam = 'Swansea' OR awayteam = 'Swansea');

Yes


```

8) How many draws were there in the `Eredivisie` between 2010 and 2015?

```sql
SELECT * FROM divisions WHERE name = 'Eredivisie';
SELECT COUNT(*) FROM matches WHERE ftr = 'D' AND season >= 2010 AND season <= 2015;

12390


```

9) Select the matches played in the Premier League in order of total goals scored (`fthg` + `ftag`) from highest to lowest. When two matches have the same total the match with more home goals (`fthg`) should come first. 

```sql
SELECT * FROM matches ORDER BY SUM(fthg + ftag) DESC, fthg DESC;


```

10) Find the name of the division in which the most goals were scored in a single season and the year in which it happened.

```sql
SELECT division_code, season, SUM(fthg + ftag) FROM matches GROUP BY division_code, season ORDER BY SUM(fthg + ftag) DESC;
SELECT DISTINCT name FROM divisions WHERE code = 'EC';

National League - 2013


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)