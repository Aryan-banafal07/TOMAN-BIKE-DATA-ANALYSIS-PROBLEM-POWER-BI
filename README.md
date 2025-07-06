# TOMAN-BIKE-DATA-ANALYSIS-PROBLEM-POWER-BI

# Problem Statement
![image](https://github.com/user-attachments/assets/3f83c8a0-59d5-44dd-b478-6df47a54f6dc)



# Output
![image](https://github.com/user-attachments/assets/c69ed9e9-8ef2-4cfa-b364-2d1d7a2043c5)


![image](https://github.com/user-attachments/assets/766c3d98-342e-46c4-8f11-0603f121503f)




# SQL CODE 

select * from bike_share_yr_0;
select * from bike_share_yr_1;

select season from bike_share_yr_0;

select * from bike_share_yr_0
union all
select * from bike_share_yr_1;


select * from cost_table;


WITH cte AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL
    SELECT * FROM bike_share_yr_1
)
SELECT 
    dteday,
    season,
    a.yr,
    weekday,
    hr,
    rider_type,
    riders,
    price,
    COGS,
    riders * price AS Revenue,
    (riders * price) - COGS AS profit
FROM cte a
LEFT JOIN cost_table b
    ON a.yr = b.yr;
