# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
REGISTER NO : 212224040236
NAME:PRABHAKARAN P
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv('drive/MyDrive/heights.csv')
print(df)

       name  height
0     mohan     5.9
1     maria     5.2
2     sakib     5.1
3       tao     5.5
4     virat     4.9
5    khusbu     5.4
6    dmitry     6.2
7    selena     6.5
8      john     7.1
9     imran    14.5
10     jose     6.1
11  deepika     5.6
12   yoseph     1.2
13    binod     5.5

pd.DataFrame(df)

name	height
0	mohan	5.9
1	maria	5.2
2	sakib	5.1
3	tao	5.5
4	virat	4.9
5	khusbu	5.4
6	dmitry	6.2
7	selena	6.5
8	john	7.1
9	imran	14.5
10	jose	6.1
11	deepika	5.6
12	yoseph	1.2
13	binod	5.5

sns.boxplot(data=df)
![download](https://github.com/user-attachments/assets/1d28a65a-8418-4778-80b3-9c6a4742e82a)

sns.scatterplot(data=df)
![download](https://github.com/user-attachments/assets/01496d83-849d-41fe-8571-5028bb8bef50)

Q1 = df['height'].quantile(0.25)
Q3 = df['height'].quantile(0.75)
IQR = Q3 - Q1
print(IQR)

0.9249999999999998

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR

lower_bound

3.8625000000000003

upper_bound

7.5625

outliers = df[(df['height'] < lower_bound) | (df['height'] > upper_bound)]
print(outliers)

 name  height
9    imran    14.5
12  yoseph     1.2

print("Q1 = ", Q1)
print("Q3 = ",Q3)
print("IQR = ", IQR)
print("Lower bound = ", lower_bound)
print("Upper bound = ", upper_bound)
print( outliers)

Q1 =  5.25
Q3 =  6.175
IQR =  0.9249999999999998
Lower bound =  3.8625000000000003
Upper bound =  7.5625
      name  height
9    imran    14.5
12  yoseph     1.2

new=df[(df['height'] > lower_bound) & (df['height'] < upper_bound)]
print(new)

 name  height
0     mohan     5.9
1     maria     5.2
2     sakib     5.1
3       tao     5.5
4     virat     4.9
5    khusbu     5.4
6    dmitry     6.2
7    selena     6.5
8      john     7.1
10     jose     6.1
11  deepika     5.6
13    binod     5.5

sns.boxplot(data=new)

![download](https://github.com/user-attachments/assets/e5a76eb3-8dfd-449d-a936-336cb6e7fac4)

sns.scatterplot(data=new)

![download](https://github.com/user-attachments/assets/e5a16aa7-e684-4d19-9784-5c611ae6ef34)



```

# Result
       The given data has been used to perform data cleaning and save the cleaned data to a file.   
