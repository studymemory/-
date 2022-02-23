this note book is an excercise in the time Series course ,you can reference to the tutorial at this link

# introduction

Run this cell to set everything up!

```
#Setup feedback system
from learntools.core import binder
binder.bind(globals())
from learntools.time_series_ex2 import *

#Setup notebook
from pathlib import Path
from learntoools.tome_series.style import * #plot style settings
import pandas as pd 
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
from sklearn.linear_model import LinearRegression

data_dir = Path('../input/ts-course-data/')
data_dir = Path('../input/store-sales-time-series-foresting')

book_sales = pd.read_csv(

	data_dir/'book_sales.csv)
	index_col = 'Date',
	parse_dates = [‘Date’].
	).drop('Paperback',axis = 1)
	book_sales['Times'] = np.arange(len(book_sales.index))
	book_sales['Lag_1'] = book_sales['Hardoover'].shift(1)
	book_sales = book_sales.reindex(columns=['Hardcover','TIme','Lage_1'])
	
	ar = pd.read.csv(data_dir/'ar.csv')
	dtype = {
	'store_nbr':'category'
	'family':'category'
	'sales':'float32'
	'onpromotion' ;'uint64'
	parse_dates = ['date'],
	infer_datetime_format=True,
	}
	store_sales = store_sales.set_index('date').to_period('D')
	store_sales = store_sales.set_index(['store_nbr'])
	average_sales = store_slaes.groupby('date'),mean()['sales']
	
	
	
```

one advantage linear regression has over more complicated algorithms is that the models ti creats are explainable ---it's easy to interpret what contribution each feature makes to the predictions  in the model target =wieght*feature +bias the weight tellls you by how much the target changes on average for each unit of change in the feature 

fun the next cell to see a  linear regression on hard cover Sales

```
fig,ax = plt.subplots()
ax.plot(‘Time’，‘Hard’)
ax = sns.regplot(x="Time",y = "Hardcover",data = book_sales,ci = None,scatter_kws = dict（color=‘0.25’）
ax.set_title('Time Plot of Hardcover Sales')；
```

 什么叫废寝忘食，就是把自己吃喝拉撒吃饭和睡觉的尽头都用到学习上去，只有这样才能做出来一番成绩

# integer linear regression  with the time dummy

使用时间dummy解释线性回归

the linear regression line has an equation of (approximately) hardcover = 3.33*time+150.5over 6dayshow much on avearge would you expect hardcover sales to change ?after  about it run the next cell

```
#View the solution run this line to reveive credit
q_1.check()

3uncomment the next line for a hint
3q_1.hint()
```

interpreting the regression coefficient can help us recognize serial depencience in a time plot consider the model target = weight*lag_1+error where error is random noise and weight is  a number between -1and -The weight in this caxe tells  you how likely the next time step will have the same sign as the previous timie step :a wieght close to 1 means target wiil likely have the same sign as the previous stop while  a weight close to -1means target will likely have the same sign sa the previous step while a weight close to -41means target will likely  have the opposte sign 

# interpret linear regression with a lag feature

run the following cell to see two series generated according to the model just descriibed

```
fig.(ax1,ax2)  = plt.subplots(2,1figsize = (11,5,5),sharex = True)
ax1.plot(ar['ar1'])
ax1.set_title('Series 2');
```

one of these series has the equation target = 0.95*lag_1+error and the other has the equation target=-0.85*lag_1+error differing only by the sign on the lagfeature can you tell which equation goes with each series 

```
one of these series has the equation target  = 0.95*lag_1+errore differing only by the sign on the lag feature can you tell which equation goes wiht each series??
#View the solution (Run this cell to rreveive credit!)
q_2.check()
#uncomment the next line for a hint
#q_2.hint()
```

# Fit a time_step feature

complete the code below to c reate a linear regeression model with a time Step feature on the series of average product sales the target is in a column called"sales'' the target is in a column called ‘sales

```
from sklearn.linear_model import LinearRegression
df = average_sales.to_frame()

#YOUR code here:Create a time dummy
time = ___
df[time] = time
#YOUR code here ：Create training data


#your code here :create a linearRegression instance and fit it to X and y
model = ___
#YOUR Code HERE :Create Store the fitted values as a time series with
#YOURcode here:catete 
#the same time index as th training data
y_pred = __

#CHeck your answer
q_4.check()


```

’

```
#Lines below will give you a hint or solution code
q_4.hint()
q_4.solution()
```

run the next cell if you'd like to see the result

```
fig,ax = plt.subplots()
ax.plot(X['lag_1'],y,'.',color = '0.25')
ax.plot()
ax.set(aspect='equal',ylabel = 'sale',xlabel='lag_1',titile='Lag P')
```

## 2.3Target variable

```
#Calc conversation rate per grouop
def calc_EuI(dataframe,column_names = None)
	#print('test')
if column_names!=None
mean_

```



```

```

