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
df= pd.read_csv("/content/SAMPLEIDS ().csv")
df

<img width="1079" height="859" alt="image" src="https://github.com/user-attachments/assets/5f4057d4-352c-4acd-8a86-7cdf1a1764cb" />

df.head(3)

<img width="1093" height="191" alt="image" src="https://github.com/user-attachments/assets/49b912d1-00ef-468a-abdc-7859fa3acfb5" />

df.tail(5)

<img width="1118" height="272" alt="image" src="https://github.com/user-attachments/assets/94a51c9f-85b8-4324-b62b-9216636a1ed3" />

df.isnull()

<img width="1009" height="867" alt="image" src="https://github.com/user-attachments/assets/89c4a2a6-2e4e-4750-b7f5-5d1f969e29e6" />

df.notnull()

<img width="953" height="852" alt="image" src="https://github.com/user-attachments/assets/1c5e915e-0326-40bc-9436-b3498e942812" />

df.isnull().sum()

<img width="255" height="582" alt="image" src="https://github.com/user-attachments/assets/e0b5ddcf-beb2-4786-98c9-031f2c3a6249" />

df.isnull().any()

<img width="290" height="579" alt="image" src="https://github.com/user-attachments/assets/027ec3b9-545e-4f8f-a5e8-6a8fff94a1fe" />

df.dropna()

<img width="1158" height="583" alt="image" src="https://github.com/user-attachments/assets/82806fe9-df0c-4ce0-9090-6edd57e35175" />


df.dropna(axis=1)

<img width="484" height="862" alt="image" src="https://github.com/user-attachments/assets/7b567bf3-7de4-4c85-8fea-3634cd09850b" />

df.fillna(0)

<img width="1127" height="867" alt="image" src="https://github.com/user-attachments/assets/3d217310-2056-4fa9-bb72-adb927519720" />

df.fillna (method = 'ffill')

<img width="1079" height="865" alt="image" src="https://github.com/user-attachments/assets/79bde26c-f0b5-4227-9c86-877db277f470" />

df.fillna (method = 'bfill')

<img width="1075" height="858" alt="image" src="https://github.com/user-attachments/assets/f36b5bd2-c543-41d8-aa6b-9667f4cbd3cf" />

ir=pd.read_csv("/content/iris ().csv")
ir

<img width="770" height="521" alt="image" src="https://github.com/user-attachments/assets/c3ea1e37-4c4b-4db8-94a3-83851bbc8e13" />

ir.describe()

<img width="795" height="379" alt="image" src="https://github.com/user-attachments/assets/d69cc599-f939-4514-b1e7-8058aec2f751" />

import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)



<img width="807" height="708" alt="image" src="https://github.com/user-attachments/assets/5fd2b958-e213-40db-861e-6aac86a61ba6" />

Q1= ir.sepal_width.quantile(0.25)
Q3= ir.sepal_width.quantile(0.75)
IQR= Q3-Q1
print(IQR )

<img width="429" height="43" alt="image" src="https://github.com/user-attachments/assets/12a59f61-93e3-4e7d-9f6d-48cb6235611d" />

rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']

<img width="252" height="269" alt="image" src="https://github.com/user-attachments/assets/ff0b5966-350f-4e86-86dd-0c14224c7b46" />

rid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']

<img width="299" height="570" alt="image" src="https://github.com/user-attachments/assets/a49ed787-929d-47fd-9de6-c92ff3069c97" />

sns.boxplot(x='sepal_width',data= rid)

<img width="788" height="591" alt="image" src="https://github.com/user-attachments/assets/dc509417-e0c2-4a1f-854e-536e38b3b2e3" />

import numpy as np
import scipy.stats as stats
Z= np.abs(stats.zscore(ir['sepal_width']))
Z

<img width="840" height="680" alt="image" src="https://github.com/user-attachments/assets/e0e7e8c8-0bcd-4be3-90ae-3a1a248a9f56" />

df1 = ir[Z<3]
df1

<img width="786" height="549" alt="image" src="https://github.com/user-attachments/assets/621df047-8d44-4d8b-8aa5-8a471f9ba3d4" />


# Result

The given data has been successfully read, cleaned by handling duplicates and missing values, and saved to a new file named cleaned_data.csv.
