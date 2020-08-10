---
title: "Lambda Function"
author: "Vaishnavi"
date: 2020-08-9
description: "-"
type: technical_note
draft: false


---


```python
import pandas as pd
```


```python
content = ['hi','hello','how are you']
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
      <td>hi</td>
    </tr>
    <tr>
      <th>1</th>
      <td>hello</td>
    </tr>
    <tr>
      <th>2</th>
      <td>how are you</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['msg_length'] = df['Sms content'].apply(lambda x:len(x))
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
      <th>msg_length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>hi</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>hello</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>how are you</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
