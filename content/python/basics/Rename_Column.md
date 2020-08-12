---
title: "Rename Column"
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
data = ['Database team','ML team' ,'Flask team']  
df = pd.DataFrame(data, columns = ['Team'])
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
      <th>Team</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Database team</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ML team</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Flask team</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns=['Intern Team']
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
      <th>Intern Team</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Database team</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ML team</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Flask team</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.rename(columns={'Intern Team':'Team'},inplace=True)
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
      <th>Team</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Database team</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ML team</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Flask team</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
