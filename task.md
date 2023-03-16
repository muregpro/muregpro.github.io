---
title: Task Details
layout: home
nav_order: 2
---

# Task

The &micro;-RegPro Challenge aims to evaluate the performance of multimodal image registration methods between pre- and intra-operative imaging methods for surgicla and interventional tasks. The registration of MR and TRUS images assists prostate biopsy and focal therapy, arguably having
transformed prostate cancer patient care to a less invasive and more localized diagnostic, monitoring and
treatment pathway.

Using intensity-based methods, feature-based methods, or some combination of the two, participants’ should provide a function which accepts as input a:

- moving image,
- fixed image,
- moving label.

The function must also produce as output a:

- warped moving label,
- dense deformation field (DDF).

Participants are permitted to deform or transform the images in any manner (e.g. parametric or non-parametric transformation) which they should choose, however; they must provide an equivalent DDF for purposes of metric computation on the test data.

Given that this task encompasses unsupervised transform prediction, there is no ground truth transformation which may be used to compute a loss function value. However, methods based on similarity measures from the images or provided segmentations, or other approaches, may be used to drive the learning process.

{: .important }
While the test data will not have segmentation labels publicly visible, participants may derive segmentations as part of their inference process in order to assist their registration method.

Organizers will provide end-to-end weakly-supervised baseline solutions adapted from LocalNet ([Hu et al., 2019](https://doi.org/10.1016/j.media.2018.07.002)) and VoxelMorph ([Balakrishnan et al., 2019](https://doi.org/10.1109/tmi.2019.2897538)) in the Leaderboard and in a GitHub repository.