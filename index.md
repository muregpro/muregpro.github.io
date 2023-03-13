---
title: Home
layout: home
---

# &micro;-RegPro Challenge

**Welcome to the MR to Ultrasound Registration for Prostate (&micro;-RegPro) Challenge homepage.**

Multimodal image registration between pre-operative and intra-operative imaging enables the fusion of clinically important information during many surgical and interventional tasks. The registration of magnetic resonance imaging (MR) and transrectal ultrasound (TRUS) images assists prostate biopsy and focal therapy, arguably having transformed prostate cancer patient care to a less invasive and more localized diagnostic, monitoring and treatment pathway. Though, even with great progress having been made by the community in the past two decades, challenges remain in this application. First, paired MR and TRUS data from a sizable patient cohort are not routinely stored in clinical practice, and publicly-accessible data is scarce and low-quality. Second, annotating anatomical and pathological landmarks on both images - critical in representing corresponding locations for validation - requires expert domain knowledge and experience from multiple disciplines including urology, radiology and pathology.

In addition to its prevalence-warranted clinical importance, this application has seen a wide range of registration algorithms proposed; both feature- and intensity-based classical methods and unsupervised or segmentation-driven learning methods have been innovated with some most technically interesting approaches in the field such as biomechanical regularisation and statistical motion modelling.

The &micro;-RegPro challenge aims to provide well-curated, yet real-world clinical data, with more than a hundred paired MR and TRUS images, annotated carefully by researchers and clinicians with more than 15 years of experience working with this application. The outcome of the challenge includes one of the first multimodal imaging datasets, facilitated with expert annotations for validation, for benchmarking advancement in registration methodologies, as well as for future research in managing the most common non-skin cancer in men.

The &micro;-RegPro challenge will occur as a one-time event with a fixed challenge submission timeline, as noted in the [challenge timeline](Timeline).

## Timeline

| Challenge Timeline |                                                  |
| ------------------ | ------------------------------------------------ |
| April 3 2023       | Registration Opens                               |
| April 3 2023       | Training Data Release                            |
| June 5 2023        | Validation Data Release                          |
| July 3 2023        | Test Data Evaluation Begins ("Submissions Open") |
| July 3 2023        | Baseline Algorithm Performance Released          |
| July 17 2023       | Test Data Evaluation Closes                      |
| July 24 2023       | Winners Announced and Speaker Invitations        |

## The Task

The outcome of this challenge is the development of a method which produces an accurate alignment of the prostate gland and other anatomical structures, such as those provided as landmarks for localizing relevant anatomical and potentially pathological targets during guided prostate biopsies, and for treatment/intervention planning or decision support.

### The Data

The target cohort from which this data was collected inclues patients with mpMR who will undergo an MR-targeted, TRUS-guided prostate biopsy procedure to assist in the diagnosis and staging of their prostate cancer.

In this dataset are found subjects of the SmartTarget Biopsy Clinical Trial ([Hamid et al., 2019](https://doi.org/10.1016/j.eururo.2018.08.007)). 141 men who had undergone a prior (positive or negative) transrectal ultrasound biopsy and had a discrete lesion on mpMR (PI-RADs score 3–5) requiring targeted transperineal biopsy were enrolled at University College London Hospital, London, UK; 129 underwent both biopsy strategies (visual registration and image fusion) and completed the study.

Of these 141 patients, 108 pairs had US images acquired in the transverse plane during their biopsy, and 33 in the sagittal plane. The 108 pairs which were acquired in the transverse plane, as well as their paired MRs, are included in the challenge.

The data is split into training, validation, and test sets of 65, 8, and 35 images, respectively.

The MR images were captured as specified in the [clinical trial protocols](https://clinicaltrials.gov/ct2/show/record/NCT02341677?view=record). A mixture of 1.5T and 3T MR scanners at
University College London Hospital were used for the T2-weighted MR imaging. All MR volumes are of 120 x 128 x 128 voxels.

A range of 57–112 TRUS frames were acquired in each case by rotating a digital transperineal stepper (D&K Technologies GmbH, Barum, Germany) with recorded relative angles covering the majority of the prostate gland, using a standard clinical ultrasound machine (HI-VISION Preirus, Hitachi Medical Systems Europe), at a depth of 65 mm and a frequency of 9.0 MHz, equipped with a bi-plane (C41L47RP) transperineal probe, at University College London Hospital. These parasagittal slices were then used to reconstruct a 3D volume. All reconstructed TRUS volumes are of 81 x 118 x 88 voxels.

The image volumes (MR and TRUS) have been resampled to 0.8mm^3 isotropic voxel size, which is sufficent for developing and validating registration algorithms.

The TRUS volumes were centre cropped to a field of view which includes the required anatomical structures.

Training, validation and test cases consist of paired MR and TRUS volumes. Each will be accompanied by a complete prostate gland segmentation, as well as other additional anatomical landmark annotations, described in the below section.

### Labels / Annotations

Anatomical landmarks which were identified in each pair of MR and TRUS images, such as lesions, zonal structures, water-filled cysts, and calcifications, as well as prostate gland masks are provided in the training and validation data.

For the provided annotations, the prostate gland segmentations on the MR images were acquired as part of the Smart Target clinical trial protocols ([Donaldson et al., 2017](https://doi.org/10.1016/j.juro.2017.02.1016)).

The gland segmentations on the TRUS images were manually edited by two medical imaging research fellows based on automatically contoured prostate glands on original TRUS slices obtained using the method proposed in ([Ghavami et al., 2018](https://doi.org/10.1117/12.2293300)).

Besides full gland segmentations for all cases, the landmarks include apex, base, urethra, visible lesions, junctions between the gland, gland zonal separations, vas deferens and the seminal vesicles, and other patient-specific point landmarks such as calcifications and fluid-filled cysts were manually defined

Of note, summary statistics, such as age, PSA, lesion volume, and Gleason scores for all patients are available in ([Hamid et al., 2019](https://doi.org/10.1016/j.eururo.2018.08.007)). 

### Methods

Using intensity-based methods, feature-based methods, or some combination of the two, participants’ should provide a function which accepts:

Input: a moving image, a fixed image, and a moving label.

And produces:

Output: a warped moving label, and a dense deformation field (DDF).

Participants are permitted to deform or transform the images in any manner (e.g. parametric or non-parametric transformation) which they should choose, however; they must provide an equivalent DDF for purposes of metric computation on the test data.

Given that this task encompasses unsupervised transform prediction, there is no ground truth transformation which may be used to compute a loss function value. However, methods based on similarity measures from the images or provided segmentations, or other approaches, may be used to drive the learning process.

*Note: While the test data will not have segmentation labels publicly visible, participants may derive segmentations as part of their inference process in order to assist their registration method.*

### Assessment Criteria

There are 8 unique metrics used for validation in the &micro;-RegPro challenge. These are as follows:

1. Dice Similarity Coefficient (DSC): computed between the warped mask of the TRUS image and the mask of the MR image over the prostate gland boundary; averaged over all cases in the test set; in the range [0, 1] where higher indicates better registration.

2. Robustness of DSC (RDSC): DSC averaged over 68% of the highest-DSC cases in the test set.

3. Target Registration Error (TRE): registration error based on the l1 norm for anatomical landmarks which are indicated by regions identifiable in both sets of imaging, such as zonal structures, waterfilled cysts, and calcifications. A lower TRE between the TRUS and MR images indicates better registration. TRE is computed per-case, where the TRE for each case if the root-mean-square (RMS) TRE over all landmarks for that case. The mean of the TRE over all cases is then normalised to the range [0, 1] by assuming unregistered images have maximum TRE. This maximum TRE is obtained by determining the maximum individual landmark pre-registration TRE in the test set. If any submitted aggregate TREs are higher than the maximum individual landmark pre-registration TRE, the value will be clipped to 1.

4. Robustness of TRE (RTRE): TRE averaged over 68% of lowest-TRE cases in the test set.

5. Robustness of Targets (RTs): registration error based on the l1 norm for 3 lowest-error landmarks out of 5 total landmarks between the TRUS and MR images; averaged over all cases in the test set.

6. 95th Percentile Hausdorff Distance (95%HD): 95th percentile of the distances between boundary points in one set to the nearest point in the other set where sets are based on organ boundary points from TRUS and MR image segmentations; averaged over all cases in the test set; normalised to the range [0, 1] by assuming unregistered images have maximum 95%HD (if any cases submitted with worse performance than unregistered then values are clipped to the range [0, 1]).

7. Standard Deviation of log Jacobian Determinant (StDJD): computed using the jacobian over the deformation field; averaged over all cases in the test set.

8. Runtime: the amount of time it takes to compute the warped image using the algorithm; computed over all cases and then averaged to obtain the average per-case runtime.

For transparencry and clarity, we note that these metrics are chosen because:

1. Dice Similarity Coefficient (DSC): DSC reflects the volumetric overlap between the registered image pair which is desirable in use cases such as intra-operative augmented reality where preoperative images (or features from these images) may be registered and overlaid onto the intraoperative images ([Bianchi et al., 2021](https://doi.org/10.1016/j.eururo.2021.06.020)); furthermore, DSC is capable of reflecting both size and localization agreement between the registered image pair which is useful for medical imaging applications such as intraoperative lesion localization using registration of intra-operative and preoperative images ([Zijdenbos et al., 1994](https://doi.org/10.1109/42.363096); [Bertels et al. 2019](https://doi.org/10.1007/978-3-030-32245-8_11)).

2. Robustness of DSC (RDSC): we chose to compute robustness metrics to ignore the effect of outliers if they are present; the value of 68% was chosen as we assumed computed metric values to be normally distributed so it then follows that approximately 68% of the errors must lie within one standard deviation of the mean error, which we deem to be sufficient to ignore the effect of outliers.

3. Target Registration Error (TRE): TRE specifically allows us to evaluate registration performance for the specific features of interest in the biomedical application ([Datteri et al. 2012](https://doi.org/10.1007/978-3-642-33454-2_18)); in this challenge, these include apex, base, urethra, visible lesions, junctions between the gland, gland zonal separations, vas deferens and the seminal vesicles, and other patient-specific point landmarks such as calcifications and fluid-filled cysts. Furthermore, TRE may also indicate physical plausibility e.g. DSC may be very high but points at the features of interest may not be properly aligned, which is why TRE supplements DSC as a metric for evaluating registration performance.

4. Robustness of TRE (RTRE): see 2.

5. Robustness of Targets (RTs): see 2; additionally, accounting for robustness over targets allows us to ignore some labelling inconsistencies in the data that may have occurred due to errors and variability in human labels.

6. 95th Percentile Hausdorff Distance (95%HD): 95%HD indicates the distance between the boundaries of the organs of interest which is important in clinical applications such as for intraoperative guidance ([Bianchi et al., 2021](https://doi.org/10.1016/j.eururo.2021.06.020)).

7. Standard Deviation of log Jacobian Determinant (StDJD): StDJD indicates the smoothness of deformation which is may indicate the physical plausibility of the deformations ([Kabus et al., 2009](https://doi.org/10.1007/978-3-642-04268-3_92); [Leow et al., 2007](https://doi.org/10.1109/TMI.2007.892646)).

8. Runtime: the runtime is important in our application of interest, which is preoperative to intraoperative registration, where ideally real-time registration would be desirable to generate any overlays of the preoperative images onto intraoperative images ([Bianchi et al., 2021](https://doi.org/10.1016/j.eururo.2021.06.020)).

Overall, these metrics permit the computation of a score by:

`Score = 0.2*(DSC) + 0.1*(RDSC) + 0.3*(1-TRE) + 0.1*(1-RTRE) + 0.1*(1-RTs) + 0.2*(1-95%HD)`

The overall scores will be in the range [0, 1] where higher is better. We will report these to 3 decimal places.

Rankings will be generated based on these scores. In the event of the same scores, we will award a higher rank based on the StDJD and award. In the case of a further tie, we will award a higher rank to the submission with a smaller runtime.

*Note: The minimum score (0) will be given for any case which does not run correctly or for which metrics are unable to be calculated.*

## Discussion Board 

TBA on GitHub
## Awards

All results will be announced publicly unless errors were made in the data processing. Teams will be permitted to make multiple distinct submissions (must not be a simple change of hyperparameters). The leaderboards will be available to view publicly [here].

- The first-place and runner-up participants will receive additional certificates.
- All successful participants will receive certificates of participation.

## Participation Policy

- Submitted methods must be fully automatic.
- Public and Private Data are permitted, however their use must be disclosed by participants.
- Organizers may participate and listed in leaderboards, but not eligble for awards

### Data usage agreement

The data is made available under [CC BY NC SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). The challenge data shall be available for use exclusively for research purposes, due to the restrictions from [original ethics approval and patient consent](https://clinicaltrials.gov/ct2/show/record/NCT02341677?view=record). 

The training and validation data will remain publicly available after the completion of the challenge. The training and validation data may be used within the research remit of this challenge, and in further research-related publications. The training and validation data is not to be used commercially. However, if the desired use case is unclear, the organizers ask that those accessing the data refrain from further use or distribution outside of this challenge.

## Submission Process

Participants must Dockerize their trained network/algorithm/method and will submit these, via file-sharing link (e.g. OneDrive, Dropbox) to the organizers through e-mail to [`muregpro@gmail.com`](mailto:muregpro@gmail.com). 

The e-mail submission must contain:

- Team name;
- Team affiliation and country (e.g. University College London, United Kingdom).
- Full name(s) of all team members;
- Brief description of method (100 characters maximum);
- File-sharing link to Dockerized algorithm;

Receipt of all submissions will be acknowledged by e-mail, and submissions will be evaluated and posted to the leaderboard within 2 working days of receipt.

The evaluation code to evaluate the registration algorithms will be made publicly available at the same time that that section of the challenge becomes available to enter (July 3 2023).

Participating teams' are encouraged, but not required, to make their code publicly available. We will provide links to any available source code on the challenge website.

## Organizers

Zachary M. C. Baum, MSc, University College London

Shaheer U. Saeed, BEng, University College London

Zhe Min, PhD, University College London

Yipeng Hu, PhD, University College London

Dean C. Barratt, PhD, University College London

## Publications / Publication Policy

We aim to submit a publication which summarizes the dataset and results from the challenge. Members of the top five teams will be invited as co-authors.

We encourage participants to submit papers of their contributions and/or any novel methodologies for medical image registration. However, until the challenge paper is published (submission to arXiv is considered sufficient), participants should not refer to challenge-specific data or results. Participants must cite the challenge paper and dataset once they are available.

## Sponsors

TBC