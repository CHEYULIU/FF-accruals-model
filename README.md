# FF-accruals-model
## Note: Accruals and Cashflow anomalies

---  
### 1. Hypothesis
>* The first hypothesis  
>&#160;* *There is persistence in current earnings performance.*  
>&#160;* *Current earnings performance is less persistent if it is attributable to the accrual than to the cash flow.*
>* The second hypothesis
>&#160;* *Stock prices anticipate the average persistance of earnings performance.*  
>&#160;* *The earnings rooted in stock prices fail to reveal the low persistence in earnings if it is attributable to high accrual and low cash flows and high persistence in earnings if it is attributable to low accrual and high cash flows.*

 
---  
### 2. The model used
* The first equation  

![](https://latex.codecogs.com/gif.latex?Earnings_{t-1}=\alpha_{0}&plus;\alpha_{1}\times&space;Earnings_{t}&plus;\varepsilon_t)  

This equation is used to examine whether the earnings have the persistence ability.  
  
* The second equation  

![](https://latex.codecogs.com/gif.latex?Earnings_{t&plus;1}&space;=&space;\gamma_{0}&space;&plus;&space;\gamma_{1}&space;\times&space;Accruals_{t}&space;&plus;&space;\gamma_{2}&space;\times&space;Cash_{t}&plus;&space;\varepsilon_t)  

The equation breaks the ![](https://latex.codecogs.com/gif.latex?Earnings_t) in the first equation into apart, so that we can see which one of both accruals item and cash item is the attribution of the persistence of the earnings.

--- 
### Python code

```python
from EmQuantAPI import *
import pandas as pd
from pandas import Series, DataFrame
import numpy as np
import statsmodels.api as sm 
import matplotlib.pyplot as plt

earning_r = DataFrame(code, columns = ['code'])
accrual_r = DataFrame(code, columns = ['code'])
cash_r = DataFrame(code, columns = ['code'])

for n in range(1,12):
    earning_r[earning.columns[n]] = earning.iloc[:,n] / asset.iloc[:,n]
    accrual_r[accrual.columns[n]] = accrual.iloc[:,n] / asset.iloc[:,n]
    cash_r[cash.columns[n]] = cash.iloc[:,n] / asset.iloc[:,n]
    
# process the data of earnings, add each two columns after the first column into the first two columns columns by columns 
tt = earning_r
b = tt.iloc[:,1:3]
b.columns = [1,2]

for k in range(0,8):
    a = earning_r.iloc[:,(2+k):(4+k)]
    a.columns = [1,2]
    b = b.append(a,ignore_index = True)

t2 = earning_r
t3 = accrual_r
t4 = cash_r
a1 = t2.iloc[:,1]
b1 = t3.iloc[:,2]
c1 = t4.iloc[:,2]
d = pd.concat([a1,b1,c1],axis = 1, join = 'outer')
d.columns = [1,2,3]
for k in range(1,10):
    x = earning_r.iloc[:,k+1]
    y = accrual_r.iloc[:,k+2]
    z = cash_r.iloc[:,k+2]
    w = pd.concat([x,y,z], axis=1, join='outer')
    w.columns = [1,2,3]
    d = d.append(w,ignore_index = True)
    

```



