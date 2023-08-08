# Sales-Dashboard-for-Pizza

PIZZA SALES SQL QUERIES
1.	Key Performance Indicators (KPIs)

  	a.	Total Revenue
       select sum(total_price) as total_revenue from pizza.pizza_sales;
       
    b.	Average Order Value
      select sum(total_price) / count(distinct order_id) as Avg_ord_val from pizza.pizza_sales;
     
    c.	Total Pizza Sold
      select sum(quantity) as total_pizza_sold from pizza.pizza_sales;
     
    d.	Total Order 
     select count(distinct order_id) as total_order from pizza.pizza_sales;
     
    e.	Average Pizza Per Order
    select cast(sum(quantity) as decimal(10,2))/  cast(count(distinct order_id) as decimal(10,2)) as avg_pizza_per_ord from pizza.pizza_sales;
 
3.	Daily Trends of Total Orders
select dayname(order_date)as order_day ,count(distinct order_id) as total_order from pizza.pizza_sales ;   
 

4.	Monthly Trends of Total Orders
select dayname(month,order_date) as month_name, count( distinct order_id) as total_order from pizza.pizza_sales group by dayname(month,order_date) order by total_order desc;
 

5.	% of Sales by Pizza Category
select pizza_category ,sum(total_price) as total_sales ,sum(total_price)*100/( select sum(total_price) from pizza.pizza_sales) as percentage_sales from pizza.pizza_sales group by pizza_category;
 
6.	% of Sales by Pizza Size
select pizza_size ,sum(total_price) as total_sales ,sum(total_price)*100/( select sum(total_price) from pizza.pizza_sales) as percentage_sales from pizza.pizza_sales group by pizza_size;
 
7.	Total Pizza Sold by Pizza Category
select pizza_category, sum(quantity) as Total_Quantity_Sold from pizza.pizza_sales group by pizza_category order by Total_Quantity_Sold desc;
 
8.	Top 5 Pizza by Revenue
select pizza_name , sum(total_price) as total_revenue from pizza.pizza_sales group by pizza_name order by total_revenue desc limit 5  ;
 
9.	Bottom 5 Pizza by Revenue
select pizza_name , sum(total_price) as total_revenue from pizza.pizza_sales group by pizza_name order by total_revenue limit 5  ;
 
10.	Top 5 Pizza by Quantity
select pizza_name , sum(quantity) as total_quantity from pizza.pizza_sales group by pizza_name order by total_quantity desc limit 5  ;
 

11.	Bottom 5 Pizza by Quantity
select pizza_name , sum(quantity) as total_quantity from pizza.pizza_sales group by pizza_name order by total_quantity limit 5  ;
 

12.	Top 5 Pizza by Pizza Order
select  pizza_name, count(distinct order_id) as Total_Orders from pizza.pizza_sales group by pizza_name order by Total_Orders desc limit 5;
 
13.	Bottom 5 Pizza by Pizza Order
select  pizza_name, count(distinct order_id) as Total_Orders from pizza.pizza_sales group by pizza_name order by Total_Orders limit 5;
 

