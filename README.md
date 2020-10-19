# Clustering-of-Baltimore-City-Employees-Salaries-Data

## Background
The Baltimore City Government is increasingly focusing on attracting talent, but departments are facing challenges in recruitment. For instance, the [Baltimore Police Department](https://www.baltimoresun.com/maryland/baltimore-city/bs-md-ci-consent-decree-report-20200122-pth324df5vexxbrzyn7m6ebzwy-story.html) has a critical shortage of officers because more officers are leaving than joining. Recruitment and retention is crucial to ensuring that the Baltimore City Government has enough talent to sustain and improve its services, operations, and impact. Each department is in a different situation, and this analysis explores a potential cause of the discrepancies: annual and gross salaries partially depending on years worked. 

## Business Question
Could lower salaries in certain departments be contributing to recruitment and retention difficulties within the Baltimore City Government?

## Data Question - Open Data
[Baltimore City Open Data](https://data.baltimorecity.gov) publishes datasets from Baltimore City's government departments. The purpose is to share information about Baltimore City's services, housing & development, crime, culture & arts, finances, geographics, health, neighborhoods, public safety, public works, and transportation. The open publication of data would allow for greater analysis and engagement with the community on ways to improve Baltimore City.  

This analysis uses the dataset called [Baltimore City Employees Salaries.](https://data.baltimorecity.gov/City-Government/Baltimore-City-Employees-Salaries/w28m-utix) For each employee, the dataset has his/her ID, job title, agency ID, agency name, hire date, annual salary, gross pay, and the data's fiscal year. 

## Data Question - Analysis
This analysis uses Microsoft Excel to answer the following question: 
- How can we group departments within Baltimore City Government based on the annual salary, gross pay, and years worked of employees? 

## Data Answer
Clustering of the data with four anchors (Council Services, Liquor License, Transportation, Enoch Pratt Library) produced the following assignments: 

![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Department%20Assignments.png)

Council Services is the first anchor: 
- Z-Score Annual Salary: 1.43 (High annual salary)
- Z-Score Gross Pay: 1.52 (High gross pay)
- Z-Score Years Worked: 1.38 (High years worked)

Liquor License is the second anchor: 
- Z-Score Annual Salary: -0.20 (Slightly below average annual salary)
- Z-Score Gross Pay: -0.28 (Slightly below average gross pay)
- Z-Score Years Worked: -0.51 (Slightly below average years worked)

Transportation is the third anchor: 
- Z-Score Annual Salary: -1.07 (Low annual salary)
- Z-Score Gross Pay: -0.79 (Low gross pay)
- Z-Score Years Worked: 0.77 (High years worked)

Enoch Pratt Library is the fourth anchor: 
- Z-Score Annual Salary: -0.80 (Low annual salary)
- Z-Score Gross Pay: -0.76 (Low gross pay)
- Z-Score Years Worked: -0.10 (Slightly below average years worked)

The departments assigned to each anchor has similar characteristics in terms of their annual salaries, gross pay, and years worked relative to the average. The following graphs visually represent the clusters. 

- Cluster 1 = Council Services
- Cluster 2 = Liquor License
- Cluster 3 = Transportation
- Cluster 4 = Enoch Pratt Library

![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Cluster%20Visual%201.png)

![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Cluster%20Visual%202.png)

![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Cluster%20Visual%203.png)

## Business Answer
The departments with the Council Services anchor demonstrate that there is the possibility that higher annual salaries and gross pay could contribute to greater number of years worked. The Liquor License anchor also shows that lower annual salaries and gross pay could result in smaller amount of years worked. 

## Step-by-Step Instructions
1. In the Baltimore City Employees Salaries data, filter for **Fiscal Year** column for **FY2020**. Copy and paste the filtered data into a new worksheet called **FY2020 Data**.  
2. In the **FY2020 Data** worksheet, insert two columns to the right of **Hire Date** called **Days Worked** and **Years Worked**. 
- Change the format of all values in the **Hire Date** column to **Short Date**. 
- For each employee, enter the formula =TODAY()-Hire Date in the **Days Worked** column.
- For each employee, enter the formula =Days Worked/365 in the **Years Worked** column. Make sure that the **Years Worked** value returns two decimal places. 

![alt text](https://github.com/Daphne-Tang/Clustering-of-Baltimore-City-Employees-Salaries-Data/blob/main/Screenshots%20for%20Instructions/Adding%20Days%20and%20Years%20Worked.png)

3. In the **FY2020 Data** worksheet, filter the **AgencyName** column for each department. Copy and paste each department's data into a separate worksheet with the title **FY2020 [Department Name].**
4. For each department: 
- Filter the **Annual Salary** column to make sure that there are no negative or 0 values. 
- Filter the **Gross Pay** column to make sure that there are no negative or 0 values. 
- Filter the **Years Worked** column to make sure that there are no impossible numbers (e.g. 120 years worked). 
- Copy and paste the data into a new Excel workbook (**Analysis Part 2**) that has separate tabs for each department's newly filtered data.
- Calculate the average annual salary, gross pay, and years worked for each department with the AVERAGE function. 
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

14. Conduct a cluster analysis. In the Solver, set the maximum time limit to 60 seconds and the integer optimality to 0. 
15. Create 3 scatterplots showing the clusters on the graphs with different colors. 
