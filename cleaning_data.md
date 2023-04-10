What issues will you address by cleaning the data?

1) remove unwanted/irrelevant data
2) ensure data types are uniform across all tables
3) correcting missing values
4) correcting spelling errors in string data



Queries:
Below, provide the SQL queries you used to clean your data.

DELETE FROM products
WHERE "name" IS NULL;
