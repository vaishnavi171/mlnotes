---
title: "Post Stemmer"
author: "Vaishnavi"
date: 2020-08-09
description: "-"
type: technical_note
draft: false


---


```python
from nltk.stem import PorterStemmer
e_words= ["wait", "waiting", "waited", "waits"]
ps =PorterStemmer()
for w in e_words:
    rootWord=ps.stem(w)
    print(rootWord)
```

    wait
    wait
    wait
    wait



```python

```
