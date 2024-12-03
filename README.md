# DATA-MART-CaseStudy
Data Cleaning, Data Exploration 📅📅
Data Mart is the latest venture and Client want my help to analyze the sales and 
performance of the venture. In June 2020 - large scale supply changes were made 
at Data Mart. All Data Mart products now use sustainable packaging methods in 
every single step from the farm all the way to the customer.
Client asked the help to quantify the impact of this change on the sales performance for 
Data Mart and its separate business areas. 🌍🌍

SCHEMA USED BELOW ->>💻⬇️⬇️⬇️
COLUMN NAME DATA TYPE 📅
week_date date
region varchar(20)
platform varchar(20)
segment varchar(10)
customer varchar(20)
transactions int
sales int
CASE STUDY QUESTIONS ⬇️⬇️⬇️
A. Data Cleansing Steps
In a single query, perform the following operations and generate a new table in 
the data_mart schema named clean_weekly_sales:
1. Add a week_number as the second column for each week_date value, for 
example any value from the 1st of January to 7th of January will be 1, 8th to 
14th will be 2, etc.
2. Add a month_number with the calendar month for each week_date value as 
the 3rd column
3. Add a calendar_year column as the 4th column containing either 2018, 2019 
or 2020 values
4. Add a new column called age_band after the original segment column using 
the following mapping on the number inside the segment value
(segment) (age_brand)
   1        YOUNG_ADULTS
   2        MIDDLE_AGED
3 or 4      RETIREES
5. Add a new demographic column using the following mapping for the first 
letter in the segment values:
   (SEGMENT) (DEMOGRAPHIC)
   C          COUPLES
   F          FEMALES
6. Ensure all null string values with an "unknown" string value in the 
original segment column as well as the 
new age_band and demographic columns
7. Generate a new avg_transaction column as the sales value divided 
by transactions rounded to 2 decimal places for each record

B. Data Exploration 💹📈📉📊
1. Which week numbers are missing from the dataset?
2. How many total transactions were there for each year in the dataset?
3. What are the total sales for each region for each month?
4. What is the total count of transactions for each platform
5. What is the percentage of sales for Retail vs Shopify for each month?
6. What is the percentage of sales by demographic for each year in the dataset?
7. Which age_band and demographic values contribute the most to Retail 
sales?



Answers- first step i used i created a database 
under the database i provide all the column which are required ⬇️⬇️
week_date date,
region VARCHAR(100),
platform VARCHAR(100),
segment VARCHAR(100),
customer_type VARCHAR(100),
transactions INT(11),
sales INT(11)

then i cleaned the data with WEEK(), MONTH(), and YEAR() functions in SQL
The WEEK() function is used to extract the week number of a date.
The MONTH() function extracts the month number (1 to 12) from a date.
The YEAR() function extracts the year from a date.
This will fetch into •	WEEK() helps in weekly analysis.
•	MONTH() is for monthly aggregation or filtering.
•	YEAR() is for yearly trends or filtering.

i performed case when query in my sql, The CASE WHEN statement in SQL is a conditional expression that works like an if-else statement in programming languages. It allows you to return specific values based on conditions within a query.
under which i used •	LEFT() starts from the beginning of the string.
•	RIGHT() starts from the end of the string.
•	These functions are particularly useful in data cleaning, formatting, and extracting specific substrings.
these two along with case when helps me to fetch the solution for point 4 and point 5 of section A Data Cleaning
then i performed simple arithmetic for fetching out new avg_transaction column of point 7 in section A data cleaning

Then i performed B section DATA EXPLORATION ⬇️↙️↙️↙️
Point 1 where i had to check missing data i performed a query to generate a sequence of numbers in SQL. Let me break it down step by step:
Step 1: Create the Table
CREATE TABLE seq100(
    x INT NOT NULL AUTO_INCREMENT PRIMARY KEY
);
•	What this does: 
Creates a table named seq100.
The table has one column x, which is an integer and automatically increases with each new row because of the AUTO_INCREMENT feature.
The column x is also set as the primary key, meaning each value in this column must be unique.
________________________________________
Step 2: Insert Initial Values
INSERT INTO seq100 VALUES (),(),(),(),(),(),(),(),(),();
•	What this does: 
Inserts 10 rows into the table seq100.
Each row has an empty value () because x is AUTO_INCREMENT, so SQL automatically generates the numbers starting from 1.
Step 3: Repeat the Inserts
INSERT INTO seq100 VALUES (),(),(),(),(),(),(),(),(),();
This step is repeated multiple times (5 times in total in your example).
Each time, 10 new rows are added, continuing the sequence of numbers. After all the inserts, the table will have 50 rows: 
Double the Numbers
INSERT INTO seq100 SELECT x + 50 FROM seq100;
What this does: 
It takes all the existing numbers in the table and adds 50 to each one.
Then it inserts these new numbers back into the table.
After this step, the table will have numbers from 1 to 100: 
View the Numbers
SELECT * FROM seq100;
What this does: 
Displays all the rows in the table, showing numbers from 1 to 100.
________________________________________
Purpose of the Query
This query creates a sequence of numbers from 1 to 100 in a table without manually entering all the numbers. It’s a preparatory step often used in tasks like:
1.	Generating a sequence of weeks (e.g., 1 to 52).
2.	Finding missing values (like missing week numbers in your case).
3.	Creating a reference table for comparison or joins.
For point 2 i simply performed group by to fetch total transactions were there for each year in the dataset
For point 3 & 4 same.... :D
For point 5 i used Window functions with PARTITION BY month_number which is crucial in this query because it ensures the percentage of sales is calculated separately for each month
Same with Point 6 i used Window functions with PARTITION BY demographic to fetch percentage of sales by demographic for each year in the dataset
and in last Point 7 i used query for the total sales for each combination of age_band and demographic in the clean_weekly_sales table, but only for records where the platform is 'Retail'. The results are grouped by age_band and demographic, and then sorted by Total_Sales in descending order, showing the combinations with the highest sales first.


## Conclusion:
This project helped me strengthen my SQL skills. Key insights included identifying missing week numbers, understanding the sales performance across different platforms, and gaining insights into the demographic breakdown of sales.
## SQL Queries:
All SQL queries used in this project can be found in the `casestudy.sql` file in the repository.


