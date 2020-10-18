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

## Business Answer

## Step-by-Step Instructions
1. In the Baltimore City Employees Salaries data, filter for **Fiscal Year** column for **FY2020**. Copy and paste the filtered data into a new worksheet called **FY2020 Data**.  
2. In the **FY2020 Data** worksheet, insert two columns to the right of **Hire Date** called **Days Worked** and **Years Worked**. 
- Change the format of all values in the **Hire Date** column to **Short Date**. 
- For each employee, enter the formula =TODAY()-**Hire Date** in the **Days Worked** column.
- For each employee, enter the formula =**Days Worked**/365 in the **Years Worked** column. Make sure that the **Years Worked** value returns two decimal places. 

![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Adding%20Days%20and%20Years%20Worked.png)

3. In the **FY2020 Data** worksheet, filter the **AgencyName** column for each department. Copy and paste each department's data into a separate worksheet with the title **FY2020 [Department Name].**
4. For each department: 
- Filter the **Annual Salary** column to make sure that there are no negative or 0 values. 
- Filter the **Gross Pay** column to make sure that there are no negative or 0 values. 
- Filter the **Years Worked** column to make sure that there are no impossible numbers (e.g. 120 years worked). 
- Copy and paste the data into a new Excel workbook (**Analysis Part 2**) that has separate tabs for each department's newly filtered data.
- Calculate the average annual salary, gross pay, and years worked for each department with the =AVERAGE() function. 
5. In the **Analysis Part 2** workbook, create a tab called **Data**. Create a table like below that includes the average annual salary, gross pay, and years worked for each department. Exclude the **Rep** and **Dem** departments because annual salaries are 0 and would skew the analysis.
![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Data.png)
6. Calculate the mean and standard deviations of the annual salary, gross pay, and years worked for all departments.
7. For each specific department, assign a number and find the z-scores for the average annual salary, gross pay, and years worked for each worked with the formula = STANDARDIZE(x, mean, standard deviation).
8. Create a table like below to create 5 anchors. For now, randomly type in department numbers like 1, 2, 3, 4, 5. 
- In the **Department Name** column, use Vlookup to find the corresponding department name for each department number.
- In the **Z-Score Annual Salary**, **Z-Score Gross Salary**, and **Z-Score Years Worked** columns, use Vlookup to find those corresponding values for each department number. 
![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Anchor.png)
9. Use the SUMXMY2 function to find the sum of squares of differences of corresponding values in two arrays: the z-score array for each department and each anchor's z-score array. 
10. Create a column called **Min_Distance2**. For each department, use the MIN formula to find the lowest sum of squares of differences. 
11. Use the SUM formula to find the total of the **Min_Distance2**.
12. In the **Assignment** column, use the MATCH function to find the anchor that corresponds to the lowest distance2 for each department. 
13. In the **Department Assignment** column, use the VLOOKUP function to find the name of the anchor department. 
![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Cluster.png)
