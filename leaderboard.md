---
title: Leaderboard
layout: home
nav_order: 99
---

| **Rank** | **Team Name** | **Model Name**                                 | **DSC** | **RDSC** | **HD95** | **TRE** | **RTRE** | **RTs** | **Score** | **Team Members**                            |
|----------|---------------|------------------------------------------------|---------|----------|----------|---------|----------|---------|-----------|---------------------------------------------|
| **1**    | Tiny v2       | UNet ROI Segmentation - Affine+Deformable ANTs | 0.862   | 0.885    | 3.666    | 2.450   | 1.667    | 0.687   | **0.827** | Wen Tang, Han Kang, Pengxin Yu, Chenhao Pei |
| **2**    | Tiny          | Two Stage UNet - Affine+ROI Seg -> Deformable  | 0.830   | 0.879    | 5.910    | 1.857   | 0.667    | 1.857   | **0.797** | Wen Tang, Han Kang, Pengxin Yu, Chenhao Pei |
| **3**    | MVL           | LocalNet + Focal Tversky Loss                  | 0.702   | 0.751    | 4.253    | 2.370   | 1.853    | 1.152   | **0.469** | Byungwoo Kim, Daseul Park, Changwoo Lee     |
| **4**    | Baseline      | LocalNet (Not Fully Converged)                 | 0.553   | 0.632    | 11.631   | 7.654   | 5.805    | 4.256   | **0.425** |                                             |
| **5**    | Baseline      | VoxelMorph (Not Fully Converged)               | 0.352   | 0.431    | 13.131   | 10.727  | 8.898    | 7.375   | **0.210** |                                             |
| **-**    | Smile         | Padding + ModeTv2                              | TBA     | TBA      | TBA      | TBA     | TBA      | TBA     | **TBA**   | Haiqiao Wang, Yi Wang                       |

> Note: All values are rounded to 3 decimal places.

> Note: Any submissions with additional data are noted with an * following the team name.

> Note: Team Smile result computation is in progress (submission on-time, issue with docker image).