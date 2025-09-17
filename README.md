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
import numpy as np
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data
```
<img width="857" height="665" alt="image" src="https://github.com/user-attachments/assets/d5f1efa8-f8c7-4a9f-9732-de12229385ae" />

```
data.head(4)
```
<img width="740" height="163" alt="image" src="https://github.com/user-attachments/assets/8937c638-4f43-46f6-b409-a65e2786f825" />

```
data.tail(7)
```
<img width="764" height="252" alt="image" src="https://github.com/user-attachments/assets/3cea74f5-49c4-4eaa-b8ef-48ac0a5d8afc" />

```
data.isnull()
```
<img width="621" height="654" alt="image" src="https://github.com/user-attachments/assets/3871998d-f3f5-43cb-a994-96abc734aa61" />

```
data.notnull()
```
<img width="604" height="656" alt="image" src="https://github.com/user-attachments/assets/9ca1abe6-83f0-48fe-a5af-ae6383d23489" />

```
data.isnull().sum()
```
<img width="136" height="421" alt="image" src="https://github.com/user-attachments/assets/ebef172f-562b-4384-91fc-9147b000a3ce" />

```
data.isnull().any()
```
<img width="146" height="425" alt="image" src="https://github.com/user-attachments/assets/83ef6f9e-c50c-47f2-9c5d-c0f0f772f55b" />

```
data.dropna(axis=1)
```
<img width="224" height="653" alt="image" src="https://github.com/user-attachments/assets/0e43833d-af76-4acc-b108-6c2755414c51" />

```
data.dropna(axis=0)
```
<img width="764" height="433" alt="image" src="https://github.com/user-attachments/assets/05de09b5-8cc9-4996-b39e-c568c856d376" />

```
data.fillna(0)
```
<img width="772" height="655" alt="image" src="https://github.com/user-attachments/assets/5fb5806b-1068-4fa3-add6-657fb26e91ed" />

```
data.fillna(method="ffill")
```
<img width="1265" height="690" alt="image" src="https://github.com/user-attachments/assets/07fcb58c-70ee-4377-9e4a-5b30963f5dc0" />

```
data.bfill()
```
<img width="763" height="653" alt="image" src="https://github.com/user-attachments/assets/683a6d6b-166c-4e61-81a6-be6f11bae6a1" />

```
data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```
<img width="769" height="660" alt="image" src="https://github.com/user-attachments/assets/7a526cea-1a5a-40b5-ad15-e2c3b7d349f1" />

```
ir=pd.read_csv("/content/iris.csv")
ir
```
<img width="502" height="392" alt="image" src="https://github.com/user-attachments/assets/e5e4388f-1b02-482b-98d3-ce24c137223c" />

```
ir.describe()
```
<img width="438" height="274" alt="image" src="https://github.com/user-attachments/assets/f3e7f47a-2fd4-4ec0-8174-04e0fd01784d" />

```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```
<img width="514" height="432" alt="image" src="https://github.com/user-attachments/assets/5b1cf7c1-4c62-4e56-9df4-4881a23dac89" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="71" height="30" alt="image" src="https://github.com/user-attachments/assets/58c9828f-f003-4af0-98e6-d89d8e7f1412" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="135" height="194" alt="image" src="https://github.com/user-attachments/assets/abc955d1-d333-4378-86cc-91ff3bf53bf2" />

```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```
<img width="493" height="388" alt="image" src="https://github.com/user-attachments/assets/2e2365fc-da1c-43bc-bd2f-6a48d9d0d43a" />

```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="136" height="415" alt="image" src="https://github.com/user-attachments/assets/b04a0919-b735-475e-8420-4228e975cfa9" />

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```
<img width="542" height="495" alt="image" src="https://github.com/user-attachments/assets/0e5bfa80-6531-4727-bbe7-c205175be312" />


# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
