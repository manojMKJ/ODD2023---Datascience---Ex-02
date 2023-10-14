# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them


# Explanation:

An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

# Algorithm:
#Step1: Read the given Data.

#Step2: Get the information about the data.

#Step3: Detect the Outliers using IQR method and Z score.

#Step4: Remove the outliers.

#Step5: Plot the datas using Box Plot.


# code:

#bhp.csv:
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
#height.csv
```
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```
# Output:

#bhp.csv

![o1](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/61d94636-e5f1-4fba-ba2c-1902b63b7dd3)
![o2](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/51f8d1c2-385b-434b-a06f-9aa09ec840ad)
![o3](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/33bb4856-de97-4205-acb2-373273e00f5a)
![o4](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/29138dea-6456-4268-bbe1-3d1ec8d67aa7)
![o5](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/8f7c2f6d-9e93-4ee8-80ce-28a726bd943f)
![o6](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/98d40afb-699e-4286-b700-97b543251f72)

#height.csv

![o7](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/8ab62f65-875e-4dbf-889b-88c02ce2f29a)
![o8](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/45cdb489-c760-41f9-b85b-ebc9ef2f3354)
![o9](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/cdbd8286-6118-4d40-aafe-d4778764133b)
![o10](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/3b6c747a-534a-4480-b4aa-5f2b09fd84ee)
![o11](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/f7a0e19b-8bde-4766-ba3d-e25575cd04e4)
![o12](https://github.com/BALA291/ODD2023---Datascience---Ex-02/assets/120717501/53d5e0b2-0099-4333-9034-54861016e02a)




# Result:

Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
