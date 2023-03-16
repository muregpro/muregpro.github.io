---
title: Dataset
layout: home
nav_order: 3
---

# The Dataset

The target cohort from which this data was collected inclues patients with mpMR who will undergo an MR-targeted, TRUS-guided prostate biopsy procedure to assist in the diagnosis and staging of their prostate cancer.

In this dataset are found subjects of the SmartTarget Biopsy Clinical Trial ([Hamid et al., 2019](https://doi.org/10.1016/j.eururo.2018.08.007)). 141 men who had undergone a prior (positive or negative) transrectal ultrasound biopsy and had a discrete lesion on mpMR (PI-RADs score 3–5) requiring targeted transperineal biopsy were enrolled at University College London Hospital (UCLH), London, UK; 129 underwent both biopsy strategies (visual registration and image fusion) and completed the study.

Of these 141 patients, 108 pairs had US images acquired in the transverse plane during their biopsy, and 33 in the sagittal plane. The 108 pairs which were acquired in the transverse plane, as well as their paired MRs, are included in the challenge.

The data is split into training, validation, and test sets of 65, 8, and 35 images, respectively.

**TODO: PROVIDE LINK**

## Images

The MR images were captured as specified in the [clinical trial protocols](https://clinicaltrials.gov/ct2/show/record/NCT02341677?view=record). A mixture of 1.5T and 3T MR scanners at
UCLH were used for the T2-weighted MR imaging. All MR volumes are of 120 x 128 x 128 voxels.

A range of 57–112 TRUS frames were acquired in each case by rotating a digital transperineal stepper with recorded relative angles covering the majority of the prostate gland, using a standard clinical ultrasound machine, at a depth of 65 mm and a frequency of 9.0 MHz, equipped with a bi-plane transperineal probe, at UCLH. These parasagittal slices were then used to reconstruct a 3D volume. All reconstructed TRUS volumes are of 81 x 118 x 88 voxels.

The image volumes (MR and TRUS) have been resampled to 0.8mm^3 isotropic voxel size, which is sufficent for developing and validating registration algorithms.

The TRUS volumes were centre cropped to a field of view which includes the required anatomical structures.

Training, validation and test cases consist of paired MR and TRUS volumes. Each will be accompanied by a complete prostate gland segmentation, as well as other additional anatomical landmark annotations, described in the below section.

## Labels / Annotations

Anatomical landmarks which were identified in each pair of MR and TRUS images, such as lesions, zonal structures, water-filled cysts, and calcifications, as well as prostate gland masks are provided in the training and validation data.

For the provided annotations, the prostate gland segmentations on the MR images were acquired as part of the Smart Target clinical trial protocols ([Donaldson et al., 2017](https://doi.org/10.1016/j.juro.2017.02.1016)).

The gland segmentations on the TRUS images were manually edited by two medical imaging research fellows based on automatically contoured prostate glands on original TRUS slices obtained using the method proposed in ([Ghavami et al., 2018](https://doi.org/10.1117/12.2293300)).

Besides full gland segmentations for all cases, the landmarks include apex, base, urethra, visible lesions, junctions between the gland, gland zonal separations, vas deferens and the seminal vesicles, and other patient-specific point landmarks such as calcifications and fluid-filled cysts were manually defined

{: .note }
Summary statistics, such as age, PSA, lesion volume, and Gleason scores for all patients are available in ([Hamid et al., 2019](https://doi.org/10.1016/j.eururo.2018.08.007)). 