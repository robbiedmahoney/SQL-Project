Question 1: 

Are there any duplicate member id entries ?

SQL Queries:

SELECT "fullVisitorId", COUNT("fullVisitorId") AS entries
FROM all_sessions
GROUP BY "fullVisitorId"
HAVING COUNT("fullVisitorId") > 1
ORDER BY entries;

Answer: 

Yes, there are 794 duplicate member id's.




Question 2: 

What is the average time spent on each web page ?

SQL Queries:

SELECT SUM("timeOnSite") / SUM(pageviews) AS avg_time_on_each_page FROM all_sessions;

Answer:

The average tine spent on each web page is 38 seconds.





Question 3: 

What is the average lead time for restocking products ?


SQL Queries:

SELECT SUM("restockingLeadTime") / COUNT("SKU") AS average_restocking_leadtime FROM products;

Answer:

The average restocking lead time is 11 days.

