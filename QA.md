What are your risk areas? Identify and describe them.

To ensure data is complete with no blank or null fields.
To ensure data is unique with no duplicate fields.
To ensure data is consistent with our expectations.

QA Process:
Describe your QA process and include the SQL queries used to execute it.


To ensure data is complete, in this example I will look to see that there are no null fields in the "name" column of the "products" table.

SELECT "name"
FROM products
WHERE "name" IS NULL;


To ensure there are no duplicate product sku's, I will look to see if there are more than one duplicate sku.

SELECT "SKU", COUNT("SKU") AS duplicates
FROM products
GROUP BY "SKU"
HAVING COUNT("SKU") > 1
ORDER BY duplicates;

To ensure data is consistent with my expectations, I will test that total items ordered are in the correct data type.

select total_ordered from sales_report;
