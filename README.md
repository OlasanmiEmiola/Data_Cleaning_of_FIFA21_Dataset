# **DATA CLEANING CHALLENGE**
***
![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/no-revisions-cpIgNaazQ6w-unsplash.jpg)

***
## Introduction 
  This is a challenge was organized by [@PromiseNonso_](https://twitter.com/PromiseNonso_?s=20) and [@vicSomadina](https://twitter.com/vicSomadina?s=20) to help newbies to learn how to clean data using different tools. Excel was used to clean this data. 
  Data cleaning, also known as data cleansing, is the process of identifying and correcting or removing inaccurate, incomplete, irrelevant, or duplicate data in a dataset. The purpose of data cleaning is to ensure that the data is accurate, consistent, and reliable, so that it can be effectively used for analysis, reporting, or other purposes.Data cleaning can be performed in Excel using various techniques and functions available in the software. It invovles removing duplicates, handling missing values, correcting inconsistencies, validating data, standardizing data among others. 
  [click here to view raw file](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Raw_FIFA21.xlsx)
***
  
##  Aim of the project 
   The aim of the project is to clean the dataset and prepare it for more further analysis 
   
***

##  Objectives 
    The oject of the project is to 
    * Clean the inconsistent values 
    * Remove special characters
    * Standaradize each column 
    * Check for duplicates 
    * Data validation 
 
 ***  
  
## Project Cleaning Procedure
***

* The raw what imported into the Google sheets and then downloaded into Excel Spreadsheets, this process took care of the special characters in the Long name column 

![Image 1](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Contract.png)

* Contract column was separated in to  Contract start, Contract End, and Contract Type
* Use text to column to separate the year using the delimiter( ~) 
* ***IF(ISNUMBER(K2),"On Contract",IF(ISNUMBER(SEARCH("Loan",K2)),"On Loan",IF(ISNUMBER(SEARCH("Free",K2)),"Free","")))*** argument was used to Extract the contract Type 

![Image 2](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Final%20Contract.png)
 

***

* ***M2-YEAR(T2)*** argument used to determine the number of years the players will be playing for the club 

***

![inital Weight and Height](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/initial_height_weight.png) 


* The *height* Column was formatted using the argument ***IF(ISNUMBER(SEARCH("cm",P2)),CONCATENATE((INT((LEFT(P2,3))/30.48)),"'",ROUND((LEFT(P2,3)/2.54)-(INT(LEFT(P2,3)/30.48)*12),0),""""),P2)***. This formatted the height into ft and inches

* The *Weight* column was formatted using the argument
***IF(ISNUMBER(SEARCH("kg",R2)),ROUND(CONVERT(SUBSTITUTE(R2,RIGHT(R2,2),""),"kg","lbm"),0),SUBSTITUTE(R2,RIGHT(R2,3),""))***. This convert the weight into lbs rounded the number to nearest whole value 

![Final Height and Weight](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Height_Weight.png)

***

![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/initial_wage.png)

* The *Value* column was formatted using the argument ***IF(ISNUMBER(SEARCH("M",Y2)),SUBSTITUTE(Y2,RIGHT(Y2,1),"")*1000000,IF(RIGHT(Y2,1)="K",SUBSTITUTE(Y2,RIGHT(Y2,1),"")*1000,NUMBERVALUE(Y2)))

* The *weekly wage* column was formatted using the argument ***IF(RIGHT(AA2,1)="K",SUBSTITUTE(AA2,RIGHT(AA2,1),"")*1000,NUMBERVALUE(AA2))

* The *Release Clause* was Formatted using the ***IF(ISNUMBER(SEARCH("M",AC2)),SUBSTITUTE(AC2,RIGHT(AC2,1),"")*1000000,IF(RIGHT(AC2,1)="K",SUBSTITUTE(AC2,RIGHT(AC2,1),"")*1000,NUMBERVALUE(AC2)))***

![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Final_Wage_value.png)

***

![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/IR_SM.png)

The IR,W/F and SM was formattied using the Text to columns to remove the special Characters  

##  Snippets  of the cleaned data

![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Screenshot%20(32).png)

![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Screenshot%20(33).png)

![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Screenshot%20(34).png)


##  Recommendation
  This dataset is ready for further analysis and statistical modelling 

[Click Here to download the Clean data](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/FIFA21_cleaned_dataset.xlsx)
