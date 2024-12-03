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

1. **Load the Dataset**
´´´r
   # Load data
perfactors <- read.csv("path/to/StudentPerformanceFactors.csv")

Rows: 6607 Columns: 20                 [] 89.75GB/s, eta:  0s
── Column specification ───────────────
Delimiter: ","
chr (13): Parental_Involvement, Acc...
dbl  (7): Hours_Studied, Attendance...

   # Preview the first few rows
head(StudentPerformanceFactors)

# A tibble: 6 × 20
  Hours_Studied Attendance
          <dbl>      <dbl>
1            23         84
2            19         64
3            24         98
4            29         89
5            19         92
6            19         88
#   18 more variables:
#   Parental_Involvement <chr>,
#   Access_to_Resources <chr>,
#   Extracurricular_Activities <chr>,
#   Sleep_Hours <dbl>,
#   Previous_Scores <dbl>,
#   Motivation_Level <chr>, …

2. **Inspect the Structure**  
  ```r
# Get data structure
str(perfactors)

> str(perfactors)
tibble [6,378 × 21] (S3: tbl_df/tbl/data.frame)
 $ Hours_Studied             : num [1:6378] 23 19 24 29 19 19 29 25 17 23 ...
 $ Attendance                : num [1:6378] 84 64 98 89 92 88 84 78 94 98 ...
 $ Parental_Involvement      : Factor w/ 3 levels "high","low","medium": 2 2 3 2 3 3 3 2 3 3 ...
 $ Access_to_Resources       : chr [1:6378] "high" "medium" "medium" "medium" ...
 $ Extracurricular_Activities: chr [1:6378] "no" "no" "yes" "yes" ...
 $ Sleep_Hours               : num [1:6378] 7 8 7 8 6 8 7 6 6 8 ...
 $ Previous_Scores           : num [1:6378] 73 59 91 98 65 89 68 50 80 71 ...
 $ Motivation_Level          : chr [1:6378] "low" "low" "medium" "medium" ...
 $ Internet_Access           : chr [1:6378] "yes" "yes" "yes" "yes" ...
 $ Tutoring_Sessions         : num [1:6378] 0 2 2 1 3 3 1 1 0 0 ...
 $ Family_Income             : chr [1:6378] "low" "medium" "medium" "medium" ...
 $ Teacher_Quality           : chr [1:6378] "medium" "medium" "medium" "medium" ...
 $ School_Type               : chr [1:6378] "public" "public" "public" "public" ...
 $ Peer_Influence            : chr [1:6378] "positive" "negative" "neutral" "negative" ...
 $ Physical_Activity         : num [1:6378] 3 4 4 4 4 3 2 2 1 5 ...
 $ Learning_Disabilities     : chr [1:6378] "no" "no" "no" "no" ...
 $ Parental_Education_Level  : chr [1:6378] "high school" "college" "postgraduate" "high school" ...
 $ Distance_from_Home        : chr [1:6378] "near" "moderate" "near" "moderate" ...
 $ Gender                    : chr [1:6378] "male" "female" "male" "male" ...
 $ Exam_Score                : num [1:6378] 67 61 74 71 70 71 67 66 69 72 ...
 $ Previous_Scorse           : num [1:6378] 73 59 91 98 65 89 68 50 80 71 ...
 - attr(*, "na.action")= 'omit' Named int [1:229] 34 128 241 276 317 360 381 397 403 409 ...
  ..- attr(*, "names")= chr [1:229] "34" "128" "241" "276" ...

# Summary statistics for all columns

> summary(perfactors)
 Hours_Studied     Attendance    
 Min.   : 1.00   Min.   : 60.00  
 1st Qu.:16.00   1st Qu.: 70.00  
 Median :20.00   Median : 80.00  
 Mean   :19.98   Mean   : 80.02  
 3rd Qu.:24.00   3rd Qu.: 90.00  
 Max.   :44.00   Max.   :100.00  
 Parental_Involvement
 high  :1836         
 low   :1291         
 medium:3251         
                                         
 Access_to_Resources
 Length:6378        
 Class :character   
 Mode  :character   
                                       
 Extracurricular_Activities
 Length:6378               
 Class :character          
 Mode  :character          
                                                     
  Sleep_Hours     Previous_Scores 
 Min.   : 4.000   Min.   : 50.00  
 1st Qu.: 6.000   1st Qu.: 63.00  
 Median : 7.000   Median : 75.00  
 Mean   : 7.035   Mean   : 75.07  
 3rd Qu.: 8.000   3rd Qu.: 88.00  
 Max.   :10.000   Max.   :100.00  
 Motivation_Level   Internet_Access   
 Length:6378        Length:6378       
 Class :character   Class :character  
 Mode  :character   Mode  :character  
                                                                           
 Tutoring_Sessions Family_Income     
 Min.   :0.000     Length:6378       
 1st Qu.:1.000     Class :character  
 Median :1.000     Mode  :character  
 Mean   :1.495                       
 3rd Qu.:2.000                       
 Max.   :8.000                       
 Teacher_Quality    School_Type       
 Length:6378        Length:6378       
 Class :character   Class :character  
 Mode  :character   Mode  :character  
                                                                           
 Peer_Influence     Physical_Activity
 Length:6378        Min.   :0.000    
 Class :character   1st Qu.:2.000    
 Mode  :character   Median :3.000    
                    Mean   :2.973    
                    3rd Qu.:4.000    
                    Max.   :6.000    
 Learning_Disabilities
 Length:6378          
 Class :character     
 Mode  :character     
                                         
 Parental_Education_Level
 Length:6378             
 Class :character        
 Mode  :character        
                                                 
 Distance_from_Home    Gender         
 Length:6378        Length:6378       
 Class :character   Class :character  
 Mode  :character   Mode  :character  
                                      
                                                                           
   Exam_Score     Previous_Scorse 
 Min.   : 55.00   Min.   : 50.00  
 1st Qu.: 65.00   1st Qu.: 63.00  
 Median : 67.00   Median : 75.00  
 Mean   : 67.25   Mean   : 75.07  
 3rd Qu.: 69.00   3rd Qu.: 88.00  
 Max.   :101.00   Max.   :100.00


2. **Handle Missing Data**  

> colSums(is.na(perfactors))
             Hours_Studied 
                         0 
                Attendance 
                         0 
      Parental_Involvement 
                         0 
       Access_to_Resources 
                         0 
Extracurricular_Activities 
                         0 
               Sleep_Hours 
                         0 
           Previous_Scores 
                         0 
          Motivation_Level 
                         0 
           Internet_Access 
                         0 
         Tutoring_Sessions 
                         0 
             Family_Income 
                         0 
           Teacher_Quality 
                        78 
               School_Type 
                         0 
            Peer_Influence 
                         0 
         Physical_Activity 
                         0 
     Learning_Disabilities 
                         0 
  Parental_Education_Level 
                        90 
        Distance_from_Home 
                        67 
                    Gender 
                         0 
                Exam_Score 
                         0 
> perfactors <- na.omit(perfactors)
> sum(duplicated(perfactors))
[1] 0

3. **Separate Data Types**  
perfactors$Hours_Studied <- as.numeric(perfactors$Hours_Studied)
> perfactors$Attendance <- as.numeric(perfactors$Attendance)
> perfactors$Sleep_Hours <- as.numeric(perfactors$Sleep_Hours)
> perfactors$Previous_Scorse <- as.numeric(perfactors$Previous_Scores)
> perfactors$Previous_Scores <- as.numeric(perfactors$Previous_Scores)
> perfactors$Parental_Involvement <- as.factor(perfactors$Parental_Involvement)

4. **Visualize the Data**  
   > ggplot(perfactors, aes(x = Exam_Score)) +
+     geom_histogram(binwidth = 5, fill = "blue", color = "black")

> ggplot(perfactors, aes(x = Teacher_Quality)) +
+     geom_bar(fill = "orange")


   - Develop interactive **Tableau** dashboards for deeper analysis.

## **Key Findings**  
- **Hours_Studied** and **Motivation_Level** are positively correlated with exam performance.  
- **Parental_Involvement** and **Access_to_Resources** contribute significantly to student success.  
- **Sleep** and **Physical Activity** impact academic consistency.

## **Sources**  
The dataset used in this project is synthetic and designed for educational and analysis purposes.  
- [Student Performance Factors on Kaggle](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors)


## **Future Enhancements** ##
- Expand the dataset with additional attributes for more comprehensive analysis.
- Enhance **Tableau** dashboards for a more interactive user experience.

## **License** ##
This project is licensed under the [CC0: Public Domain Dedication.](https://creativecommons.org/publicdomain/zero/1.0/)
