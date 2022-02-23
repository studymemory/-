WIDS 2022- EDA&Feature engineering



https://www.kaggle.com/angiengkh/wids-2022-eda-feature-engineering/notebook

**WiDS 2022-EDA&Feature engineering** 

**2.Descriptice statistics**

​                \#List all numeric attributes num = list(train.select_dtypes(include=[np.number]).columns) print(f"There are {len(num)} numerical clumns in the dataset") num              

**2.1Missing values**

​                tm - pd.DaataFrame((train.isna(.mean()*100),columns = ['Precentage of Nan values'])) tmp[tmp['Percentage of Nan values']>0] #Numnerical features train[num].describve()               

from the quick scan above,there are missing values in some 

statics #numeraical features

​                train[num].describe()              

From the data above ,we see that

- Months with lowest aveage temperatrue :Jan &Feb       This is expect4d since these are the cooler winter months
- This is expected since these are th ecooler winter months
- MOnths wiht highest avearage temperatrue JUL&Aug
- This is expected since thsesee are the hotter summer  months

b.Distribution

Firstly,we will temporaily replace thsese missing values wiht the mean sand review the distributrion in the next section before we diceide on lkogical values to use as replacements

**Distribution**

Firsty,we will tempralily repalce these missing values with the mean sand revbiew the distribuiton inthe next section before we decide on logical values to use as replacements

​             

```
   train['year_built'].min()
   train['year_built'].max()


```

```
#Train-replace nan mean
trainp['year_built'] = train{'year_built].fillna(train['year_built'].mean)
train['energy_star_rating'] = train['energy_star_rating'].gillna(train['energy_star_rating'].filllna(train['energy_star_rating'].mean())
train['direction_max_wind_speed'] = train['direction_peak_wnind_speed'] = train['direction_peank_wind_speed'].mean())
```

