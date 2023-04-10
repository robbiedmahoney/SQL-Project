Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:

SELECT country, city, "totalTransactionRevenue" FROM all_sessions
GROUP BY country, city, "totalTransactionRevenue"
HAVING "totalTransactionRevenue" >= 1000000
ORDER BY "totalTransactionRevenue" DESC
LIMIT 10;


Answer:
The three highest cities with highest level of transaction revenues weren't known, but the countries were all USA.

"United States"	"not available in demo dataset"	1015480000
"United States"	"not available in demo dataset"	1005500000
"United States"	"not available in demo dataset"	849700000


**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

SELECT all_sessions.country, all_sessions.city, AVG(sales_report.total_ordered) FROM all_sessions
	JOIN sales_report
	ON all_sessions."productSKU" = sales_report."productSKU"
	GROUP BY all_sessions.country, all_sessions.city
	ORDER BY all_sessions.country;

Answer:

snippet:

"Argentina"	"Buenos Aires"	22.2500000000000000
"Argentina"	"Santa Fe"	60.0000000000000000
"Argentina"	"Rosario"	1.00000000000000000000
"Armenia"	"not available in demo dataset"	16.0000000000000000
"Australia"	"not available in demo dataset"	18.4042553191489362
"Australia"	"Los Angeles"	3.0000000000000000





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
SELECT country, city, "v2ProductCategory" FROM all_sessions
	GROUP BY country, city, "v2ProductCategory"
	ORDER BY country;


Answer:

The vast majority of products sold were under the "Home" category.



**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

SELECT all_sessions.country, all_sessions.city, products.name, products."orderedQuantity" FROM all_sessions
	JOIN products
	ON all_sessions."productSKU" = products."SKU"
	GROUP BY all_sessions.country, all_sessions.city, products.name, products."orderedQuantity"
	ORDER BY all_sessions.country, all_sessions.city, products."orderedQuantity" DESC;



Answer:
snippet
"Australia"	"Adelaide"	" Men's Watershed Full Zip Hoodie Grey"	54
"Australia"	"Brisbane"	" Twill Cap"	1429
"Australia"	"Brisbane"	" Leatherette Notebook Combo"	1148
"Australia"	"Brisbane"	" Men's Vintage Henley"	79
"Australia"	"Brisbane"	" High Capacity 10,400mAh Charger"	73



**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

SELECT country, city, "totalTransactionRevenue" FROM all_sessions
	WHERE "totalTransactionRevenue" >= 1
	GROUP BY country, city, "totalTransactionRevenue"
	ORDER BY "totalTransactionRevenue" DESC;


Answer:

The highest grossing cities/country were mainly in the USA.





