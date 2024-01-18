![Pizza](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/pizza%20cropped.jpg?raw=true)
# Oven Joy Pizzeria Sales Report

Welcome to the Oven Joy Pizzeria Sales Report project! This repository contains SQL queries and corresponding visualizations created using Power BI for analyzing the sales data of Oven Joy Pizzeria and gain impactful insights from it.

You can Check out the dashboard here: https://www.novypro.com/project/oven-joy-pizzeria-sales-analysis-report

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


7. **Monthly Trend**
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

1. **Total Revenue Percentage by Pizza category**
     ```sql
     select pizza_category,
     sum(total_price) *100 / (select sum(total_price) from pizza_sales)
     as pizza_cat_percent
     from pizza_sales
     group by pizza_category;
     ```
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Pizza%20sales%20percentage%20by%20category.png?raw=true)
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000242.png?raw=true)

2. **Total Revenue Percentage by Pizza size**
     ```sql
     select pizza_category,
     sum(total_price) *100 / (select sum(total_price) from pizza_sales)
     as pizza_cat_percent
     from pizza_sales
     group by pizza_category;
     ```
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/pizza%20sales%20percentage%20by%20size.png?raw=true)
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000234.png?raw=true)

3. **Total Pizza Sold by Pizza category**
     ```sql
     select pizza_category,
     sum(total_price) *100 / (select sum(total_price) from pizza_sales)
     as pizza_cat_percent
     from pizza_sales
     group by pizza_category;
     ```
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/total%20pizza%20sold%20by%20pizza%20size.png?raw=true)
     ![Pizza Sales Percentage by category](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000225.png?raw=true)
...

## Bestsellers and Worst sellers

1. **Top 5 Pizzas by Revenue**
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
   

2. **Top 5 Pizzas by Total Quantity**
     ```sql
     select pizza_name, sum(quantity) as pizza_qnt
     from pizza_sales
     group by pizza_name
     order by pizza_qnt desc
     limit 5;
     ```
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/top%205%20by%20quantity.png?raw=true) 
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000345.png?raw=true)

3. **Top 5 Pizzas by Total Order**
     ```sql
    SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Orders DESC
    limit 5;
     ```
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/top%205%20by%20order.png?raw=true) 
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000351.png?raw=true)

4. **Bottom 5 Pizzas by Revenue**
     ```sql
     select pizza_name,
     sum(total_price) as pizza_revenue,
     count(pizza_id) as no_of_orders
     from pizza_sales
     group by pizza_name
     order by pizza_revenue
     limit 5;
     ```
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/bottom%205%20by%20revenue.png?raw=true) 
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000359.png?raw=true)

5. **Bottom 5 Pizzas by Total Quantity**
     ```sql
     select pizza_name, sum(quantity) as pizza_qnt
     from pizza_sales
     group by pizza_name
     order by pizza_qnt
     limit 5;
     ```
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/bottom%205%20by%20quantity.png?raw=true) 
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000405.png?raw=true)

6. **Bottom 5 Pizzas by Total Order**
     ```sql
     SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Orders
    limit 5;
     ```
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/bottom%205%20by%20order.png?raw=true) 
     ![Top 5 Pizzas by Revenue](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-14%20000412.png?raw=true)

...
## Power BI Dashboard
![Report](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-13%20234650.png?raw=true)

![Report](https://github.com/Shaishta-Anjum/Pizza-Sales-Report/blob/main/icons/Screenshot%202024-01-13%20234729.png?raw=true)


The dashboard allows you to filter the analysis based on Pizza category, offering a comprehensive view of sales performance for each category. Additionally, you can leverage the sliders to narrow down the data within specific date ranges, providing you with the flexibility to analyze trends and patterns over time.

## Insights
- Orders are highest on weekends, i.e. on **Friday/Saturday** evenings.
- There are maximum orders from month of **July** and **January**.
- **Classis Category** of Pizzas contributes the most to total order and maximum sale.
- The **Thai Chicken Pizza** generates the most revenue.
- The **Chicken Deluxe Pizza** contributes the most to total order and total quantity.
- The **Brie Carre Pizza** contributes the least to total order & total quantity and generates the least revenue.
 
Feel free to navigate through the dashboard and uncover more valuable insights. Should you have any questions or suggestions, please don't hesitate to reach out. 
Happy exploring!
