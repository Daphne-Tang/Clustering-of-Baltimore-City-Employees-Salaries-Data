# Clustering-of-Baltimore-City-Employees-Salaries-Data

## Background

## Business Question

## Data Question - Open Data
[Baltimore City Open Data](https://data.baltimorecity.gov) publishes datasets from Baltimore City's government departments. The purpose is to share information about Baltimore City's services, housing & development, crime, culture & arts, finances, geographics, health, neighborhoods, public safety, public works, and transportation. The open publication of data would allow for greater analysis and engagement with the community on ways to improve Baltimore City.  

This analysis uses the dataset called [Baltimore City Employees Salaries.](https://data.baltimorecity.gov/City-Government/Baltimore-City-Employees-Salaries/w28m-utix) For each employee, the dataset has his/her ID, job title, agency ID, agency name, hire date, annual salary, gross pay, and the data's fiscal year. 

## Data Question - Analysis
This analysis uses Microsoft Excel to answer the following question: 
- How can we group departments within Baltimore City Government based on the annual salary, gross pay, and years worked of employees? 

## Data Answer


![alt text]()

## Business Answer

## Step-by-Step Instructions
1. In the Baltimore City Employees Salaries data, filter for **Fiscal Year** column for **FY2020**. Copy and paste the filtered data into a new worksheet called **FY2020 Data**.  
2. In the **FY2020 Data** worksheet, insert two columns to the right of **Hire Date** called **Days Worked** and **Years Worked**. 
- Change the format of all values in the **Hire Date** column to **Short Date**. 
- For each employee, enter the formula =TODAY()-**Hire Date** in the **Days Worked** column.
- For each employee, enter the formula =**Days Worked**/365 in the **Years Worked** column. Make sure that the **Years Worked** value returns two decimal places. 

![alt text]()
