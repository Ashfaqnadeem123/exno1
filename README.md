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
 import pandas as pd
df=pd.read_csv("/content/Data_set (1).csv")
df         
df.info()
![image](https://github.com/user-attachments/assets/92052fc2-8fef-465c-a9dc-a8fbb46be0ec)
df.describe()
![image](https://github.com/user-attachments/assets/d1264ab6-5065-4666-af79-93dbd0e4c896)
df.head(10)
![image](https://github.com/user-attachments/assets/642f169d-1028-4b10-8ffd-e78ccc8a9e23)
df.tail(5)
![image](https://github.com/user-attachments/assets/ac76b36c-4ed8-49ac-86cc-0d3a7e95875d)
df.isnull()
![image](https://github.com/user-attachments/assets/545c13e2-9824-45f1-97db-61d14bd8bc3c)
df.notnull()
![image](https://github.com/user-attachments/assets/a0debb7f-3ae1-4fb0-88bc-b3ab5281328e)
df.dropna(axis=0)
![image](https://github.com/user-attachments/assets/e2eda5e8-a233-4226-9210-8aa3ffdeb841)
df.dropna(axis=1)
![image](https://github.com/user-attachments/assets/6c7d0b3b-a148-4b1a-9a4a-762427731e3d)
dfs=df[df['num_episodes']>20]
dfs
![image](https://github.com/user-attachments/assets/7afb429c-901e-4980-b9e4-960c9cfb1014)
dfs=df[df['show_name'].str.startswith(('A','F')) & (df['num_episodes']>25)]
dfs
![image](https://github.com/user-attachments/assets/8879aee9-9412-40f0-8bc0-ce3a4e6980cc)
df.iloc[:3]
![image](https://github.com/user-attachments/assets/e79ebc76-8af1-49cb-a3b1-40b606b5a346)
df.iloc[:4]
![image](https://github.com/user-attachments/assets/24168d9f-2622-4b24-a044-2187fc50bbe8)
df.iloc[[1,3,5],[1,3,5]]
![image](https://github.com/user-attachments/assets/1172145d-f4f8-4a7a-98dc-7a7066d4989b)
df.fillna('sample value')
![image](https://github.com/user-attachments/assets/4b9594e1-576c-4514-96bc-31dfb4066576)
ffill=df.fillna(method='ffill')
ffill
![image](https://github.com/user-attachments/assets/2dbefab6-d489-4c01-85c6-ac82cf6527aa)
bfill=df.fillna(method='bfill')
bfill
![image](https://github.com/user-attachments/assets/119d86e6-7089-41b3-ae52-eb5e0b3a8775)
df1=df.fillna(df['num_episodes'].mean())
df
![image](https://github.com/user-attachments/assets/885e019e-e3e2-46ea-9092-04d23a328dd5)
fmean=df['lifetime_popularity_rank'].fillna(value=df['lifetime_popularity_rank'].mean())
fmean
![image](https://github.com/user-attachments/assets/fd64bf15-d660-41fb-8bfb-09e30bb6ca44)
df=pd.read_csv("/SAMPLEIDS.csv")
df
![image](https://github.com/user-attachments/assets/9e74a544-245d-4392-be33-258523a45b80)
df.shape
![image](https://github.com/user-attachments/assets/57d3ced3-eb62-49dd-a29d-102ed6985d80)
df.describe()
![image](https://github.com/user-attachments/assets/b4849526-6988-417d-8ebf-a0ffdfda6eb2)
df.info()
![image](https://github.com/user-attachments/assets/b0de20c8-44ef-498f-acc6-41e0023945cd)
df['GENDER'].value_counts()
![image](https://github.com/user-attachments/assets/6c2122c1-1268-4642-adaa-9d86c960a953)
df.dropna(how='any').shape
![image](https://github.com/user-attachments/assets/d8f1048a-7019-46b6-be4e-6f8e24add170)
x1=df.dropna(how='any')
x1
![image](https://github.com/user-attachments/assets/e5284c62-3071-4de8-8c14-211946c88490)
res=df.dropna(subset=['M1','M2','M3','M4'],how='any')
res
![image](https://github.com/user-attachments/assets/16634ee8-551c-42ce-b6ba-5178bd6aa9f6)
mean = df.TOTAL.mean()
mean
![image](https://github.com/user-attachments/assets/1b9005af-c096-4d54-9773-01e60608c58f)
mn = df.TOTAL.fillna(mean,inplace=False)
mn
![image](https://github.com/user-attachments/assets/aa87af4b-b569-4540-be5e-3ced5c11b0af)
df.isnull()
![image](https://github.com/user-attachments/assets/bcc14f80-1156-46a7-ae4f-bf78a906bbe2)
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
![image](https://github.com/user-attachments/assets/54295110-d984-4753-a6a3-3b6bb5e275cd)
sns.heatmap(df.isnull(),yticklabels=True,annot=True)
![image](https://github.com/user-attachments/assets/ab71eddc-2c2b-425d-b201-b497157622e1)
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
![image](https://github.com/user-attachments/assets/432f03dc-176a-433a-ad54-3c4715c6c927)
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
df=pd.read_csv("/content/heights.csv")
df
![image](https://github.com/user-attachments/assets/a785c178-fa45-4cec-aedc-64bbdc4a778f)
sns.boxplot(data=df)
![image](https://github.com/user-attachments/assets/5e4f69f7-3aba-451b-a4be-5722741a88a7)
sns.scatterplot(data=df)
![image](https://github.com/user-attachments/assets/07f448e8-1880-462a-8ba3-8ea7d32bca76)
max=df['height'].quantile(0.75)
min=df['height'].quantile(0.25)
iqr=max-min
iqr
![image](https://github.com/user-attachments/assets/971101e6-c821-4b9c-bfbd-0f2a9106e212)
sns.boxplot(data=df)
![image](https://github.com/user-attachments/assets/761624a0-5399-4aa5-a17c-3d5d34ba62bd)
sns.scatterplot(data=df)
![image](https://github.com/user-attachments/assets/3987f72e-be30-4463-98b4-8ba25e9456c2)
low=min-1.5*iqr
low
![image](https://github.com/user-attachments/assets/739f1bb8-c787-4f02-bbab-b6e51f54bea8)
high=max+1.5*iqr
high
![image](https://github.com/user-attachments/assets/aca23201-61ab-45a9-9c1f-cd7255213884)
qm=df[((df['height']>=low)&(df['height']<=high))]
qm
![image](https://github.com/user-attachments/assets/c281beb2-3550-4d6a-a319-92615a3249f4)
sns.boxplot(data=qm)
![image](https://github.com/user-attachments/assets/18ddc5b2-a15d-4434-80cd-74f5fd79a48c)
sns.scatterplot(data=qm)
![image](https://github.com/user-attachments/assets/8dc0ec88-dae5-40e1-b3ce-c18b382583c2)
data={'weight':[12,11,13,14,16]}
df=pd.DataFrame(data)
df
![image](https://github.com/user-attachments/assets/b8de2b91-8a95-4035-a57d-f5321a23dac9)
z=np.abs(stats.zscore(df))
z
![image](https://github.com/user-attachments/assets/a96e0424-c1d2-4d7c-826c-73c38a4d6143)
z=np.abs(stats.zscore(qm['height']))
z
![image](https://github.com/user-attachments/assets/94827bf0-91d0-4bad-8a98-19816a1e7f88)
df1=qm[z<3]
df1
![image](https://github.com/user-attachments/assets/1cbbbf6f-a02d-4f04-89f0-8576c36aa0af)
val=qm['height']
val
![image](https://github.com/user-attachments/assets/ac3b9608-6992-42c1-9c53-9c08a7f93a38)
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
![image](https://github.com/user-attachments/assets/49d2097e-3272-496c-aa45-87784978e92a)

# Result

