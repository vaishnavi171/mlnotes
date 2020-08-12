---
title: "Remove Stopwords"
author: "Vaishnavi"
date: 2020-08-09
description: "-"
type: technical_note
draft: false


---


```python
import pandas as pd
```


```python
content = ['hey  i am your boss!','he is great..','nice@']
```


```python
df=pd.DataFrame(content,columns={'Sms content'})
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
      <th>Sms content</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>hey  i am your boss!</td>
    </tr>
    <tr>
      <th>1</th>
      <td>he is great..</td>
    </tr>
    <tr>
      <th>2</th>
      <td>nice@</td>
    </tr>
  </tbody>
</table>
</div>




```python
import nltk
nltk.download('stopwords')
stopwords=nltk.corpus.stopwords.words('english')
stopwords[:5]
```

    [nltk_data] Downloading package stopwords to /home/vaish/nltk_data...
    [nltk_data]   Package stopwords is already up-to-date!





    ['i', 'me', 'my', 'myself', 'we']




```python
def remove_stopwords(text):
    clean_text=[word for word in text if word not in stopwords]
    return clean_text
```


```python
df['clean_text'] = df['Sms content'].apply(lambda row : remove_stopwords(row))
df.head()
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
      <th>Sms content</th>
      <th>clean_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>hey  i am your boss!</td>
      <td>[h, e,  ,  ,  ,  , u, r,  , b, !]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>he is great..</td>
      <td>[h, e,  ,  , g, r, e, ., .]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>nice@</td>
      <td>[n, c, e, @]</td>
    </tr>
  </tbody>
</table>
</div>


