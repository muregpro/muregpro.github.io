---
title: Assessment
layout: home
nav_order: 4
---

# Assessment Criteria

## Metrics

There are 8 unique metrics used for validation in the &micro;-RegPro challenge. These are as follows:

1. Dice Similarity Coefficient (DSC): computed between the warped mask of the TRUS image and the mask of the MR image over the prostate gland boundary; averaged over all cases in the test set; in the range [0, 1] where higher indicates better registration.

2. Robustness of DSC (RDSC): DSC averaged over 68% of the highest-DSC cases in the test set.

3. Target Registration Error (TRE): registration error based on the l1 norm for anatomical landmarks which are indicated by regions identifiable in both sets of imaging, such as zonal structures, waterfilled cysts, and calcifications. A lower TRE between the TRUS and MR images indicates better registration. TRE is computed per-case, where the TRE for each case if the root-mean-square (RMS) TRE over all landmarks for that case. The mean of the TRE over all cases is then normalised to the range [0, 1] by assuming unregistered images have maximum TRE. This maximum TRE is obtained by determining the maximum individual landmark pre-registration TRE in the test set. If any submitted aggregate TREs are higher than the maximum individual landmark pre-registration TRE, the value will be clipped to 1.

4. Robustness of TRE (RTRE): TRE averaged over 68% of lowest-TRE cases in the test set.

5. Robustness of Targets (RTs): registration error based on the l1 norm for 3 lowest-error landmarks out of 5 total landmarks between the TRUS and MR images; averaged over all cases in the test set.

6. 95th Percentile Hausdorff Distance (95%HD): 95th percentile of the distances between boundary points in one set to the nearest point in the other set where sets are based on organ boundary points from TRUS and MR image segmentations; averaged over all cases in the test set; normalised to the range [0, 1] by assuming unregistered images have maximum 95%HD (if any cases submitted with worse performance than unregistered then values are clipped to the range [0, 1]).

7. Standard Deviation of log Jacobian Determinant (StDJD): computed using the jacobian over the deformation field; averaged over all cases in the test set.

8. Runtime: the amount of time it takes to compute the warped image using the algorithm; computed over all cases and then averaged to obtain the average per-case runtime.

For transparency and clarity, we note that these metrics are chosen because:

1. Dice Similarity Coefficient (DSC): DSC reflects the volumetric overlap between the registered image pair which is desirable in use cases such as intra-operative augmented reality where preoperative images (or features from these images) may be registered and overlaid onto the intraoperative images ([Bianchi et al., 2021](https://doi.org/10.1016/j.eururo.2021.06.020)); furthermore, DSC is capable of reflecting both size and localization agreement between the registered image pair which is useful for medical imaging applications such as intraoperative lesion localization using registration of intra-operative and preoperative images ([Zijdenbos et al., 1994](https://doi.org/10.1109/42.363096); [Bertels et al. 2019](https://doi.org/10.1007/978-3-030-32245-8_11)).

2. Robustness of DSC (RDSC): we chose to compute robustness metrics to ignore the effect of outliers if they are present; the value of 68% was chosen as we assumed computed metric values to be normally distributed so it then follows that approximately 68% of the errors must lie within one standard deviation of the mean error, which we deem to be sufficient to ignore the effect of outliers.

3. Target Registration Error (TRE): TRE specifically allows us to evaluate registration performance for the specific features of interest in the biomedical application ([Datteri et al. 2012](https://doi.org/10.1007/978-3-642-33454-2_18)); in this challenge, these include apex, base, urethra, visible lesions, junctions between the gland, gland zonal separations, vas deferens and the seminal vesicles, and other patient-specific point landmarks such as calcifications and fluid-filled cysts. Furthermore, TRE may also indicate physical plausibility e.g. DSC may be very high but points at the features of interest may not be properly aligned, which is why TRE supplements DSC as a metric for evaluating registration performance.

4. Robustness of TRE (RTRE): see 2.

5. Robustness of Targets (RTs): see 2; additionally, accounting for robustness over targets allows us to ignore some labelling inconsistencies in the data that may have occurred due to errors and variability in human labels.

6. 95th Percentile Hausdorff Distance (95%HD): 95%HD indicates the distance between the boundaries of the organs of interest which is important in clinical applications such as for intraoperative guidance ([Bianchi et al., 2021](https://doi.org/10.1016/j.eururo.2021.06.020)).

7. Standard Deviation of log Jacobian Determinant (StDJD): StDJD indicates the smoothness of deformation which is may indicate the physical plausibility of the deformations ([Kabus et al., 2009](https://doi.org/10.1007/978-3-642-04268-3_92); [Leow et al., 2007](https://doi.org/10.1109/TMI.2007.892646)).

8. Runtime: the runtime is important in our application of interest, which is preoperative to intraoperative registration, where ideally real-time registration would be desirable to generate any overlays of the preoperative images onto intraoperative images ([Bianchi et al., 2021](https://doi.org/10.1016/j.eururo.2021.06.020)).

## Scoring Method

Overall, these metrics permit the computation of a score by:

`Score = 0.2*(DSC) + 0.1*(RDSC) + 0.3*(1-TRE) + 0.1*(1-RTRE) + 0.1*(1-RTs) + 0.2*(1-95%HD)`

The overall scores will be in the range [0, 1] where higher is better. We will report these to 3 decimal places.

{: .warning }
The minimum score (0) will be given for any case which does not run correctly or for which metrics are unable to be calculated.

Rankings will be generated based on these scores. In the event of the same scores, we will award a higher rank based on the StDJD and award. In the case of a further tie, we will award a higher rank to the submission with a smaller runtime.

## Maximum Runtimes

While the runtime is reported as a metric, a maximum runtime will be imposed for challenge submissions. By implementing a limit, we aim to fairly encourage usability in the target application, as well as in image registration more generally, without permitting highly-optimized code or solutions to dominate the ranking system.

When we have thoroughly benchmarked the speed of our baseline deep learning methods (LocalNet ([Hu et al., 2019](https://doi.org/10.1016/j.media.2018.07.002)) and VoxelMorph ([Balakrishnan et al., 2019](https://doi.org/10.1109/tmi.2019.2897538))), we will finalize the maximum runtime and notify all currently registered users. This will occur in advance of the Test Data Evaluation period commencing. 

This maximum runtime will be the greater of:
- 30 seconds per case,
- 10 x the average case runtime of the provided deep learning baselines (e.g. if they require 1 second on average, 10 seconds would be used here).

While we cannot, at this time, explicitly provide the maximum runtime per case, the above limits will be noted publicly ahead of submissions opening. In the interim, we note below the key specifications of the system which will be used to run all validations:

- OS: Ubuntu 18.04.06 LTS
- CPU: Intel Xeon Silver 4110 @ 2.1GHz (32 Core)
- GPU: NVIDIA Quadro P5000 (16GB VRAM)
- RAM: 32GB DRAM 

