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
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="1009" height="536" alt="image" src="https://github.com/user-attachments/assets/5a3d51b1-c1fa-46de-b80c-8496522859ae" />


```
df.head()
```

<img width="967" height="229" alt="image" src="https://github.com/user-attachments/assets/d9e54641-ec2e-49bf-9886-a84a04a0d6de" />

```
df.tail()
```

<img width="1000" height="243" alt="image" src="https://github.com/user-attachments/assets/69c0c115-b801-4449-aa01-eaa9f38a21aa" />


```
df.isnull()
```

<img width="868" height="308" alt="image" src="https://github.com/user-attachments/assets/85d8d9da-a4c3-429d-b2c2-da2a32ec46a1" />


```
df.notnull()
```

<img width="844" height="317" alt="image" src="https://github.com/user-attachments/assets/b5f995aa-9399-4251-9d4a-f148e114896b" />


```
df.isnull().sum()
```

<img width="220" height="294" alt="image" src="https://github.com/user-attachments/assets/91d0c121-2992-4d45-8948-3dd096922c90" />


```
df.isnull().any()
```

<img width="230" height="278" alt="image" src="https://github.com/user-attachments/assets/2963af5f-0023-49b5-b26f-5eafa7f15b73" />

```
df.dropna(axis=0)
```

<img width="1000" height="301" alt="image" src="https://github.com/user-attachments/assets/f34e8bc0-a089-4d59-869e-a25bcbe56e49" />


```
df.dropna(axis=1)
```

<img width="325" height="225" alt="image" src="https://github.com/user-attachments/assets/dd885fa0-518c-4c77-af6f-fd5be3080f20" />


```
df.fillna(5)
```

<img width="967" height="273" alt="image" src="https://github.com/user-attachments/assets/8ecb0297-61fe-4448-8939-c766fb2a35e3" />


```
df.fillna(method="ffill")
```

<img width="962" height="258" alt="image" src="https://github.com/user-attachments/assets/03edbcfa-876b-4c88-9053-2d2e54695df3" />

```
df.fillna({'Gender' : 'MALE' , 'ADDRESS' : 'KANCHIPURAM'})
```

<img width="955" height="273" alt="image" src="https://github.com/user-attachments/assets/b9030e28-0484-4251-8e96-8b0a8d39739d" />


```
ir=pd.read_csv("iris.csv")
ir
```

<img width="623" height="503" alt="image" src="https://github.com/user-attachments/assets/697f84b4-125e-46fd-b3c0-32b274ca09ef" />


```
ir.describe()
```

<img width="550" height="362" alt="image" src="https://github.com/user-attachments/assets/6a474c1a-2cf7-4076-b491-0d4028edba6b" />


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="708" height="565" alt="image" src="https://github.com/user-attachments/assets/5c779e95-0dca-42c6-ac67-dbf22ba70b6e" />


```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```

<img width="67" height="29" alt="image" src="https://github.com/user-attachments/assets/a5488415-cbe9-40d7-857f-89389db7d9ae" />


```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

<img width="326" height="117" alt="image" src="https://github.com/user-attachments/assets/d15972a9-d1fd-4a5b-8c26-9758378b3e15" />



```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```

<img width="624" height="507" alt="image" src="https://github.com/user-attachments/assets/babb5a89-f5a7-4be1-93e1-52e5cf94d38b" />


```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="735" height="574" alt="image" src="https://github.com/user-attachments/assets/56102e6a-b3c8-48a5-92ba-527558280566" />


```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['petal_length']))
z
```

<img width="462" height="269" alt="image" src="https://github.com/user-attachments/assets/1d9ed616-2ec2-48e7-ad64-52dc68f43809" />


```
df1=df[z<3]
df1
```

<img width="954" height="342" alt="image" src="https://github.com/user-attachments/assets/6bfeb6fc-9c47-48b4-9a6d-c8fba174d1f6" />



# Result

Thus, the program for data cleaning using python has executed successfully.

