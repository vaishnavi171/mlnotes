---
title: "Tokenisation"
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
content = ['hey boss!','great..','nice@']
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
      <td>hey boss!</td>
    </tr>
    <tr>
      <th>1</th>
      <td>great..</td>
    </tr>
    <tr>
      <th>2</th>
      <td>nice@</td>
    </tr>
  </tbody>
</table>
</div>




```python
import re
def tokenize(text):
    tokens=re.split('\W+',text)
    return tokens
```


```python
df['tokenized_text']=df['Sms content'].apply(lambda row : tokenize(row.lower()))
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
      <th>tokenized_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>hey boss!</td>
      <td>[hey, boss, ]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>great..</td>
      <td>[great, ]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>nice@</td>
      <td>[nice, ]</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
