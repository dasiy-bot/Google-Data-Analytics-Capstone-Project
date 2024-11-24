# **Student Performance Analysis**

## **Project Overview**  
This project analyzes various factors influencing student performance in exams. By exploring attributes such as hours studied, attendance, parental involvement, and others, we aim to identify key drivers of academic success and provide actionable insights.

## **Technologies & Tools Used**  
- **R** & **ggplot2**: Used for data cleaning, analysis, and visualization.  
- **Tableau**: For creating interactive dashboards to explore insights.

## **Dataset Overview**  
The dataset contains attributes related to student behaviors, environments, and academic outcomes:

| **Attribute**               | **Description**                                                                 |
|-----------------------------|---------------------------------------------------------------------------------|
| **Hours_Studied**            | Hours spent studying per week.                                                  |
| **Attendance**               | Percentage of classes attended.                                                |
| **Parental_Involvement**     | Level of parental involvement (Low, Medium, High).                             |
| **Extracurricular_Activities** | Participation in extracurricular activities (Yes, No).                        |
| **Sleep_Hours**              | Average hours of sleep per night.                                               |
| **Motivation_Level**         | Student's motivation level (Low, Medium, High).                                |
| **Exam_Score**               | Final exam score.                                                              |

## **Key Steps**  

1. **Inspect the Structure**  
   - Use R functions (`str()`, `head()`, `summary()`) to analyze the structure and key statistics of the dataset.

2. **Handle Missing Data**  
   - Identify missing values and visualize missingness using bar charts or heatmaps with **ggplot2**.

3. **Separate Data Types**  
   - Organize variables into numerical, categorical, and ordinal types for further analysis.

4. **Visualize the Data**  
   - Create visualizations using **ggplot2**:  
     - **Scatterplots**: To analyze relationships (e.g., Hours_Studied vs. Exam_Score).  
     - **Boxplots**: To compare exam scores across categories like **Gender** or **School Type**.  
     - **Histograms**: For distributions of variables like **Sleep Hours** and **Attendance**.  
   - Develop interactive **Tableau** dashboards for deeper analysis.

## **Key Findings**  
- **Hours_Studied** and **Motivation_Level** are positively correlated with exam performance.  
- **Parental_Involvement** and **Access_to_Resources** contribute significantly to student success.  
- **Sleep** and **Physical Activity** impact academic consistency.

## **Sources**  
The dataset used in this project is synthetic and designed for educational and analysis purposes.  
- [Student Performance Factors on Kaggle](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors)


## **Future Enhancements** ##
- Add machine learning models to predict student performance based on key features.
- Expand the dataset with additional attributes for more comprehensive analysis.
- Enhance **Tableau** dashboards for a more interactive user experience.

## **License** ##
This project is licensed under the [CC0: Public Domain Dedication.](https://creativecommons.org/publicdomain/zero/1.0/)
