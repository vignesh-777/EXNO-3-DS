## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

## ORDINAL ENCODENING
```py
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![](./out1.png)

```py
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[['ord_2']])
```
![](./out2.png)

```py
df['bo2']=e1.fit_transform(df[['ord_2']])
df
```
![](./out3.png)

```py
dfc['ord_2']=le.fit_transform(df[['ord_2']])
```
![](./out4.png)
```py
dfc
```
![](./out5.png)

```py
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df[['nom_0']]))
```
![](./out6.png)
```py
df2=pd.concat([df2,enc],axis=1)
df2
```
![](./out7.png)

```py
pd.get_dummies(df2,columns=['nom_0'])
```
![](./out8.png)

## BINARY ENCODING
```py
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![](./out9.png)

```py
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```
![](./out10.png)


## TARGET ENCODER
```py
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
cc=pd.concat([cc,new],axis=1)
print(cc)
```
![](./out11.png)

# RESULT:
The given data and perform Feature Encoding and Transformation process are performed successfully

       
