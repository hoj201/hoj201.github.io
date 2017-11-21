---
layout: post
title: test

---

```python
import json
```


```python
# annotations (start-frame, stop-frame)
aditya_02_start_time = 1498246828.666
aditya_02_fr_ann = [
    (99, 179),
    (226, 292),
    (346, 411),
    (449, 504),
    (813, 873),
    (919,969),
    (1020, 1084),
    (1118, 1174),
]

cvt = lambda x: {'action':'reach', 'start':x[0]+aditya_02_start_time, 'end':x[1]+aditya_02_start_time}

henry_start_time = 1498246907.700
henry_fr_ann = [
    (183, 245),
    (296, 344),
    (478, 530),
    (603, 644),
    (945, 1001),
    (1053, 1102),
    (1296, 1347),
    (1400, 1443),
]
reach_windows += [{'action':'reach', 'start':x[0]+henrt, 'end':x[1]+aditya_02_start_time} for x in aditya_02_fr_ann ]



haytham_start_time = 1498247608.066
haytham_fr_ann = [
    (133, 199),
    (323, 381),
    (495, 580),
    (788, 853),
    (924, 970),
    (1058, 1110),
    (1595, 1676),
    (1728, 1801),
    (1893,  2006),
    (2104, 2160)
]

matt_start_time = 1498247314.000
matt_fr_ann = [
    (53, 120),
    (218, 265),
    (303, 347),
    (493, 532),
    (638, 683),
    (737, 774),
]

mijael_start_time = 1498247465.766
mijael_fr_ann =[
    (170, 248),
    (343, 417),
    (662, 727),
    (790, 858),
    (1284, 1385),
    (1446, 1503),
    (1693, 1758),
    (1818, 1869)
]
```


```python
cvt = lambda x, start: {'action':'reach', 'start':x[0]+start, 'end':x[1]+start}

```




    [(119, 200), (203, 270)]




```python

```
