---
title: "Pandas Exercises"
author: "Vaishnavi"
date: 2020-08-10
description: "-"
type: technical_note
draft: false


---


```python
# 1. Loading and finding info of data

import pandas as pd

df = pd.read_excel(open('kapi.xlsx', 'rb'),sheet_name='ActorScore') 
df.info()
print("----------------")
print(df.describe())
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1286 entries, 0 to 1285
    Data columns (total 7 columns):
     #   Column            Non-Null Count  Dtype  
    ---  ------            --------------  -----  
     0   Artist Name       989 non-null    object 
     1   Year              1286 non-null   int64  
     2   Movie             283 non-null    object 
     3   Critic Score      211 non-null    float64
     4   Audience Score    211 non-null    float64
     5   Box Office Score  211 non-null    float64
     6   Updated By        0 non-null      float64
    dtypes: float64(4), int64(1), object(2)
    memory usage: 70.5+ KB
    ----------------
                  Year  Critic Score  Audience Score  Box Office Score  Updated By
    count  1286.000000    211.000000      211.000000        211.000000         0.0
    mean   2014.715397      6.739336        7.308057          6.677725         NaN
    std       3.807410      1.332137        1.432574          1.767545         NaN
    min    1990.000000      3.000000        3.000000          2.000000         NaN
    25%    2012.000000      6.000000        6.000000          5.000000         NaN
    50%    2015.000000      7.000000        8.000000          7.000000         NaN
    75%    2018.000000      8.000000        8.000000          8.000000         NaN
    max    2020.000000     10.000000       10.000000          9.000000         NaN



```python
# 2. Finding shape of data

df.shape
```




    (1286, 7)




```python
# 3. Seeing the first and last data
print(df.head(5))
print("________________________________________________________________________________________________")
print(df.tail(5))
```

      Artist Name  Year            Movie  Critic Score  Audience Score  \
    0     Dhanush  2010  Uthama puthiran           5.0             7.0   
    1     Dhanush  2011          Venghai           4.0             5.0   
    2     Dhanush  2012                3           7.0             8.0   
    3     Dhanush  2013           Maryan           8.0             7.0   
    4     Dhanush  2014              VIP           8.0             9.0   
    
       Box Office Score  Updated By  
    0               5.0         NaN  
    1               4.0         NaN  
    2               8.0         NaN  
    3               7.0         NaN  
    4               8.0         NaN  
    ________________________________________________________________________________________________
         Artist Name  Year Movie  Critic Score  Audience Score  Box Office Score  \
    1281         NaN  2016   NaN           NaN             NaN               NaN   
    1282         NaN  2017   NaN           NaN             NaN               NaN   
    1283         NaN  2018   NaN           NaN             NaN               NaN   
    1284         NaN  2019   NaN           NaN             NaN               NaN   
    1285         NaN  2020   NaN           NaN             NaN               NaN   
    
          Updated By  
    1281         NaN  
    1282         NaN  
    1283         NaN  
    1284         NaN  
    1285         NaN  



```python
# 4. Looking null values in dataset

print(df.isna().sum())
print("______________")
print(df.isna().sum().sum())
```

    Artist Name          297
    Year                   0
    Movie               1003
    Critic Score        1075
    Audience Score      1075
    Box Office Score    1075
    Updated By          1286
    dtype: int64
    ______________
    5811



```python
# 5. Dropping columns

df.drop(['Updated By'],axis=1,inplace=True)
df
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
      <th>Artist Name</th>
      <th>Year</th>
      <th>Movie</th>
      <th>Critic Score</th>
      <th>Audience Score</th>
      <th>Box Office Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Dhanush</td>
      <td>2010</td>
      <td>Uthama puthiran</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Dhanush</td>
      <td>2011</td>
      <td>Venghai</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dhanush</td>
      <td>2012</td>
      <td>3</td>
      <td>7.0</td>
      <td>8.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Dhanush</td>
      <td>2013</td>
      <td>Maryan</td>
      <td>8.0</td>
      <td>7.0</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dhanush</td>
      <td>2014</td>
      <td>VIP</td>
      <td>8.0</td>
      <td>9.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1281</th>
      <td>NaN</td>
      <td>2016</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1282</th>
      <td>NaN</td>
      <td>2017</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1283</th>
      <td>NaN</td>
      <td>2018</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1284</th>
      <td>NaN</td>
      <td>2019</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1285</th>
      <td>NaN</td>
      <td>2020</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1286 rows × 6 columns</p>
</div>




```python
# 6. Dropping null value rows

df.dropna(how='any',inplace=True)
print(df)
print(df.shape)
```

        Artist Name  Year            Movie  Critic Score  Audience Score  \
    0       Dhanush  2010  Uthama puthiran           5.0             7.0   
    1       Dhanush  2011          Venghai           4.0             5.0   
    2       Dhanush  2012                3           7.0             8.0   
    3       Dhanush  2013           Maryan           8.0             7.0   
    4       Dhanush  2014              VIP           8.0             9.0   
    ..          ...   ...              ...           ...             ...   
    218       Vivek  2020   Dharala Prabhu           6.0             5.0   
    220  Vetrimaran  2011        Aadukalam           8.0             6.0   
    222  Vetrimaran  2013      Udhayam NH4          10.0             6.0   
    223  Vetrimaran  2014       Poriyaalan           6.0             6.0   
    224  Vetrimaran  2015     Kaaka Muttai           8.0            10.0   
    
         Box Office Score  
    0                 5.0  
    1                 4.0  
    2                 8.0  
    3                 7.0  
    4                 8.0  
    ..                ...  
    218               4.0  
    220               6.0  
    222               5.0  
    223               6.0  
    224               7.0  
    
    [211 rows x 6 columns]
    (211, 6)



```python
# 7. Checking whether null values are present

df.isna().sum()
```




    Artist Name         0
    Year                0
    Movie               0
    Critic Score        0
    Audience Score      0
    Box Office Score    0
    dtype: int64




```python
# 8. Prints the datatypes of all columns

print(df.dtypes) 
```

    Artist Name          object
    Year                  int64
    Movie                object
    Critic Score        float64
    Audience Score      float64
    Box Office Score    float64
    dtype: object



```python
# 9. Finding unique actor names and year

act=list(df['Movie'].unique())
print(act)
print("_____________________________________________")
y=list(df['Year'].unique())
print(y)
```

    ['Uthama puthiran', 'Venghai', 3, 'Maryan', 'VIP', 'Anegan', 'Kodi', 'VIP 2', 'Vada chennai', 'Asuran', 'Pattas', 'VTV', 'Osthi', 'Podaa podi', 'Kanna laddu thinna aasaiya', 'Inga enna solluthu', 'Vaalu', 'Achcham enbathu madamaiyada', 'Anbanavan adangathavan asarathavan', 'Chekka chivantha vaanam', 'Vantha Rajavathan varuven', 'Kaatrin mozhi', 'Sura', 'Velayudham', 'Thuppaki', 'Thalaivaa', 'Kaththi', 'Puli', 'Theri', 'Mersal', 'Sarkar', 'Bigil', 'David', 'Ethir neechal', 'Vanakkam chennai', 'Vellailla pattadhaari', 'Vedhalam', 'Remo', 'Vivegam', 'Kolamavu kokila', 'Petta', 'Darbar', 'Manam kothi paravai', 'Kedi Billa killadi Ranga', 'Varuthapadatha valibar sangam', 'Maan karate', 'Rajini murugan', 'Velaikaran', 'Seema Raja', 'Mr local', 'Hero', 'Baana kaathadi', 'Naan E', 'Neethane En ponvasantham', 'Anjaan', 'Thanga magan', 24, 'U Turn', 'Irumbu thirai', 'Super deluxe', 'Thodari', 'Bairavaa', 'Thaana serntha koottam', 'Nadigayar thilagam', 'Seema raja', 'Saamy 2', 'Sandakozhi 2', 'Penguin', 'Enthiran', 'Vinnai thaandi varuvaaya', 'Kadal', 'Kochadaiyaan', 'I', '2.o', 'Gentle man', 'Indian', 'Mudhalvan', 'Boys', 'Anniyan', 'Sivaji', 'Nanban', '7aum arivu', 'Endrendrum Punnagai', 'Idhu Kathirvelan Kadhal', 'Iru Mugan', 'Vanamagan', 'Spyder', 'Dev', 'Kaappan', 'Dheena', 'Ramana', 'Ghajini', '7 am arivu', 'Thillalangadi', 'Engeyum Kadhal', 'Aadhi Bhagavan', 'Nimirndhu nil', 'Romeo Juliet', 'Thani Oruvan', 'Miruthan', 'Bogan', 'Tik Tik Tik', 'Adanga maru', 'Comali', 'Mankatha', 'Billa 2', 'Arrambam', 'Mass', 'Dharma Durai', 'Kadamban', 'Irumbu Thirai', 'NGK', 'Boss Engira Bhaskaran', 'Aarambam', 'Raja Rani', 'Idhu Kathirvelanin kadhal', 'Nanbenda', 'Maya', 'Dora', 'Kolamavu Kokila', 'Viswasam', 'Anjali', 'Thalapathy', 'Roja', 'Bombay', 'Alaipayuthey', 'Ayutha eluthu', 'Raavanan', 'O kadhal kanmani', 'Kaatru veliyidai', 'Naattamai', 'Avvai Shanmugi', 'Padayappa', 'Panchathanthiram', 'Aethiree', 'Saravana', 'Dasavatharam', 'Aadhavan', 'Manmadhan Ambu', 'Lingaa', 'Mudinja Ivana pudi', 'Nagaram', 'Kaavalan', 'Mambattiyaan', 'Tenali Raman', 'Eli', 'Kaththi Sandai', 'Shivalinga', 'Vinnai Thaandi Varuvayaa', 'Samar', 'Yennai Arindhaal', 'Aranmanai 2', 96, 'Irumbokottai murattu Singam', 'Kanchana', 'Kanchana 2', 'Motta Siva ketta Siva', 'Kanchana 3', 'Singam', 'Vedi', 'Muratu Kalai', 'Singam 2', 'Velaiyilla Pattathari', 'Yennai Arindhal', 'Manithan', 'Ezhumin', 'Dharala Prabhu', 'Aadukalam', 'Udhayam NH4', 'Poriyaalan', 'Kaaka Muttai']
    _____________________________________________
    [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020, 1993, 1996, 1999, 2003, 2005, 2007, 2001, 2002, 1990, 1991, 1992, 1995, 2000, 2004, 1994, 2006, 2008, 2009]



```python
# 10. Finding avg in each score of the artist

c=list(df.iloc[::,3:6])
for i in c:
    s=df.groupby(["Artist Name"])[i].sum()
    av=s/(df.groupby(["Artist Name"])[i].count())
    print(av)

```

    Artist Name
    AR Murugadoss           7.777778
    AR Rahman               7.818182
    Anirudh Ravichandran    7.545455
    Dhanush                 6.272727
    Harris Jayaraj          7.000000
    Jayam Ravi              6.545455
    KS Ravi Kumar           6.363636
    Keerthy Suresh          6.636364
    Mani Ratnam             7.090909
    Nayanthara              6.000000
    Raghava Lawrence        4.750000
    Samantha                7.454545
    Shankar                 8.300000
    Simbu                   5.181818
    Siva Karthikeyan        6.818182
    Trisha                  6.666667
    Vadivelu                5.818182
    Vetrimaran              8.000000
    Vijay                   6.500000
    Vivek                   6.454545
    Yuvan Shankar Raja      6.363636
    Name: Critic Score, dtype: float64
    Artist Name
    AR Murugadoss           8.444444
    AR Rahman               8.181818
    Anirudh Ravichandran    8.090909
    Dhanush                 7.090909
    Harris Jayaraj          7.545455
    Jayam Ravi              6.909091
    KS Ravi Kumar           7.090909
    Keerthy Suresh          7.090909
    Mani Ratnam             7.818182
    Nayanthara              6.636364
    Raghava Lawrence        6.000000
    Samantha                7.818182
    Shankar                 8.600000
    Simbu                   6.000000
    Siva Karthikeyan        7.181818
    Trisha                  7.333333
    Vadivelu                6.363636
    Vetrimaran              7.000000
    Vijay                   7.700000
    Vivek                   6.636364
    Yuvan Shankar Raja      7.272727
    Name: Audience Score, dtype: float64
    Artist Name
    AR Murugadoss           8.222222
    AR Rahman               8.636364
    Anirudh Ravichandran    8.090909
    Dhanush                 6.454545
    Harris Jayaraj          7.090909
    Jayam Ravi              6.636364
    KS Ravi Kumar           6.090909
    Keerthy Suresh          7.363636
    Mani Ratnam             6.727273
    Nayanthara              5.272727
    Raghava Lawrence        4.250000
    Samantha                7.727273
    Shankar                 8.700000
    Simbu                   4.818182
    Siva Karthikeyan        7.090909
    Trisha                  5.888889
    Vadivelu                5.090909
    Vetrimaran              6.000000
    Vijay                   7.400000
    Vivek                   5.545455
    Yuvan Shankar Raja      5.545455
    Name: Box Office Score, dtype: float64



```python
# 11. Data bucketing or data binning on box office score

op_labels = ['poor','moderate', 'good', 'excellent']
category = [0.,3.,5.,7.,10.]
df['avg boxoffice rating'] = pd.cut(df['Box Office Score'], labels=op_labels, bins=category, include_lowest=False)
df
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
      <th>Artist Name</th>
      <th>Year</th>
      <th>Movie</th>
      <th>Critic Score</th>
      <th>Audience Score</th>
      <th>Box Office Score</th>
      <th>avg boxoffice rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Dhanush</td>
      <td>2010</td>
      <td>Uthama puthiran</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Dhanush</td>
      <td>2011</td>
      <td>Venghai</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dhanush</td>
      <td>2012</td>
      <td>3</td>
      <td>7.0</td>
      <td>8.0</td>
      <td>8.0</td>
      <td>excellent</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Dhanush</td>
      <td>2013</td>
      <td>Maryan</td>
      <td>8.0</td>
      <td>7.0</td>
      <td>7.0</td>
      <td>good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dhanush</td>
      <td>2014</td>
      <td>VIP</td>
      <td>8.0</td>
      <td>9.0</td>
      <td>8.0</td>
      <td>excellent</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>218</th>
      <td>Vivek</td>
      <td>2020</td>
      <td>Dharala Prabhu</td>
      <td>6.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>220</th>
      <td>Vetrimaran</td>
      <td>2011</td>
      <td>Aadukalam</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>good</td>
    </tr>
    <tr>
      <th>222</th>
      <td>Vetrimaran</td>
      <td>2013</td>
      <td>Udhayam NH4</td>
      <td>10.0</td>
      <td>6.0</td>
      <td>5.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>223</th>
      <td>Vetrimaran</td>
      <td>2014</td>
      <td>Poriyaalan</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>good</td>
    </tr>
    <tr>
      <th>224</th>
      <td>Vetrimaran</td>
      <td>2015</td>
      <td>Kaaka Muttai</td>
      <td>8.0</td>
      <td>10.0</td>
      <td>7.0</td>
      <td>good</td>
    </tr>
  </tbody>
</table>
<p>211 rows × 7 columns</p>
</div>




```python
# 12. Renaming column names

df.rename(columns = {'Artist Name':'artistname', 'Audience Score':'audiencescore', 'Box Office Score':'boxofficescore'}, inplace = True)
df
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
      <th>artistname</th>
      <th>Year</th>
      <th>Movie</th>
      <th>Critic Score</th>
      <th>audiencescore</th>
      <th>boxofficescore</th>
      <th>avg boxoffice rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Dhanush</td>
      <td>2010</td>
      <td>Uthama puthiran</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Dhanush</td>
      <td>2011</td>
      <td>Venghai</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dhanush</td>
      <td>2012</td>
      <td>3</td>
      <td>7.0</td>
      <td>8.0</td>
      <td>8.0</td>
      <td>excellent</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Dhanush</td>
      <td>2013</td>
      <td>Maryan</td>
      <td>8.0</td>
      <td>7.0</td>
      <td>7.0</td>
      <td>good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dhanush</td>
      <td>2014</td>
      <td>VIP</td>
      <td>8.0</td>
      <td>9.0</td>
      <td>8.0</td>
      <td>excellent</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>218</th>
      <td>Vivek</td>
      <td>2020</td>
      <td>Dharala Prabhu</td>
      <td>6.0</td>
      <td>5.0</td>
      <td>4.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>220</th>
      <td>Vetrimaran</td>
      <td>2011</td>
      <td>Aadukalam</td>
      <td>8.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>good</td>
    </tr>
    <tr>
      <th>222</th>
      <td>Vetrimaran</td>
      <td>2013</td>
      <td>Udhayam NH4</td>
      <td>10.0</td>
      <td>6.0</td>
      <td>5.0</td>
      <td>moderate</td>
    </tr>
    <tr>
      <th>223</th>
      <td>Vetrimaran</td>
      <td>2014</td>
      <td>Poriyaalan</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>6.0</td>
      <td>good</td>
    </tr>
    <tr>
      <th>224</th>
      <td>Vetrimaran</td>
      <td>2015</td>
      <td>Kaaka Muttai</td>
      <td>8.0</td>
      <td>10.0</td>
      <td>7.0</td>
      <td>good</td>
    </tr>
  </tbody>
</table>
<p>211 rows × 7 columns</p>
</div>




```python
# 13. Max rating in a year with movie name

df.groupby(["Year","Movie"])["audiencescore"].max()

```




    Year  Movie         
    1990  Anjali             8.0
    1991  Thalapathy        10.0
    1992  Roja               9.0
    1993  Gentle man         8.0
    1994  Naattamai          9.0
                            ... 
    2019  Viswasam           7.0
    2020  Darbar             9.0
          Dharala Prabhu     5.0
          Pattas             8.0
          Penguin            7.0
    Name: audiencescore, Length: 173, dtype: float64




```python
# 14. Calculates mean

scores=df.iloc[:,3:] 
 
scores.mean() 
```




    Critic Score      6.739336
    audiencescore     7.308057
    boxofficescore    6.677725
    dtype: float64




```python
# 15. If condition

numbers = {'set_of_numbers': [1,2,3,4,5,6,7,8,9,10]}
df = pd.DataFrame(numbers,columns=['set_of_numbers'])

df.loc[df['set_of_numbers'] <= 4, 'equal_or_lower_than_4?'] = 'True' 
df.loc[df['set_of_numbers'] > 4, 'equal_or_lower_than_4?'] = 'False' 

print (df)
```

       set_of_numbers equal_or_lower_than_4?
    0               1                   True
    1               2                   True
    2               3                   True
    3               4                   True
    4               5                  False
    5               6                  False
    6               7                  False
    7               8                  False
    8               9                  False
    9              10                  False



```python
# 16. Strings - If condition

names = {'First_name': ['Jon','Bill','Maria','Emma']}
df = pd.DataFrame(names,columns=['First_name'])

df.loc[df['First_name'] == 'Bill', 'name_match'] = 'Match'  
df.loc[df['First_name'] != 'Bill', 'name_match'] = 'Mismatch'  
 
print (df)
```

      First_name name_match
    0        Jon   Mismatch
    1       Bill      Match
    2      Maria   Mismatch
    3       Emma   Mismatch



```python
# 17. & and | condition

df.loc[(df['First_name'] == 'Bill') | (df['First_name'] == 'Emma'), 'name_match'] = 'Match'  
df.loc[(df['First_name'] != 'Bill') & (df['First_name'] != 'Emma'), 'name_match'] = 'Mismatch'  

print (df)
```

      First_name name_match
    0        Jon   Mismatch
    1       Bill      Match
    2      Maria   Mismatch
    3       Emma      Match



```python
# 18. To set values

numbers = {'set_of_numbers': [1,2,3,4,5,6,7,8,9,10,0,0]}
df = pd.DataFrame(numbers,columns=['set_of_numbers'])
print (df)

df.loc[df['set_of_numbers'] == 0, 'set_of_numbers'] = 999
df.loc[df['set_of_numbers'] == 5, 'set_of_numbers'] = 555

print (df)
```

        set_of_numbers
    0                1
    1                2
    2                3
    3                4
    4                5
    5                6
    6                7
    7                8
    8                9
    9               10
    10               0
    11               0
        set_of_numbers
    0                1
    1                2
    2                3
    3                4
    4              555
    5                6
    6                7
    7                8
    8                9
    9               10
    10             999
    11             999



```python
# 19. Change NAN values to 0.0

import numpy as np

numbers = {'set_of_numbers': [1,2,3,4,5,6,7,8,9,10,np.nan,np.nan]}
df = pd.DataFrame(numbers,columns=['set_of_numbers'])
print (df)

df.loc[df['set_of_numbers'].isnull(), 'set_of_numbers'] = 0
print (df)
```

        set_of_numbers
    0              1.0
    1              2.0
    2              3.0
    3              4.0
    4              5.0
    5              6.0
    6              7.0
    7              8.0
    8              9.0
    9             10.0
    10             NaN
    11             NaN
        set_of_numbers
    0              1.0
    1              2.0
    2              3.0
    3              4.0
    4              5.0
    5              6.0
    6              7.0
    7              8.0
    8              9.0
    9             10.0
    10             0.0
    11             0.0



```python
# 20. Copy function

df2 = df.copy()
df2
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
      <th>set_of_numbers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>0.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 21. String methods

s = pd.Series(['A', 'B', 'C', 'Aaba', 'Baca', np.nan, 'CABA', 'dog', 'cat'])
s.str.lower()

```




    0       a
    1       b
    2       c
    3    aaba
    4    baca
    5     NaN
    6    caba
    7     dog
    8     cat
    dtype: object




```python
# 22. Merge

left = pd.DataFrame({'key': ['foo', 'bar'], 'lval': [1, 2]})
right = pd.DataFrame({'key': ['foo', 'bar'], 'rval': [4, 5]})
print("left\n",left)
print('---------------------------------------')
print("right\n",right)
print('---------------------------------------')
print(pd.merge(left, right, on='key'))
```

    left
        key  lval
    0  foo     1
    1  bar     2
    ---------------------------------------
    right
        key  rval
    0  foo     4
    1  bar     5
    ---------------------------------------
       key  lval  rval
    0  foo     1     4
    1  bar     2     5



```python
# 23. Drop duplicate

df = pd.DataFrame({'A': [1, 2, 2, 3, 4, 5, 5, 5, 6, 7, 7]})

df.drop_duplicates(subset='A') 
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
      <th>A</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
    </tr>
    <tr>
      <th>8</th>
      <td>6</td>
    </tr>
    <tr>
      <th>9</th>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 24. Append

sr1 = pd.Series(['New York', 'Chicago', 'Toronto', 'Lisbon', 'Rio']) 
  
# Create the first Index 
index_1 = ['City 1', 'City 2', 'City 3', 'City 4', 'City 5']  
  
sr1.index = index_1 
  
# Creating the second Series 
sr2 = pd.Series(['Chicage', 'Shanghai', 'Beijing', 'Jakarta', 'Seoul']) 
  
# Create the second Index 
index_2 = ['City 6', 'City 7', 'City 8', 'City 9', 'City 10']  

sr2.index = index_2 

print(sr1)  
print('---------------------------------------')
print(sr2) 
print('---------------------------------------')


# append sr2 at the end of sr1 
result = sr1.append(sr2)
print(result) 
```

    City 1    New York
    City 2     Chicago
    City 3     Toronto
    City 4      Lisbon
    City 5         Rio
    dtype: object
    ---------------------------------------
    City 6      Chicage
    City 7     Shanghai
    City 8      Beijing
    City 9      Jakarta
    City 10       Seoul
    dtype: object
    ---------------------------------------
    City 1     New York
    City 2      Chicago
    City 3      Toronto
    City 4       Lisbon
    City 5          Rio
    City 6      Chicage
    City 7     Shanghai
    City 8      Beijing
    City 9      Jakarta
    City 10       Seoul
    dtype: object



```python
# 25. Empty series NAN count

 
# min_count = 0 is the default 
pd.Series([]).sum() 
  
# When passed  min_count = 1, 
# sum of an empty series will be NaN 
pd.Series([]).sum(min_count = 1) 
```

    <ipython-input-30-e09d8f7c215b>:5: DeprecationWarning: The default dtype for empty Series will be 'object' instead of 'float64' in a future version. Specify a dtype explicitly to silence this warning.
      pd.Series([]).sum()
    <ipython-input-30-e09d8f7c215b>:9: DeprecationWarning: The default dtype for empty Series will be 'object' instead of 'float64' in a future version. Specify a dtype explicitly to silence this warning.
      pd.Series([]).sum(min_count = 1)





    nan




```python
# 26. Rank function
 
df = pd.DataFrame(data={'Animal': ['cat', 'penguin', 'dog',

'spider', 'snake'],

'Number_legs': [4, 2, 4, 8, np.nan]}) 
df['default_rank'] = df['Number_legs'].rank()

df
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
      <th>Animal</th>
      <th>Number_legs</th>
      <th>default_rank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>cat</td>
      <td>4.0</td>
      <td>2.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>penguin</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>dog</td>
      <td>4.0</td>
      <td>2.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>spider</td>
      <td>8.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>snake</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 27. Setting a column a with the sum value
 
data = {'name': ['John', 'Peter', 'Karl'], 
        'age' : [23, 42, 19]} 
  
val = pd.DataFrame(data) 
  
# sum of all salary 
val['total'] = val['age'].sum()
val
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
      <th>name</th>
      <th>age</th>
      <th>total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>23</td>
      <td>84</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Peter</td>
      <td>42</td>
      <td>84</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Karl</td>
      <td>19</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 28. Date and Time function

df = pd.DataFrame({'year': [2015, 2016],

'month': [2, 3],

'day': [4, 5]})

pd.to_datetime(df) 
```




    0   2015-02-04
    1   2016-03-05
    dtype: datetime64[ns]




```python
# 29. Slicing

df[:2]
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
      <th>year</th>
      <th>month</th>
      <th>day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2015</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016</td>
      <td>3</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 30. Concat function

s1 = pd.Series(['a', 'b'])

s2 = pd.Series(['c', 'd'])

pd.concat([s1, s2]) 
```




    0    a
    1    b
    0    c
    1    d
    dtype: object




```python

```
