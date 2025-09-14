# Apple-sales-and-Performance-Data-Analysis-using-SQL-
📊 Project Overview
- SQL project analyzing Apple App Store data to uncover trends in app categories, pricing, ratings, and user engagement

🛠 Tools Used
- SQL (SQLite)
- Apple App Store datasets (AppleStore.csv, appleStore_description1.csv, appleStore_description2.csv)

📂 Files in this Repository

- AppleStore.csv → Main dataset with app details (ratings, prices, categories, etc.)

- appleStore_description1.csv → App description dataset (part 1)

- appleStore_description2.csv → App description dataset (part 2)

- AppleStore_Queries.sql → SQL script containing exploratory and analytical queries

📌 Key Insights

- The App Store hosts a diverse range of apps, with some categories dominating in volume and user engagement.

- Paid apps generally receive higher ratings compared to free apps.

- Apps with support for multiple languages tend to have better ratings.

- Certain genres consistently show lower average ratings, suggesting quality challenges.

- Top-rated apps differ by category, showing unique success drivers across genres.

🚀 How to Use

- Import the datasets into your SQL environment (SQLite).

- Run the queries in AppleStore_Queries.sql step by step to replicate the analysis.

- Modify or extend the queries to explore additional KPIs, such as revenue potential or review counts.

📑 Example Queries

-- Find the number of apps per genre --
SELECT prime_genre, COUNT(*) AS number_of_apps
FROM AppleStore
GROUP BY prime_genre
ORDER BY number_of_apps DESC;

-- Compare average ratings of free vs paid apps --
SELECT CASE 
         WHEN price = 0 THEN 'Free' 
         ELSE 'Paid' 
       END AS app_type,
       AVG(user_rating) AS avg_rating
FROM AppleStore
GROUP BY app_type;

-- Check if apps with more supported languages have higher ratings --
SELECT CASE 
         WHEN lang_num < 10 THEN '<10 languages'
         WHEN lang_num BETWEEN 10 AND 30 THEN '10–30 languages'
         ELSE '>30 languages'
       END AS language_bucket,
       AVG(user_rating) AS avg_rating
FROM AppleStore
GROUP BY language_bucket
ORDER BY avg_rating DESC;






