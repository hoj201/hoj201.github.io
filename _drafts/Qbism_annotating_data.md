---
layout: post
title: The Quantum Mechanics of Amazon Mechanical Turk
tag: math, physics, data science
---

I needed to make an algorithm for detecting walking. To do this we need annotated data. That means watching many videos and labelling windows of time (e.g. subject started walking in frame 36... subject stopped walking in frame 110).

The standard route to annotation is Amazon Mechanical Turk (heretofore referred to as AMT).  Why is it called "Mechanical Turk" you ask?  The reason is because....

Anyway, back to our regularly scheduled program. I needed to annotate a bunch of videos with people walking (and not walking). To use AMT, I needed to cast the annotation task as something like an image classification task.  So I could chop the videos up into one second chunks, and for each second I could ask the question "Is the person in the video walking?"

If I do this for every second of every video I would get walk annotations with 1 second resolution. Of course, why stop there?  Why not have higher resolution.  There are roughly 30 frames of video every second. Why not give just a single frame of video, and achieve the maximal resolution? The reason is accuracy.  There are lots of motions that given just a single frame may appear to be walking, but which are not (e.g. taking a single step to adjust posture is not walking), additionally, there are moments of walking that may appear to be just standing upright (like when the left leg swings forward and is momentarily aligned with the the right leg).

Conversely, you would obviously not want to split the video into 10 second chunks. If a 10 second chunk of video is labelled as "walking", it not clear which of the 10 seconds the annotator is referring to. It's as if "walking" has a natural resolution, an h-bar, and there is some sort of Heisenberg Uncertainty principle that says
$$
  \Delta t \cdot S \geq \hbar
$$
where $S = p_{+} \log(p_{+}) + p_{-} \log(p_{-})$ is the entropy of the probability with which we think the subject is or is not walking in the given video-clip.

I can't make this so precise, but I managed to come up with a simple model on the subway ride home.

## Walking in the frequency domain
There is a difference between walking and dancing.  There is a difference between walking and sitting. Finally, there is a difference between walking and adjusting your posture while just standing around.

The biggest difference is that walking produces rhythmic signals in the accellerometer in a very narrow region of the frequency domain. It's not inconceivable that a reasonable walk detector would entail applying a Fourier transform the the signal to obtain $\hat{\psi}(p)$
and we would classify the person as walking with a confidence of
$$
  p_{walk} = \int E_{+}(p) \hat{\psi}(p) dp
$$
where $E_{+}$ is a function that is large around the frequencies in which walking tends to be active, and is low everywhere else.

We could even construct a walk operator
$$
  H = E_{+} \otimes E_{+}
$$

## The AMT Uncertainty Principle

From the Fourier Uncertainty Principle we known that

$$
  \sigma(p) \Delta t \geq 1
$$

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
