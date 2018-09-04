

```python
#EDA on the real estate data

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
from sklearn.preprocessing import StandardScaler
from scipy import stats
import warnings
warnings.filterwarnings('ignore')
```


```python
df_train=pd.read_csv(r"C:\Users\Ashwin Sabapathy\Documents\02. Projects\Research\Kaggle\Zillow Challenge\Input\all\train.csv")
df_train.columns
```




    Index(['Id', 'MSSubClass', 'MSZoning', 'LotFrontage', 'LotArea', 'Street',
           'Alley', 'LotShape', 'LandContour', 'Utilities', 'LotConfig',
           'LandSlope', 'Neighborhood', 'Condition1', 'Condition2', 'BldgType',
           'HouseStyle', 'OverallQual', 'OverallCond', 'YearBuilt', 'YearRemodAdd',
           'RoofStyle', 'RoofMatl', 'Exterior1st', 'Exterior2nd', 'MasVnrType',
           'MasVnrArea', 'ExterQual', 'ExterCond', 'Foundation', 'BsmtQual',
           'BsmtCond', 'BsmtExposure', 'BsmtFinType1', 'BsmtFinSF1',
           'BsmtFinType2', 'BsmtFinSF2', 'BsmtUnfSF', 'TotalBsmtSF', 'Heating',
           'HeatingQC', 'CentralAir', 'Electrical', '1stFlrSF', '2ndFlrSF',
           'LowQualFinSF', 'GrLivArea', 'BsmtFullBath', 'BsmtHalfBath', 'FullBath',
           'HalfBath', 'BedroomAbvGr', 'KitchenAbvGr', 'KitchenQual',
           'TotRmsAbvGrd', 'Functional', 'Fireplaces', 'FireplaceQu', 'GarageType',
           'GarageYrBlt', 'GarageFinish', 'GarageCars', 'GarageArea', 'GarageQual',
           'GarageCond', 'PavedDrive', 'WoodDeckSF', 'OpenPorchSF',
           'EnclosedPorch', '3SsnPorch', 'ScreenPorch', 'PoolArea', 'PoolQC',
           'Fence', 'MiscFeature', 'MiscVal', 'MoSold', 'YrSold', 'SaleType',
           'SaleCondition', 'SalePrice'],
          dtype='object')




```python
df_train['SalePrice'].describe()
```




    count      1460.000000
    mean     180921.195890
    std       79442.502883
    min       34900.000000
    25%      129975.000000
    50%      163000.000000
    75%      214000.000000
    max      755000.000000
    Name: SalePrice, dtype: float64




```python
sns.distplot(df_train['SalePrice']);
```


![png](output_3_0.png)



```python
sns.distplot(df_train['GrLivArea']);
```


![png](output_4_0.png)



```python
var="GrLivArea"
data=pd.concat([df_train[var],df_train['SalePrice']],axis=1)
data.plot.scatter(x=var,y='SalePrice',ylim=(0,800000))
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1507423de10>




![png](output_5_1.png)



```python
var="TotalBsmtSF"
data=pd.concat([df_train[var],df_train['SalePrice']],axis=1)
data.plot.scatter(x=var,y='SalePrice',ylim=(0,800000))
```




    <matplotlib.axes._subplots.AxesSubplot at 0x15074574208>




![png](output_6_1.png)



```python
var='OverallQual'
data=pd.concat([df_train[var],df_train['SalePrice']],axis=1)
fig=sns.boxplot(x=var,y="SalePrice",data=data)
```


![png](output_7_0.png)



```python
var='Fireplaces'
data=pd.concat([df_train[var],df_train['SalePrice']],axis=1)
sns.boxplot(x=var,y="SalePrice",data=data);
```


![png](output_8_0.png)



```python
var='YearBuilt'
data=pd.concat([df_train[var],df_train['SalePrice']],axis=1)
sns.boxplot(x=var,y="SalePrice",data=data);
```


![png](output_9_0.png)

