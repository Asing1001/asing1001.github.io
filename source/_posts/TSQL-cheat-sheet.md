---
title: Transact-SQL cheat sheet
date: 2018-04-12 15:35:37
tags: [TSQL, MS SQL, SQL, Transact-SQL]
---

```sql
-- Get current datetime
GETDATE()

-- Get year of datetime
YEAR(GETDATE())

-- Get difference between dates (subtract date), dateformat 
DATEDIFF(dateformat, startdate, enddate)

-- Between
select * from User where CreatedDate between '2016-09-26' and '2016-09-27'

-- Order by
select * from User order by column desc

-- Group by
select UserCode, Count(*) from User group by UserCode

-- Select top 10
SELECT TOP (10) * from User
```