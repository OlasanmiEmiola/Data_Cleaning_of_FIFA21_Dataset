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

* The raw what imported into the Google sheets and then downloaded into Excel Spreadsheets. This process took care of the special characters in the Long name column.
* There no empty cells on the ***Nationality*** Column   
* The ***age*** column was checked for outliners. I founf three players with ages of 43 and 53. I checked it out online and found that it was true. So the age columns was left as it.
* The ***Club*** column was checked for missing values 

* The ***contract*** Column carried the Contract start year, contract end year, free players 1.e. no contract, and the players on Loan    

![Image 1](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Contract.png)

* Use text to column to separate the year using the delimiter( ~) was used to extarct the years into different columns. 
  This argument  ***IF(ISNUMBER(K2),"On Contract",IF(ISNUMBER(SEARCH("Loan",K2)),"On Loan",IF(ISNUMBER(SEARCH("Free",K2)),"Free","")))***  was used to format the contract start year to seperate the players the are *On Contract*, *Loan*, and *Free*.  

![Image 2](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Final%20Contract.png)
 

***
* The ***height*** column has different units i.e. cm and ft/in. I formatted the entire column using the argument ***IF(ISNUMBER(SEARCH("cm",P2)),CONCATENATE((INT((LEFT(P2,3))/30.48)),"'",ROUND((LEFT(P2,3)/2.54)-(INT(LEFT(P2,3)/30.48)*12),0),""""),P2)***. This arguments searches for the "cm" and extract it out the number, then the number are formated to ft/inches. Note, the argument leaves out the rows that were already formatted in ft/in 

![inital Weight and Height](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/initial_height_weight.png) 

* The ***weight*** column has different units i.e lbs and kg. I formatted the entire column using using the argument
***IF(ISNUMBER(SEARCH("kg",R2)),ROUND(CONVERT(SUBSTITUTE(R2,RIGHT(R2,2),""),"kg","lbm"),0),SUBSTITUTE(R2,RIGHT(R2,3),""))***. This convert the weight (kg) into lbs rounded the number to nearest whole value and leaves out the rows already in lbs 

![Final Height and Weight](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Height_Weight.png)

***

* The ***joined date*** was formatted as Excel date and there were no null entries 

* The ***Loan Date End*** was also formattted in the Excel date formatted

*  I used this argument ***M2-YEAR(T2)*** on the joined date to determine the number of years the players will be playing for the club to create a ***Years of Playing*** column 

***
* The *Value column*, *Weekly wage*, and *Release Clause* has no missing values but were formatted in "M" and "K" indicating Milions and Thousands In Euros

![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/initial_wage.png)

* The ***Value*** column was  formatted using the argument ***IF(ISNUMBER(SEARCH("M",Y2)),SUBSTITUTE(Y2,RIGHT(Y2,1),"")*1000000,IF(RIGHT(Y2,1)="K",SUBSTITUTE(Y2,RIGHT(Y2,1),"")*1000,NUMBERVALUE(Y2))). This extraced the Ks and Ms, Multiplied it with 1000 and 1000000 respectively 

* The ***weekly wage*** column was formatted using the argument ***IF(RIGHT(AA2,1)="K",SUBSTITUTE(AA2,RIGHT(AA2,1),"")*1000,NUMBERVALUE(AA2))> This extracted the Ks and and multiplied by 1000, leaving out the rows that were already in the correct format. 

* The ***Release Clause*** was Formatted using the ***IF(ISNUMBER(SEARCH("M",AC2)),SUBSTITUTE(AC2,RIGHT(AC2,1),"")*1000000,IF(RIGHT(AC2,1)="K",SUBSTITUTE(AC2,RIGHT(AC2,1),"")*1000,NUMBERVALUE(AC2)))***. This extraced the Ks and Ms, Multiplied it with 1000 and 1000000 respectively 

![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Final_Wage_value.png)

***
* There was no identified issues with the  ***attacking, crossing, finishing, heading_accuracy, Volleys, Skill, dribbling, curves, Fk accuracy, shortpassing, Fk Acurracy, long passing , ball control, movement, acceleration, sprint speed, agility, reactions, balance, power, shot power, jumping, stamina, strenght, longshots, mentality, aggressions, interceptions, postioning, vision, penalties, composure, defending, marking, standing tackle, sliding tackle, goalkeeping, GK postioning, GK handling, Gk, Kicking, GK postioning, GK reflexes, Total stats, Base stats, D/W, A/W, PAC, SHO, PAS, DRI, DEF, DRI, and PHY*** Columns.
***
The ***IR,W/F and SM*** were indicated with the star ratings of the player. These Colomns were  formattied using the Text to columns to remove the special Characters i.e stars 

![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/IR_SM.png)

* **After all the neccesary cleaning has been done, the filter function was used on all the columns to check for outliners.**

##  Snippets  of the cleaned data

![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Screenshot%20(32).png)

![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Screenshot%20(33).png)

![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Screenshot%20(34).png)


##  Recommendation
  This dataset is ready for further analysis and statistical modelling 

[Click Here to download the Clean data](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/FIFA21_cleaned_dataset.xlsx)
