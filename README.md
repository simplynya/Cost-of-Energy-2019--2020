"# Cost-of-Energy-2019--2020" 
CREATE DATABASE portfolioproject;
USE portfolioproject;

SELECT * FROM portfolioproject.sales_revenue_2019_2020;


-- This was an exploration SQL, where I found interesting things but also some issues that needs more investigation. 
-- Here is what I found thus far.

-- It gives the Highest Price in Cents per KWH 

Select Year, Month, State, Price_CentskWh FROM portfolioproject.sales_revenue_2019_2020
WHERE Price_CentskWh > 8
order by Price_CentskWh desc;


-- It gives the Highest Price in Cents per KWH only for 2020 

Select Year, Month, State, Price_CentskWh FROM portfolioproject.sales_revenue_2019_2020
WHERE year = 2020
order by Price_CentskWh desc;


-- It gives the Highest Price in Cents per KWH for 2020 showing the Customer Count

Select Year, Month, Customers_count, State, Price_CentskWh as Price_CentkWh_2020
FROM portfolioproject.sales_revenue_2019_2020
WHERE year = 2020
order by Price_CentskWh desc;


-- It gives the Highest Price in Cents per KWH for 2019 showing the Customer Count

Select Year, Month, State, Customers_count, Price_CentskWh as Price_CentkWh_2019
FROM portfolioproject.sales_revenue_2019_2020
WHERE year = 2019
order by Customers_count desc;


-- It gives the Higher Price in Cents per KWH based on State

Select MAX(Price_CentsKWh) as Highest_Price_State, State
From portfolioproject.sales_revenue_2019_2020
Where State is not null 
Group by State
order by Highest_Price_State desc;


-- It gives the Higher Price in Cents per KWH for Florida

Select State, year, month, Price_CentsKWh
From portfolioproject.sales_revenue_2019_2020
WHERE State LIKE '%FL%'
order by Price_CentskWh desc;


-- Just looking at specific columns

Select State, month, Customers_count, Price_CentskWh 
From portfolioproject.sales_revenue_2019_2020;


-- It gives the Price in Cents per KWH above 20 cents

Select Year, month, State, Customers_count, Price_CentskWh 
From portfolioproject.sales_revenue_2019_2020
Where Price_CentskWh > 20;

-- It gives the Price in Cents KWH for Months for Alabama

Select State, year, month, Price_CentsKWh
From portfolioproject.sales_revenue_2019_2020
WHERE State LIKE '%AL%'
order by Month asc;

-- It gives the Price in Cents KWH in Months for Florida and Hawaii (the state with the highest price)
-- Highest State vs Florida

Select State, year, month, Customers_count, Price_CentsKWh
From portfolioproject.sales_revenue_2019_2020
WHERE State IN ("FL", "HI")
order by Month asc;
