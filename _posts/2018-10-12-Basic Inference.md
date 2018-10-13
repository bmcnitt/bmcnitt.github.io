
# Brian McNitt - EC-450 - HW2


```python

## Import Packages
import statsmodels.stats.api as sms
from scipy import stats
import numpy as np
import pandas as pd
```

    C:\Users\Brian\Anaconda3\lib\site-packages\statsmodels\compat\pandas.py:56: FutureWarning: The pandas.core.datetools module is deprecated and will be removed in a future version. Please use the pandas.tseries module instead.
      from pandas.core import datetools
    


```python
df = pd.read_excel(r'C:\Users\Brian\Documents\EC450\HW1\Data for HW1.xlsx')
```

## Question 1

#### Part A: For a 95% confidence interval, what are the lower and upper limits for SmallCaps’s average return?


```python
sms.DescrStatsW(df['SmallCaps']).tconfint_mean(alpha=.05) ## 

## prints lower and upper bound
```




    (11.962753427952046, 35.66474657204796)



#### Part B: State the competing hypotheses to determine whether SmallCaps’s average return differs from 20%.

For a 95% confidence interval, the lower bound for SmallCaps is ~11.96 and the upper bound is ~35.66.

Null Hypothesis: The SmallCap's average return is equal to 20%.

Alternative Hypthesis: The SmallCap's average return is not equal to 20%.

#### Part C: At the 5% significance level, what is the conclusion to the hypothesis test?  Does SmallCaps’s average return differ from 20%?


```python
tstat, pvalue = stats.ttest_1samp(df['SmallCaps'], 20)
print("For our t test, our t statistic is ",tstat)
print("Our P Value for a 1 tailed test is", pvalue)
```

    For our t test, our t statistic is  0.6509188841403294
    Our P Value for a 1 tailed test is 0.51891580612067
    

P Value > Alpha

.52 > .05

At the 5% significance level, we fail to reject the null hypothesis. We cannot conclude the the SmallCap's average return is not equal to 20.

#### Please See attached documents at the end for question 1: D, E

## Question 2

#### Part A: State the competing hypotheses to determine whether LargeCaps’s average return is less than 15%.

Null Hypothesis: The LargeCap's average return is greater than or equal to 15%.

Alternative Hypthesis: The LargeCap's average return is less than to 15%.

LargeCaps - 15 = diff

Given p value and t statistic from a **two-tailed test**, you would reject the null hypthesis of a *greater-than equal to test* when [p value/2 < alpha] and [t statistic > 0]. 


Given p value and t statistic from a **two-tailed test**, you would reject the null hypthesis of a *less-than equal to test* when [p value/2 < alpha] and [t statistic < 0]. 

#### Part B: At the 5% significance level, what is the conclusion to the hypothesis test?  Is LargeCaps’s average return less than 15%?


```python
tstat, pvalue = stats.ttest_1samp(df['LargeCaps'], 15)
print("For our t test, our t statistic is ",tstat)
print("Our P Value for a 1 tailed test is", pvalue / 2)
```

    For our t test, our t statistic is  -1.4121683456862542
    Our P Value for a 1 tailed test is 0.08291520435654899
    

At the 5% significance level, we fail to reject the null hypothesis. We cannot conclude the the SmallCap's average return is less than 15.

#### Please see attached documents at the end for question 2: C, D

## Question 3

#### Part A: State the competing hypotheses to determine whether SmallCaps’s average return is greater than LargeCaps’s average return

Null Hypothesis: SmallCap's average return is less than or equal to LargeCap's average return.

Alternative Hypthesis: SmallCap's average return is greater than LargeCap's Return

#### Part B: At the 5% significance level, can you conclude that SmallCaps’s average return is greater than LargeCaps’s average return?  


```python
tstat, pvalue = stats.ttest_ind(a=df['SmallCaps'], b=df['LargeCaps'], equal_var = False)
print("For our t test, our t statistic is ",tstat)
print("Our P Value for a 1 tailed test is", pvalue / 2)
```

    For our t test, our t statistic is  1.987475788999216
    Our P Value for a 1 tailed test is 0.025764722030123876
    

pvalue < Alpha

tstat > 0 

**here order matters. I assign 'a' to SmallCaps and 'b' to LargeCaps. diff = a - b **

At the 5% significance level, we reject the null hypthesis. We conclude the the SmallCap's average return is greater than the LargeCap's Average Return. 

Note that I use a Welch test because of Unequal variance and not Satterthwaite (which is default on Stata). Results are very similiar, so I stick with Welch.


## Question 4

#### Please see document attached at end for question 4
