
# EC-450
# Brian McNitt
# HW- 1


```python
## import packages
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats.stats import pearsonr

%config IPCompleter.greedy=True
```


```python
df = pd.read_excel(r'C:\Users\Brian\Documents\EC450\HW1\Data for HW1.xlsx')
```


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SmallCaps</th>
      <th>LargeCaps</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>40.000000</td>
      <td>40.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>23.813750</td>
      <td>10.672500</td>
    </tr>
    <tr>
      <th>std</th>
      <td>37.055728</td>
      <td>19.381197</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-56.900000</td>
      <td>-16.420000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.197500</td>
      <td>-2.952500</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>22.140000</td>
      <td>5.560000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>32.910000</td>
      <td>23.230000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>140.300000</td>
      <td>66.300000</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.distplot(df['SmallCaps'], bins=7)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x15abcc10e80>




![png](output_4_1.png)


The distribution of small cap stocks is approxamately normal, although has a large skew for larger values. 


```python
sns.distplot(df['LargeCaps'], bins=7)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x15abcb91128>




![png](output_6_1.png)


The distribution of large cap stocks is approxemately skewed right.


```python
plt.scatter(df['LargeCaps'],df['SmallCaps'])
plt.title('Small Vs Large Cap Stock Returns')
plt.xlabel('Large')
plt.ylabel('Small')
```




    (-0.5844100985599073, 7.51002849736133e-05)




![png](output_8_1.png)


The relationship between small and large cap stock returns appears to be moderatly negative. As large cap returns tend to increase, small cap returns tend to decrease.


```python
## Returns Pearson's Correlation Coefficient and 2 tailed p value
pearsonr(df['LargeCaps'],df['SmallCaps'])
```




    (-0.5844100985599073, 7.51002849736133e-05)



The correlation coefficient for small and large cap returns is -.584. This indicates a moderate, negative relationship between the variables. 
