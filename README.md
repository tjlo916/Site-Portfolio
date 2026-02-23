# Data Analysis Portfolio

Interactive Excel Dashboard - Patient Satisfaction, Orthopedics, 2023

<img width="1023" height="770" alt="image" src="https://github.com/user-attachments/assets/acfc0922-84d7-4ddd-9cdb-3748661ad73c" />

# SQL Projects
Analyzing Industry Carbon Emissions [SQL]
SELECT 
    industry_group, 
    COUNT(DISTINCT company) AS num_companies, 
    ROUND(SUM(carbon_footprint_pcf), 1) AS total_industry_footprint
FROM 
    product_emissions
WHERE 
    year = (SELECT MAX(year) FROM product_emissions)
GROUP BY 
    industry_group
ORDER BY 
    total_industry_footprint DESC;

# Next
coding read me
previous: test no code

- Test bullet

Test line separation

double line

single: same line
testing same line

# Next: Add Theme

test add theme

Update automatically?
