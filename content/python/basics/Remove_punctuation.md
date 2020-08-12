---
title: "Remove Punctuation"
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
content = ['hey!','great..','nice@']
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
      <td>hey!</td>
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
import string
string.punctuation
def remove_punctuation(text):
    new_text=''.join([char for char in text if char not in string.punctuation])
    return new_text
```


```python
df['new_sms']=df['Sms content'].apply(lambda row : remove_punctuation(row))
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
      <th>new_sms</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>hey!</td>
      <td>hey</td>
    </tr>
    <tr>
      <th>1</th>
      <td>great..</td>
      <td>great</td>
    </tr>
    <tr>
      <th>2</th>
      <td>nice@</td>
      <td>nice</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
