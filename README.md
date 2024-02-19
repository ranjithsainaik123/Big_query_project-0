#1)	How have sales compared by month from Jan 2021 – Jun 2021?

SELECT *  FROM `midyear-nebula-413114.Project_1.Sales` LIMIT 1000;

select sum(total_sales) as totalsales , trans_month from `midyear-nebula-413114.Project_1.Sales`
group by trans_month order by totalsales desc;
#2)	How do sales compare throughout the day? (Morning, midday, evening)

SELECT Hours, sum(total_sales)  as totalsales FROM `midyear-nebula-413114.Project_1.Sales`
group by Hours order by totalsales desc;

#3)	What products are selling the most?
SELECT prod_category, sum(total_sales) as Totalsales  FROM `midyear-nebula-413114.Project_1.Sales` 
group by prod_category ORDER BY TOTAlsales desc;

#4)	Where (physical location) are most of the customers

SELECT  cust_state, count(cust_id) as counts   FROM `midyear-nebula-413114.Project_1.Sales`
 group by cust_state order by counts desc;

#5)	What age groups do we see the most sales?


SELECT cust_age, sum(total_sales) as totalsales  FROM `midyear-nebula-413114.Project_1.Sales` 
 group by cust_age  order by totalsales desc;


 #6)	How much has the average customer spent throughout Jan 2021 – Jun 2021?


SELECT 
     COUNT(DISTINCT cust_id) AS average_spent_per_customer
FROM 
    `midyear-nebula-413114.Project_1.Sales`
WHERE 
    date BETWEEN '2021-01-01' AND '2021-06-30';



