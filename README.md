# Data Cleaning Challenge 
![Alt Text](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/no-revisions-cpIgNaazQ6w-unsplash.jpg)
## Introduction 
  This is a challenge organized by [@PromiseNonso_](https://twitter.com/PromiseNonso_?s=20) and [@vicSomadina](https://twitter.com/vicSomadina?s=20) to help newbies to learn how to clean data using different tools. Excel was used to clean this data. [click here to view raw file](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Raw_FIFA21.xlsx)
  
  
  
## Cleaning Procedure 
The raw what imported into the Google sheets and then downloaded into Excel Spreadsheets 

Contract column to be separated the Contract column to Contract start, Contract End, and Contract Type 
Use text to column to separate the year using the delimiter( ~) 

Initial Contract Column | Final Contract Column 

![Initial Contract Column](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/Contract.png) | 

* ***IF(ISNUMBER(K2),"On Contract",IF(ISNUMBER(SEARCH("Loan",K2)),"On Loan",IF(ISNUMBER(SEARCH("Free",K2)),"Free","")))*** argument was used to Extract the contract Type 
* ***M2-YEAR(T2)*** argument used to determine the years the players of each player 

* The *height* Column was formatted using the argument ***IF(ISNUMBER(SEARCH("cm",P2)),CONCATENATE((INT((LEFT(P2,3))/30.48)),"'",ROUND((LEFT(P2,3)/2.54)-(INT(LEFT(P2,3)/30.48)*12),0),""""),P2)***. This formatted the height into ft and inches

* The *Weight* column was formatted using the argument
***IF(ISNUMBER(SEARCH("kg",R2)),ROUND(CONVERT(SUBSTITUTE(R2,RIGHT(R2,2),""),"kg","lbm"),0),SUBSTITUTE(R2,RIGHT(R2,3),""))***. This convert the weight into lbs rounded the number to nearest whole value 

* The *Value* column was formatted using the argument ***IF(ISNUMBER(SEARCH("M",Y2)),SUBSTITUTE(Y2,RIGHT(Y2,1),"")*1000000,IF(RIGHT(Y2,1)="K",SUBSTITUTE(Y2,RIGHT(Y2,1),"")*1000,NUMBERVALUE(Y2)))

* The *weekly wage* column was formatted using the argument ***IF(RIGHT(AA2,1)="K",SUBSTITUTE(AA2,RIGHT(AA2,1),"")*1000,NUMBERVALUE(AA2))

* The *Release Clause* was Formatted using the ***IF(ISNUMBER(SEARCH("M",AC2)),SUBSTITUTE(AC2,RIGHT(AC2,1),"")*1000000,IF(RIGHT(AC2,1)="K",SUBSTITUTE(AC2,RIGHT(AC2,1),"")*1000,NUMBERVALUE(AC2)))***

The IR,W/F and SM was formattied using the Text to columns to remove the special Characters  
  
![](https://github.com/OlasanmiEmiola/FIFA21_Dataset/blob/main/IR_SM.png)


