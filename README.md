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
import numpy as np
df = pd.read_csv("/content/SAMPLEIDS.csv")
df
```
<img width="819" height="590" alt="image" src="https://github.com/user-attachments/assets/4a1163ed-aba3-4a86-bff1-660b6f8d34c5" />

```
df.isnull()

```
<img width="826" height="655" alt="image" src="https://github.com/user-attachments/assets/0f374144-cb79-4e53-b86b-22c022b385e4" />

```
df.notnull()

```
<img width="676" height="656" alt="image" src="https://github.com/user-attachments/assets/324fd1d1-35ad-4657-bee3-5156d8939e6a" />

```
df.isna()
```
<img width="741" height="661" alt="image" src="https://github.com/user-attachments/assets/703035b9-63ef-4ab9-8a56-507344c69da6" />

```
df.shape
```
<img width="755" height="156" alt="image" src="https://github.com/user-attachments/assets/b3439469-df81-4d4f-a012-c180ea70c66a" />

```
df.describe()

```
<img width="1099" height="381" alt="image" src="https://github.com/user-attachments/assets/110007e8-f864-4fee-8c54-40651da27399" />

```
df.info()
```
<img width="969" height="815" alt="image" src="https://github.com/user-attachments/assets/5e8a83fd-0f1e-45ab-bb04-d7e492080bb4" />

```
df.head(3)
```
<img width="1544" height="251" alt="image" src="https://github.com/user-attachments/assets/e67dc7d7-020f-4499-8fe2-36b18457f914" />

```
df.tail(3)
```
<img width="1525" height="251" alt="image" src="https://github.com/user-attachments/assets/882e206b-d04a-4214-b8dd-2aa35a5eec5c" />

```
df.isnull().sum()

```
<img width="541" height="895" alt="image" src="https://github.com/user-attachments/assets/d756209e-5aee-4197-9bc6-3ca9ebdf7480" />

```
x=df.dropna(how='any')
x
```
<img width="1196" height="567" alt="image" src="https://github.com/user-attachments/assets/5b16e78d-1dce-4c28-beb0-1c9cb269c37d" />

```
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
<img width="1220" height="676" alt="image" src="https://github.com/user-attachments/assets/0a71038f-7ca5-42d8-b836-b55d78e4eb9a" />

```
tot=df.dropna(subset=['M1','M2','M3','M4'],how='any')
tot
```
<img width="1202" height="556" alt="image" src="https://github.com/user-attachments/assets/76dbfd92-3684-49e9-adfa-13e6c9dd5ce4" />

```
df.isnull().sum()
```
<img width="631" height="896" alt="image" src="https://github.com/user-attachments/assets/332c824b-2523-4df7-869a-8946987ff141" />

```
df.drop_duplicates(inplace=True)
```
<img width="1147" height="689" alt="image" src="https://github.com/user-attachments/assets/310301e5-a64f-40e0-8b3f-018a70fbd7dc" />

```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
<img width="1091" height="832" alt="image" src="https://github.com/user-attachments/assets/21aa8563-dcb1-4bf4-83ab-42fbb565a96b" />

```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
<img width="1196" height="831" alt="image" src="https://github.com/user-attachments/assets/389caa51-f788-45e8-91b6-8997d27b6c54" />

## Outlier Detection and Removal Using IQR

```
import pandas as pd
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
<img width="1206" height="817" alt="image" src="https://github.com/user-attachments/assets/542a217e-41ae-44fc-8829-8d009a6938c1" />

```
sns.boxplot(data=af)
```
<img width="934" height="462" alt="image" src="https://github.com/user-attachments/assets/5528b6cd-a2fd-4c84-97f9-df334b574c0a" />

```
sns.scatterplot(data=af)
```
<img width="935" height="450" alt="image" src="https://github.com/user-attachments/assets/61f4f91e-1ca3-4d44-b761-b02253ea9f9d" />

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
<img width="401" height="146" alt="image" src="https://github.com/user-attachments/assets/03a1a637-a463-497d-b404-93f1cb686650" />


```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
<img width="651" height="109" alt="image" src="https://github.com/user-attachments/assets/5a6d34b2-6a52-4d6e-b7ef-97347136ef88" />



```
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:", lower_bound)
print("Upper bound:", upper_bound)
print("Outliers:",outliers)
```
<img width="1032" height="239" alt="image" src="https://github.com/user-attachments/assets/c43b1083-7a3f-4753-8f99-71f70e601532" />
```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
<img width="566" height="701" alt="image" src="https://github.com/user-attachments/assets/8d6d14fb-f1a7-4c44-8d62-caa7d27cb9e5" />

```
af.dropna()
```
<img width="622" height="535" alt="image" src="https://github.com/user-attachments/assets/de77e0dd-74c0-477b-9482-118191f574b6" />

```
sns.boxplot(data=af)
```
<img width="1239" height="651" alt="image" src="https://github.com/user-attachments/assets/e7fa7897-8515-4771-9260-96b92bf07a9e" />

```
sns.scatterplot(data=af)
```
<img width="1171" height="641" alt="image" src="https://github.com/user-attachments/assets/bfff120d-9f95-424e-bb5c-9129469a17de" />






```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean = np.mean(data)
std = np.std(data)
print('mean of the dataset is', mean)
print('std. deviation is',std)
```
<img width="1730" height="214" alt="image" src="https://github.com/user-attachments/assets/4bd26af2-539a-4959-a49d-f42139ea7195" />

```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
<img width="531" height="636" alt="image" src="https://github.com/user-attachments/assets/74a63514-ddaf-4e34-b458-0786cfd76578" />

```
z = np.abs(stats.zscore(df['weight']))
print(df['weight'][z > 3])
```
<img width="641" height="105" alt="image" src="https://github.com/user-attachments/assets/81849156-9fe1-4c05-a4c7-4d55e23137e7" />

```
out = []

def d_o(val):
    ts = 3
    m = np.mean(val)
    sd = np.std(val)

    for i in val:
        z = (i - m) / sd
        if np.abs(z) > ts:
            out.append(i)

    return out
op=d_o(val)
op
```
<img width="564" height="100" alt="image" src="https://github.com/user-attachments/assets/47a0c72b-3fa6-4bb9-b555-651ccfd63b02" />


























# Result
The dataset was successfully cleaned by removing missing values and outliers using IQR and Z-score methods, and the cleaned data was saved successfully.
        
