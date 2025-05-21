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
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df=pd.read_csv("sample.csv")
df
```
![image](https://github.com/user-attachments/assets/05537c3d-265e-422d-baf8-676c15f525f3)

```
df.isnull()
```
![image](https://github.com/user-attachments/assets/2e81abb5-a677-413f-9f60-9a048080aacf)

```
df.notnull()
```
![image](https://github.com/user-attachments/assets/5086f870-2046-4a74-bd55-a68b20f5051d)

```
df.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/5f37b026-3f2f-41fe-8e00-b7de629e3f88)

```
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/a0c225d9-9004-4d13-b705-589e32e2ed55)

```
dfs=df[df['TOTAL']>270]
dfs
```
![image](https://github.com/user-attachments/assets/daad6535-7d94-4b32-9f80-b94d273799fd)
```
dfs=df[df['NAME'].str.startswith(('A','K'))&(df['TOTAL']>250)]
dfs
```
![image](https://github.com/user-attachments/assets/b032c0ac-028d-4b4f-8798-3daaf3720988)

```
df.iloc[:4]
```
![image](https://github.com/user-attachments/assets/3462e82f-7f38-4c1b-9be0-ed0b05de2a84)
```
df.iloc[0:4,1:4]
```
![image](https://github.com/user-attachments/assets/cced36ff-979c-475b-a187-063bb5f48b66)

```
df.iloc[[1,3,5],[1,3]]
```
![image](https://github.com/user-attachments/assets/8a361af7-45d7-441f-bbd0-b8cc18210482)
```
df
```
![image](https://github.com/user-attachments/assets/cf09708a-15ab-420e-9243-b9868be4907c)
```
dff=df.fillna(0)
dff
```
![image](https://github.com/user-attachments/assets/a33cc0f1-75a6-44e3-87c6-199dd34fdf35)

```
df['TOTAL'].fillna(value=df['TOTAL'].mean())
```
![image](https://github.com/user-attachments/assets/7dab1f63-8cb7-431e-805f-a8ff71296286)
```
df.ffill()
```
![image](https://github.com/user-attachments/assets/578b5846-b2c2-40de-8771-95db29cd9952)

```
df.bfill()
```
![image](https://github.com/user-attachments/assets/f1ce19c7-ed25-4952-9a1b-c7dc8a4da802)
```
df['TOTAL'] = df['TOTAL'].fillna(value=df['TOTAL'].mean())
df
```
![image](https://github.com/user-attachments/assets/4cd962a6-0dd7-4ad7-93ef-98a5ca556275)

# Result
          <<include your Result here>>
