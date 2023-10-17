# PowerBI_Dashboard
HR power BI dashboard for attendance percentage 
![presence power Bi](https://github.com/tanzeela01/PowerBI_Dashboard/assets/112768939/0ae92d0a-ca7b-4411-9159-6a5657b0db58)
Certainly! Here's a template for a README file for your project that involves analyzing a company's employee attendance records over three months:

# Employee Attendance Analysis Project

![Image](screenshot.png) (You can include a relevant image or screenshot of your project here)

## Project Overview

This project is a guided analysis of employee attendance records for a company over a three-month period. The dataset used contains attendance data for multiple employees. The main objectives of this project are as follows:

1. Calculate real-time attendance percentages for various categories, including:
   - Sick leave percentage
   - Work from home (WFH) percentage
   - The trends in these percentages, particularly in weekdays

## Data Cleaning and Transformation

In this project, the provided dataset was initially in a wide format with dates scattered across multiple columns. To facilitate analysis, the data was transformed into a long format, which made it easier to work with. Key data preparation steps include:

- Converting the wide table into a long one to gather all the date-related information into a single column for analysis.

## Making measures in power BI
Calculating the total working days 
DAX syntax
"Total Working Days =
VAR totaldays = COUNT('final_data'[Value])
VAR noworkdays = CALCULATE(
    COUNT('final_data'[Value]),
    'final_data'[Value] IN { "WO", "HO" }
)
RETURN totaldays - noworkdays
"
Calculating work from home count 
"WFH C = 
SWITCH(
    TRUE(),
    'final_data'[Value] = "WFH", 1,
    'final_data'[Value] = "HWFH", 0.5,
    0
)
"
Calculating work from home percentage
WFH Count = SUM('final_data'[WFH C])
calculating present days 
"Present days = 
VAR Presentdays = CALCULATE(COUNT('final_data'[Value]), 'final_data'[Value] = "p")
RETURN Presentdays
"
caluculating presence percentage
"PRESENCE % = DIVIDE([Present days],'Measure Table'[Total Working Days],0)"
caluculating Sick leave percentage
SL % = DIVIDE([SL C],[Total Working Days],0)
## Analysis and Objectives

The main objectives of this project's analysis are:

1. **Calculate Attendance Percentages:**
   - Calculate the Sick leave percentage by analyzing the data for sick leave entries.
   - Calculate the Work from home (WFH) percentage by analyzing the data for WFH entries.

2. **Trend Analysis:**
   - Analyze the trends in these percentages, especially on weekdays.
   - Identify patterns and insights, such as the highest WFH percentage on a specific day of the week (e.g., Friday).




## Acknowledgments

All the data files are provided by the youtube channel "Code Basics" by dhaval patel.





