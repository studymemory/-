introduction 

```
#setup feedback system
from learntools.core import binder
binder.bind(globals())
from learntools.feature_engineering_new.ex2 import *
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
from sklearn.feature_selection import mutual_info_regression

#set matplot defaults
plt.style.use('seaborn-whitegrid')
plt.rc("figure",autolayout-True)
plt.rc(
	"axes",
	labelweight = "bold",
	labelsize ="large",
	titleweight = "bold"
	titlesize =14
	titlepad =10
	)
	
	#load data
	df = pd.read_csv("../input/fe-course-data/ames.csv")
	
	# Utility functions form Tutorial
	def make_mi_scores(X,y):
	  X = X.copy()
	  for colname in X.select-dtypes(["object","category"]):
	  X[colname],_=X[colname].factorize()
	  #all discrete features should now  have integer gtypes
	  discrete_features = [pd.api.types.is_integer_dtype(t) for t in X。dtypes]
	  mi_scores - mutual_info_regression(X,y,discrete_features,random_state=0)
	  mi_scores = pd.Series(mi_scores,name = "MI Scores",index = Z.columns)
	  mi_scores = mi_scores.sort_values(ascending = Flase)
	  return mi_scores
	  
	  def plot_mi_scores(scores):\
	  scores == scores.sort_values(ascending = True)
	  width = np.arange(len(scores))
	  ticks = list(scores.index)
	  plt.barh(width.scores)
	  plt.yticks(width,ticks)
	  plt.titile("Mutual Infomation Scores")
	  to start let's rebiew the meaning of mutual information by looking at a few feature form the Ames dataset.
	  features = ["YearBuilt",,"MoSold","ScreenPorch"]
	  sns.relplot(
	  x="value",y = "SalePrice",col = "variable",data = df.melt(id_vars = "SalaePrice",value_vars = features),facet_kws=dict(sharex = False),,
	  );
	  
```

to start let's review the meaning of mutual information by looking at a few  features from the Ames dateset

```
features = ["YearBuilt","MoSold",‘ScreenPorch’]
sns.relplot(
	x = "value",y = "SalePrice",col = "variable",data = df.mlet(id_vars = "SalePrice",value_var=features),facet_kws=kws =dict(share=False)
)
```

understand mutual information

based on the plot  which feature do you  think would  have the highest mutual information whith saleprice

```
#view the solution run this cell to receive credit
q_1.check()
```



```
X = df.copy()
y = X.pop('SalePrice')
mi_scores = make_mi_scores(X,y)
```

now examine the scores using the functions in this cell ,Look especially at top and bottom ranks

```
pirnt(mi_socres.head(20))

plt.figure(dpi=100,figsixze(9,5))
plot_mi_socres(mi_scores.head(20))
#plot——mi_scores(mi_scores.tail(20)) #uncomment to see bottom 20
```

the Bodgtype feature didn't get a very  high Mi score ,a plot  confirm that categories in BldgType  don't  do a good job of distinguishing  value in SalePrice the distributions look faiely similar in  oher words

```
sns.catplot(x="BldgType",y="SalePreice",data = df,kind="boxen");

```

Still the type of a dwelling seems like it should be importment infomation ,Investigate whether BldgType  priduces  a singificant  interaction  with either of the following 

run the following cell twice the first time with feature  = "GriLicArea"

consider appar ent temperature  measures like the heat index and the wind chill these quantities attempt to measure the perceived 感知到的。

Do you recognize the themes here ? location size , and quality you needn‘t restrict development to only these top features but you do now have a good place to start combining these top features with other related features especially those youhave not identified  as creating interactons is a good strategy for coming up with a highly infomative set of features to trian your model on

keep going 

start creating feature and learn what kinds of transformations different models are most likely to benefit from

# what is  feature engineering



```
import pandas as pd
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import cross_val_score
df = pd.read_csv('../input/fe-course-data/concrete.csv)
df.head()
```



```
X=df.copy()
y  = X.pop('compressiveStrength')

#train and score baseline model
baseline = RandomForestRegressor(criterion = "mae",random_state = 0)
baseline_score = cross_val_score(
baseline;X,y,cv=5,scoring="neg_mean_absolute_error"
)
baseline_score = -1*baseline_score.mean()

print()
```





run this cell to set everything up!

```
from learntools.core import binder
binder.bind(global())
from learntools.feature_engineering_new.ex2 import *

import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import seaborn as sns
import sklearn.feanture import mutual_info_regression

```

