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


```
import pandas as pd
import seaborn as sns
import numpy as np

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/892ed986-6774-4bdc-b910-84bcd0dbcf30)

```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/d70af40a-c2d2-49f7-bb3b-67bf531fa5c0)

```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/f3aa8237-6582-488e-a388-3990ea5893bf)
```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/fab1621a-8684-4e2b-b7b1-0aab3a85805e)

```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```

![image](https://github.com/user-attachments/assets/3afa6542-cd14-4463-9f40-d3249cd25d2a)


```
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

lower_bound
```
![image](https://github.com/user-attachments/assets/e4e519b5-d47f-4a5b-9aac-284b8fef4840)

```
upper_bound
```
![image](https://github.com/user-attachments/assets/0cf5d003-2832-4ce2-a13f-0cd8ab1e025a)
```
outliers=[x for x in age if x < lower_bound or x > upper_bound]

print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/0bfe9e1d-e61f-44ca-b7c6-77ce99328709)

```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![image](https://github.com/user-attachments/assets/27fde85f-ddf0-4e48-975d-467bbf0aff73)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/16477ac9-d93a-4e7a-b670-89b968b07121)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/f5724794-1a66-47eb-8281-aec4dda46513)

```
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data) 
df
```
![image](https://github.com/user-attachments/assets/03a452e7-fdf9-452d-936a-b0e74dd0504f)

```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

```
![image](https://github.com/user-attachments/assets/2b3d0f40-aee0-475f-8559-9ac7937ee416)
```
val = [12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 202, 72, 75, 78, 81, 84, 232, 87, 90, 93, 96, 99, 258]

out=[]
def d_o(val):
    ts=3
    m=np.mean(val)
    sd=np.std(val)
    for i in val:
        z=(i-m)/sd
        if np.abs(z)>ts:
            out.append(i)
    return out

op=d_o(val)
op
```
![image](https://github.com/user-attachments/assets/33d298da-0db5-4eb9-99f4-b9bb97bf53a3)

```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

id=pd.read_csv("iris.csv")
id



```

![image](https://github.com/user-attachments/assets/e4c331b1-4fb6-4341-9597-0e0bcb5d1105)

```
sns.boxplot(x='sepal_width',data=id)

```
![image](https://github.com/user-attachments/assets/3ec9ac5c-d61d-47a9-87e9-c6e52a71eab7)

```
c1=id.sepal_width.quantile(0.25)
c3=id.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/cac27388-f439-4d4d-ba1c-cf70f537a3a6)

```
rid=id[((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]

rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/bebd7cb5-19b8-49f1-9a69-fd8fca0154a3)

```
delid=id[~((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/7248be4b-03f3-4201-8ffd-a0ec3d184aad)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/6692d4f9-23ea-4003-86c2-3aa435c66b8f)
