![Pizza](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/pizza%20cropped.jpg?raw=true)
# Oven Joy Pizzeria Sales Report

Welcome to the Oven Joy Pizzeria Sales Report project! This repository contains SQL queries and corresponding visualizations created using Power BI for analyzing the sales data of Oven Joy Pizzeria.

## Key Performance Indicators (KPIs)

1. **Total Revenue Generates**
    - SQL Query:
      ```sql
      select sum(total_price) as total_revenue
      from pizza_sales;
      ```
    - Result:
      ![Total Revenue](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/f2976346-3d39-477c-aedf-1699b39a071a/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

2. **Average Order Value**
    - SQL Query:
      ```sql
      select (sum(total_price)/count(distinct order_id)) as average_order_value
      from pizza_sales;
      ```
    - Result:
      ![Average Order Value](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/cfc7fa5a-387a-4978-ada3-7db886eaa74b/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

3. **Total Pizza Sold**
    - SQL Query:
      ```sql
      select sum(quantity) as total_pizza_sold
      from pizza_sales;
      ```
    - Result:
      ![Total Pizza Sold](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/a74571da-7aba-499d-a9f3-360bb858284f/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

...

### Ordering Trend by Weekdays
   - SQL Query:
     ```sql
     SELECT to_char(order_date, 'Day') AS order_day, COUNT(DISTINCT order_id) AS total_orders
     FROM pizza_sales
     GROUP BY to_char(order_date, 'Day');
     ```
   - Result:
     ![Ordering Trend by Weekdays](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/059cdee4-7bba-450a-b1be-a02959aa6806/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

### Monthly Trend
   - SQL Query:
     ```sql
     SELECT to_char(order_date, 'Month') AS order_month,
     COUNT(DISTINCT order_id) AS total_orders
     FROM pizza_sales
     GROUP BY to_char(order_date, 'Month');
     ```
   - Result:
     ![Monthly Trend](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/1e70dd80-88e8-4522-982e-0bcf64e3e288/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

...

## Pizza Category Analysis

### Pizza Sales Percentage by category
   - SQL Query:
     ```sql
     select pizza_category,
     sum(total_price) *100 / (select sum(total_price) from pizza_sales)
     as pizza_cat_percent
     from pizza_sales
     group by pizza_category;
     ```
   - Result:
     ![Pizza Sales Percentage by category](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/92552a44-a823-451e-b959-93836c12abda/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

...

## Top and Bottom Performers

### Top 5 Pizzas by Revenue
   - SQL Query:
     ```sql
     select pizza_name,
     sum(total_price) as pizza_revenue,
     count(pizza_id) as no_of_orders
     from pizza_sales
     group by pizza_name
     order by pizza_revenue desc
     limit 5;
     ```
   - Result:
     ![Top 5 Pizzas by Revenue](https://prod-files-secure.s3.us-west-2.amazonaws.com/13b702bf-6e3f-4936-9dd9-66111d4fb14c/b22c490e-dd86-4f64-9e4b-0fc9f85dbdbc/Untitled.png)

    - Additional Links:
        - [Link 1](#)
        - [Link 2](#)

...

Feel free to explore the interactive Power BI dashboard for a more in-depth analysis! If you have any questions or suggestions, please don't hesitate to reach out.
