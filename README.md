![Pizza](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/pizza%20cropped.jpg?raw=true)
# Oven Joy Pizzeria Sales Report

Welcome to the Oven Joy Pizzeria Sales Report project! This repository contains SQL queries and corresponding visualizations created using Power BI for analyzing the sales data of Oven Joy Pizzeria and gain impactful insights from it.

![Report](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-13%20234650.png?raw=true)



![Report](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-13%20234729.png?raw=true)

## Key Performance Indicators (KPIs)

1. **Total Revenue Generates**
      ```sql
      select sum(total_price) as total_revenue
      from pizza_sales;
      ```

      ![Total Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Total_Revenue.png?raw=true)            ![Total Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000254.png?raw=true)

2. **Average Order Value**
      ```sql
      select (sum(total_price)/count(distinct order_id)) as average_order_value
      from pizza_sales;
      ```
      ![Average Order Value](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Avg%20Order%20Value.png?raw=true)      ![Average Order Value](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000259.png?raw=true)

3. **Total Pizza Sold**
      ```sql
      select sum(quantity) as total_pizza_sold
      from pizza_sales;
      ```
      ![Total Pizza Sold](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Total%20Pizza%20Sold.png?raw=true)      ![Total Pizza Sold](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000312.png?raw=true)


4. **Total Pizza Sold**
      ```sql
      select count(distinct order_id) as total_order_placed
      from pizza_sales;
      ```
      ![Total Orders](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Total%20Orders%20placed.png?raw=true)![Total Orders](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000306.png?raw=true) 
...

5. **Daily Trend**
     ```sql
     SELECT to_char(order_date, 'Day') AS order_day, COUNT(DISTINCT order_id) AS total_orders
     FROM pizza_sales
     GROUP BY to_char(order_date, 'Day');
     ```
     ![Ordering Trend by Weekdays](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/daily%20trend.png?raw=true)
     ![Ordering Trend by Weekdays](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000148.png?raw=true)


6. **Monthly Trend**
     ```sql
     SELECT to_char(order_date, 'Month') AS order_month,
     COUNT(DISTINCT order_id) AS total_orders
     FROM pizza_sales
     GROUP BY to_char(order_date, 'Month');
     ```
     ![Monthly Trend](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Monthly%20trend.png?raw=true)     
     ![Monthly Trend](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000212.png?raw=true)


...

## Pizza Type Analysis

1. **Pizza Sales Percentage by category**
     ```sql
     select pizza_category,
     sum(total_price) *100 / (select sum(total_price) from pizza_sales)
     as pizza_cat_percent
     from pizza_sales
     group by pizza_category;
     ```
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Pizza%20sales%20percentage%20by%20category.png?raw=true)
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000242.png?raw=true)


...

## Bestsellers and Worst sellers

**Top 5 Pizzas by Revenue**
     ```sql
     select pizza_name,
     sum(total_price) as pizza_revenue,
     count(pizza_id) as no_of_orders
     from pizza_sales
     group by pizza_name
     order by pizza_revenue desc
     limit 5;
     ```
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/top%205%20by%20revenue.png?raw=true) 
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000339.png?raw=true)

...

Feel free to explore the interactive Power BI dashboard for a more in-depth analysis! If you have any questions or suggestions, please don't hesitate to reach out.
