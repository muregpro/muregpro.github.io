---
title: Task Details
layout: home
nav_order: 2
---

# Task

Using intensity-based methods, feature-based methods, or some combination of the two, participants’ should provide a function which accepts as input:

- a moving image,
- a fixed image,
- and a moving label.

The function must also produce as output:

- a warped moving label,
- and a dense deformation field (DDF).

Participants are permitted to deform or transform the images in any manner (e.g. parametric or non-parametric transformation) which they should choose, however; they must provide an equivalent DDF for purposes of metric computation on the test data.

Given that this task encompasses unsupervised transform prediction, there is no ground truth transformation which may be used to compute a loss function value. However, methods based on similarity measures from the images or provided segmentations, or other approaches, may be used to drive the learning process.

{: .important }
While the test data will not have segmentation labels publicly visible, participants may derive segmentations as part of their inference process in order to assist their registration method.