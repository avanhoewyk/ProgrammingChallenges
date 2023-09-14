# SQL Challenge

The database contains three tables: marketing_performance, website_revenue, and campaign_info. Refer to the CSV
files to understand how these tables have been created.

`marketing_performance` contains daily ad spend and performance metrics -- impression, clicks, and conversions -- by campaign_id and location:
```sql
create table marketing_data (
 date datetime,
 campaign_id varchar(50),
 geo varchar(50),
 cost float,
 impressions float,
 clicks float,
 conversions float
);
```

`website_revenue` contains daily website revenue data by campaign_id and state:
```sql
create table website_revenue (
 date datetime,
 campaign_id varchar(50),
 state varchar(2),
 revenue float
);
```

`campaign_info` contains attributes for each campaign:
```sql
create table campaign_info (
 id int not null primary key auto_increment,
 name varchar(50),
 status varchar(50),
 last_updated_date datetime
);
```

### Challenge Submit Instructions

1. Fork the repository
2. Answer the questions below in a single SQL file - e.g answers.sql
3. Provide Link to Forked Repository to PMG PMG Talent Acquisition Team

### Please provide a SQL statement for each question

1. Write a query to get the sum of impressions by day.

```sql
SELECT SUM(impressions), date
FROM marketing_performance
GROUP BY date;
```

2. Write a query to get the top three revenue-generating states in order of best to worst. How much revenue did the third best state generate?
```sql
SELECT TOP 3 state, revenue
FROM website_revenue ORDER BY revenue DESC;
```

3. Write a query that shows total cost, impressions, clicks, and revenue of each campaign. Make sure to include the campaign name in the output.
```sql
SELECT FROM * website_revenue
NATURAL JOIN marketing_performance;

SELECT SUM(cost), SUM(impressions), SUM(clicks), SUM(revenue)
FROM marketing_performance
ORDER BY campaign_id;

SELECT SUM(cost), SUM(impressions), SUM(clicks)
FROM marketing_performance
GROUP BY campaign_id;

SELECT campaign_id, name
FROM marketing_performance
(CASE
WHEN campaign_id = 64441550 THEN name = Campaign1
WHEN campaign_id = 55304737 THEN name = Campaign2
WHEN campaign_id = 89363211 THEN name = Campaign3
WHEN campaign_id = 86363015 THEN name = Campaign4
WHEN campaign_id = 99058240 THEN name = Campaign5;
```

4. Write a query to get the number of conversions of Campaign5 by state. Which state generated the most conversions for this campaign?
   
5. In your opinion, which campaign was the most efficient, and why?

**Bonus Question**

6. Write a query that showcases the best day of the week (e.g., Sunday, Monday, Tuesday, etc.) to run ads.


