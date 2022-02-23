EXERCISE:MUTAL INFORMATION





```
LOAD data

df= pd.read.csv(''../input/fe-course-data/ames.csv'')

#utility function form tutorial

def make_mi_score(X.y):

 x=x.copy

for colname in X.select_dtypes(["object","category"])
X[colname] in X.[colname].factorize()
#All discrete features should now have integer dtypes
discrete_feature = [pd.api.types.is_integer_dtype(t) for t in X.dtypes]
miscores = mutual_info_regeression(X,y,discrete_features = discrete_feature,random_state=0)
mi_scores = mtual_info_regerssion(X,y,discrete_features=discrete_features,random_state=0)
mi_socres=pd.Series(mi_scores,nam    ="MI Score",index = X.column)
mi_scores = mi_scores.soret_value(ascending+False)
return mi_scores

def plot_mi_socres(scores)
 scores = scores.soret_values(ascending+True)
return mi_scores
def plot_mi_score(scores)
 scores=scores.sort_values9ascending=true)
 def plot_mi_scores(scores)
 scores = socres.core_values(ascending=True）
 width = np.arange(len(scores))
 ticks= list(scores.index)
 plt.barh(widdth,scores)
 plt.yticks(width,ticks)
 plt.title("Mutual Information Socres)\
 
 features = {"YearBuilt","MoSold","ScreenPorch"}
 sns.relplot(
 	x="value",y="SalePrice",col = "varialble",data = df.melt(id_vars=“Sale
 )
 
```

understand mutual information

based on the plots ,which feature do you think would have the highest mutual information with SalePrice?

```
#View the solution (run this cell to receieve credit)
q_1.check()
```

The Ames dataset has seventy_eight feature --alot to work with all at once!Formation with SalePrice?

```
# View the solution (Run this cell to reveive credit!)
q_1.check()
```

the ames dataset has sevetny_eight feature ---alot to work with all at once !Fortunnately you can identify the feature with the most poential

use the make_mi_scores function (introducd in the tutuorial) to compute mutual information socre for the ames features



```
X = df.copy()
y = X.pop('SalePrice')
mi_scores = make_mi_socres(X,y)

```

now  examine the scores using the functions in the cell ,look especially at top and bottom ranks

print (mi_scores.head(20))

#pirnt(mi_scores.tail(20)) #uncomment to see bootom 20

plt.figure(dpi = 100,figsize=-(8,5))

plot_mi_sores(mi_scores.head(20))

#plot_mi_scores.tail(20)#uncommment to see bottom 20



## examine mi scores

DOthe scores seem reasonable ?Do the hight scoring features represent thins you'd thinkmost people would in a home?Do you notice any themes in what thy describe?

```
Do the scores seem reasonable?
#View the solution (run this cell to reveive credit)!
q_2.check()




```

in this step you'll incestigate possible  interaction effects for the BldgType feature.this feature descreibes the broad structrue fo the dwelling in five categories

```
sns.cateplot(x="BldgType",y = "SalePrice",data=df,kind = "boxen");
```



still the type of  a dwellding seems like it should be important information investigate whether BldgType produces significant interaction with either of the following :

run the following cell twice the first time with feature =  ”GrriLicaArea“ and the next time with featuture  = "MOSOld"



```
#YOUR CODEHERE
feature = 'GrlicArea'
sns.lmplot(
    x = featuture,y = "SalePrice",hue = "BVldgType",col = "BldgType"
    data = df,scatter-kws = {'edgecloler':}
    
)
```

''





