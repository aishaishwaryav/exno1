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
data=pd.read_csv("/content/SAMPLEIDS.csv")
```
```
data.head(7)
```

<img width="999" height="320" alt="image" src="https://github.com/user-attachments/assets/ac2bc984-2d5b-4cf3-bdee-a13cd10f68fa" />

```
data.isnull()
```

<img width="672" height="700" alt="Screenshot 2025-09-10 135600" src="https://github.com/user-attachments/assets/93bd6124-2194-4ddf-a0bb-a9f9dc3c9358" />

```
data.isnull().sum()
```

<img width="118" height="452" alt="image" src="https://github.com/user-attachments/assets/b1b7fc4e-072c-4da4-8eca-29d5f5b99c7a" />

``
data.isnull().any()
``

<img width="159" height="453" alt="image" src="https://github.com/user-attachments/assets/5826fbf1-d130-46e5-8ea6-4f7d49735730" />

```
data.notnull()
```

<img width="647" height="688" alt="image" src="https://github.com/user-attachments/assets/4c0eae65-f1da-452d-a056-1391ea1f806d" />

```
data.fillna(0)
```

<img width="813" height="694" alt="image" src="https://github.com/user-attachments/assets/1ddaa5de-2af2-4cdb-81be-b195e49a7283" />

```
data.dropna(axis=0)
```

<img width="823" height="447" alt="image" src="https://github.com/user-attachments/assets/743ac9ea-6d38-438d-8612-938ac95b7a63" />

```
data.dropna(axis=1)
```

<img width="232" height="693" alt="image" src="https://github.com/user-attachments/assets/3069e90c-8819-4222-a9f6-b0c54fd4d1d6" />

```
data.fillna(method="ffill")
```

<img width="825" height="458" alt="image" src="https://github.com/user-attachments/assets/f49ddfe3-5f09-4609-b6e6-1cd3890d2307" />

```
data.fillna(method="bfill")
```

<img width="854" height="687" alt="image" src="https://github.com/user-attachments/assets/610d2127-e87f-4933-bbae-4632236222b2" />

```
data_dropped = data.dropna()
data_dropped
```

<img width="820" height="452" alt="image" src="https://github.com/user-attachments/assets/62e25184-645d-4828-9637-e9fa6bcccf92" />

```
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

<img width="813" height="700" alt="image" src="https://github.com/user-attachments/assets/8470c7f5-47cf-43d6-8939-809e3f23088b" />

```
data.shape
```

<img width="71" height="19" alt="image" src="https://github.com/user-attachments/assets/65e9a00a-a54b-481d-a475-7b75d28ab942" />

```
data.info()
```

<img width="348" height="385" alt="image" src="https://github.com/user-attachments/assets/ab130dc7-09bc-4d1c-9c7a-fcde187af80b" />

```
data.describe()
```

<img width="835" height="327" alt="image" src="https://github.com/user-attachments/assets/3df99174-aadc-4b84-a663-326954110496" />

```
ir=pd.read_csv('iris.csv')
ir
```

<img width="587" height="464" alt="image" src="https://github.com/user-attachments/assets/a92c73c0-a1e0-4656-8991-b13823ddfb07" />

```
ir.describe()
```

<img width="539" height="333" alt="image" src="https://github.com/user-attachments/assets/c69ee9fe-d829-489b-b68f-07099e242c63" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="609" height="524" alt="image" src="https://github.com/user-attachments/assets/8788135d-ca7a-4bde-88db-cfa7e2096470" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```

<img width="61" height="31" alt="image" src="https://github.com/user-attachments/assets/8990233d-d63a-4f7c-b798-9d5ad15a9b85" />

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

<img width="167" height="229" alt="image" src="https://github.com/user-attachments/assets/ad712f2d-944c-4023-84d9-c3aa87a5fd21" />

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

<img width="594" height="464" alt="image" src="https://github.com/user-attachments/assets/e679a36f-4c43-4c5f-af9f-c347bf706f3a" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="594" height="512" alt="image" src="https://github.com/user-attachments/assets/1ffafa9a-ba2c-4406-a933-41fcf18e2009" />

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```

```
dataset=pd.read_csv("/content/heights.csv")
dataset
```

<img width="206" height="599" alt="image" src="https://github.com/user-attachments/assets/df60eacb-b413-4e01-b0cc-0d98af68ca58" />

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```
iqr = q3-q1
iqr
```

<img width="250" height="36" alt="image" src="https://github.com/user-attachments/assets/d40fff84-491f-4331-858f-5e41eac0c2a1" />

```
low = q1 - 1.5*iqr
low
```

<img width="196" height="40" alt="image" src="https://github.com/user-attachments/assets/b97b81de-213b-4ec0-8c41-928e596fc9f1" />

```
high = q3 + 1.5*iqr
high
```

<img width="119" height="31" alt="image" src="https://github.com/user-attachments/assets/f16fc682-9da5-4ac7-9893-207cc2800669" />

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

<img width="202" height="507" alt="image" src="https://github.com/user-attachments/assets/9d4d2f3f-fc12-4c6e-9033-13feb06ae08a" />

```
z = np.abs(stats.zscore(df['height']))
z
```

<img width="148" height="639" alt="image" src="https://github.com/user-attachments/assets/40a4a101-2af6-45c5-99c0-4826abbef55e" />

```
df1 = df[z<3]
df1
```

<img width="199" height="570" alt="image" src="https://github.com/user-attachments/assets/aba375bd-c283-4ae4-9390-8875a8412a7c" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
