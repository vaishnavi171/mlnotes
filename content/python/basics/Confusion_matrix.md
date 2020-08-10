---
title: "Confusion Matrix"
author: "Vaishnavi"
date: 2020-08-9
description: "-"
type: technical_note
draft: false


---

from sklearn.metrics import confusion_matrix


```python
var1 = "Cat"
var2 = "Ant"
var3 = "Bird"
```


```python
true = [var3, var1, var3, var3, var1, var2]
pred = [var1, var1, var3, var3, var1, var3]
```


```python
confusion_matrix(true, pred, labels=[var1, var2, var3])
```




    array([[2, 0, 0],
           [0, 0, 1],
           [1, 0, 2]])




```python

```
