<img width="1204" alt="image" src="https://github.com/user-attachments/assets/10cfb539-64a2-49cb-a59f-89ed9ac07e60" />


```
DAX USED
```
```
AVG handling time = 
VAR totalCallDuration=SUM('01 Call-Center-Dataset'[talk duration])
VAR totalCallAnsweres=CALCULATE(COUNTA('01 Call-Center-Dataset'[answered (Y/N)]),'01 Call-Center-Dataset'[answered (Y/N)]="Y")
RETURN 
    DIVIDE(totalCallDuration,totalCallAnsweres,0)
```
```
call abandoned % = 
VAR CallsNotAnswered=CALCULATE(COUNTA('01 Call-Center-Dataset'[call id]),'01 Call-Center-Dataset'[answered (Y/N)]="N")
RETURN 
   FORMAT( DIVIDE(CallsNotAnswered,[total calls],0),"0.00%")
```
```
call resolved % = 
VAR TotalresolvedCalls=CALCULATE(COUNTA('01 Call-Center-Dataset'[call id]), '01 Call-Center-Dataset'[resolved]="Y")
VAR TotalCalls=CALCULATE(COUNTA('01 Call-Center-Dataset'[call id]),'01 Call-Center-Dataset'[answered (Y/N)]="Y")
RETURN 
    FORMAT(DIVIDE(TotalresolvedCalls,TotalCalls,0),"0.00%")
```
```
CSAT = 

VAR totalratings=SUM('01 Call-Center-Dataset'[satisfaction rating])
VAR ratings=COUNT('01 Call-Center-Dataset'[satisfaction rating])
RETURN 
    FORMAT(DIVIDE(totalratings,ratings*5,0),"0.00%")
```
```
last call = 
MAX('01 Call-Center-Dataset'[date time])
```
```
speed of answer = 
VAR totalCallDuration=SUM('01 Call-Center-Dataset'[speed of answer in seconds])
VAR totalCallAnsweres=CALCULATE(COUNTA('01 Call-Center-Dataset'[answered (Y/N)]),'01 Call-Center-Dataset'[answered (Y/N)]="Y")
RETURN 
    DIVIDE(totalCallDuration,totalCallAnsweres,0)
```
```
total calls = 

DISTINCTCOUNT('01 Call-Center-Dataset'[call id])
```

