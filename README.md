# Student-Performance-Analytics-Dashboard

## Project Overview

This project analyzes student performance using a dataset containing academic, behavioral, and socioeconomic factors. The goal of this Power BI dashboard is to identify which factors are most associated with student exam performance and provide clear visual insights for decision-making.

The dashboard focuses on understanding how attendance, study hours, previous scores, access to resources, parental involvement, teacher quality, and other factors affect students' exam scores.

## Dataset

The dataset contains student-level performance records with multiple factors related to academic outcomes.

### Key Dataset Information

- Total students: 6,607
- Target variable: Exam Score
- Tool used: Microsoft Power BI
- Data format: CSV

### Main Columns Used

| Column | Description |
|---|---|
| Hours_Studied | Number of hours studied by the student |
| Attendance | Student attendance percentage |
| Previous_Scores | Student's previous academic score |
| Exam_Score | Final exam score |
| Access_to_Resources | Level of access to academic resources |
| Parental_Involvement | Level of parental involvement |
| Motivation_Level | Student motivation level |
| Teacher_Quality | Quality level of teaching |
| Family_Income | Student family income category |
| Internet_Access | Whether the student has internet access |
| Learning_Disabilities | Whether the student has learning disabilities |
| School_Type | Type of school |
| Gender | Student gender |

## Data Cleaning

Before building the dashboard, the dataset was cleaned in Power Query.

### Cleaning Steps

- Replaced null values with `Unknown`
- Checked column data types
- Converted numeric columns to whole number format
- Created calculated columns for grouping and segmentation
- Created DAX measures for KPIs and analysis

### Columns with Missing Values

| Column | Action Taken |
|---|---|
| Teacher_Quality | Null values replaced with Unknown |
| Parental_Education_Level | Null values replaced with Unknown |
| Distance_from_Home | Null values replaced with Unknown |

## DAX Measures

The following DAX measures were created for the dashboard:

### DAX
Total Students = COUNTROWS(StudentPerformanceFactors)

Average Exam Score = AVERAGE(StudentPerformanceFactors[Exam_Score])

Average Attendance = AVERAGE(StudentPerformanceFactors[Attendance])

Average Study Hours = AVERAGE(StudentPerformanceFactors[Hours_Studied])

Average Previous Score = AVERAGE(StudentPerformanceFactors[Previous_Scores])

High Risk Students =
CALCULATE(
    COUNTROWS(StudentPerformanceFactors),
    StudentPerformanceFactors[Exam_Score] < 60
)

High Risk Rate =
DIVIDE(
    [High Risk Students],
    [Total Students]
)


### Calculated Columns

### Performance Level

### Dax

Performance Level =
SWITCH(
    TRUE(),
    StudentPerformanceFactors[Exam_Score] < 60, "High Risk",
    StudentPerformanceFactors[Exam_Score] < 70, "Average",
    StudentPerformanceFactors[Exam_Score] < 80, "Good",
    "Excellent"
)

### Attendance Group

### Dax
Attendance Group =
SWITCH(
    TRUE(),
    StudentPerformanceFactors[Attendance] < 70, "60% - 69%",
    StudentPerformanceFactors[Attendance] < 80, "70% - 79%",
    StudentPerformanceFactors[Attendance] < 90, "80% - 89%",
    "90% - 100%"
)

### Study Hours Group

### Dax

Study Hours Group =
SWITCH(
    TRUE(),
    StudentPerformanceFactors[Hours_Studied] < 10, "Less than 10",
    StudentPerformanceFactors[Hours_Studied] < 20, "10 - 19",
    StudentPerformanceFactors[Hours_Studied] < 30, "20 - 29",
    "30+"
)

### Dashboard Pages

## Page 1: Overview

This page provides a high-level summary of student performance.

Visuals Included - 
- Total Students card,
- Average Exam Score card,
- Average Attendance card,
- Average Study Hours card,
- High Risk Students card,
- Average Previous Score card,
- Exam Score distribution chart,
- Students by Performance Level,
- Average Exam Score by Gender,
- Also some Slicers to get a clear picture.

Purpose

This page gives a quick overview of overall student performance and helps users understand the general condition of the dataset.

## Page 2: Academic Factors

This page focuses on academic behavior and its relationship with exam scores.

Visuals Included - 
- Average Exam Score by Attendance Group,
- Average Exam Score by Study Hours Group,
- Exam Score vs Attendance scatter plot,
- Exam Score vs Previous Scores scatter plot. 

Key Focus Areas - 
- Attendance impact on exam performance,
- Study hours impact on exam performance,
- Relationship between previous scores and final exam score,
- Effect of tutoring sessions on student outcomes. 

## Page 3: Support and Socioeconomic Factors

This page analyzes non-academic factors that may influence student performance.

Visuals Included - 
- Average Exam Score by Parental Involvement,
- Average Exam Score by Access to Resources,
- Average Exam Score by Teacher Quality,
- Average Exam Score by Family Income,
- Average Exam Score by Internet Access. 

Purpose

This section helps identify how family background, school support, and access to learning resources affect student outcomes.


## Page 4: Risk Analysis

This page identifies students who may need academic support.

Visuals Included -
Students by Performance Level -
- Risk Level by Learning Disabilities,
- High Risk Students by Attendance Group,
- High Risk Students by Study Hours Group,
- Risk matrix by Motivation Level and Performance Level. 

Purpose

The goal of this page is to identify patterns among high-risk students and support early intervention planning.

## Page 5: Key Influencer Analysis

Power BI's Key Influencers visual was used to identify which factors have the strongest relationship with exam scores.

Fields Used - 
- Attendance,
- Hours_Studied,
- Previous_Scores,
- Tutoring_Sessions,
- Access_to_Resources,
- Parental_Involvement,
- Motivation_Level,
- Family_Income,
- Teacher_Quality,
- Internet_Access,
- Peer_Influence,
- Distance_from_Home, 

Key Insights

The dashboard revealed several important insights:

- 1. Attendance is one of the strongest factors associated with student exam performance.
  2. Students with higher study hours generally achieve better exam scores.
  3. Previous academic performance has a positive relationship with final exam scores.
  4. Students with better access to resources tend to perform better.
  5. Higher parental involvement is associated with better academic outcomes.
  6. Students with internet access have slightly higher average exam scores.
  7. Teacher quality and family income also show noticeable differences in average performance.
  8. Gender and school type show relatively small differences in exam scores.


### Conclusion

This Power BI dashboard provides a detailed analysis of student performance by combining academic, behavioral, and socioeconomic factors. The dashboard helps identify the main drivers of exam performance and highlights students who may require additional support.

The project demonstrates how Power BI can be used to transform raw education data into meaningful insights for academic performance monitoring and decision-making.
