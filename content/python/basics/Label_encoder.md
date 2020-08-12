---
title: "Label Encoder"
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
content = ['ham','spam','ham']
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
      <td>ham</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
    </tr>
  </tbody>
</table>
</div>




```python
# encode
from sklearn import preprocessing
encode = preprocessing.LabelEncoder()
df['find spam'] = encode.fit_transform(df['Sms content'])
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
      <th>find spam</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ham</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>spam</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ham</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
