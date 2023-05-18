---
title: Home
layout: home
nav_order: 1
---

# &micro;-RegPro Challenge

**Welcome to the MR to Ultrasound Registration for Prostate (&micro;-RegPro) Challenge homepage.**

Multimodal image registration between pre-operative and intra-operative imaging enables the fusion of clinically important information during many surgical and interventional tasks. The registration of magnetic resonance imaging (MR) and transrectal ultrasound (TRUS) images assists prostate biopsy and focal therapy, arguably having transformed prostate cancer patient care to a less invasive and more localized diagnostic, monitoring and treatment pathway. Though, even with great progress having been made by the community in the past two decades, challenges remain in this application. First, paired MR and TRUS data from a sizable patient cohort are not routinely stored in clinical practice, and publicly-accessible data is scarce and low-quality. Second, annotating anatomical and pathological landmarks on both images - critical in representing corresponding locations for validation - requires expert domain knowledge and experience from multiple disciplines including urology, radiology and pathology.

In addition to its prevalence-warranted clinical importance, this application has seen a wide range of registration algorithms proposed; both feature- and intensity-based classical methods and unsupervised or segmentation-driven learning methods have been innovated with some most technically interesting approaches in the field such as biomechanical regularisation and statistical motion modelling.

The &micro;-RegPro challenge aims to provide well-curated, yet real-world clinical data, with more than a hundred paired MR and TRUS images, annotated carefully by researchers and clinicians with more than 15 years of experience working with this application. The outcome of the challenge includes one of the first multimodal imaging datasets, facilitated with expert annotations for validation, for benchmarking advancement in registration methodologies, as well as for future research in managing the most common non-skin cancer in men.

The &micro;-RegPro challenge will occur as a one-time event with a fixed challenge submission timeline at [MICCAI 2023](https://conferences.miccai.org/2023/en/), as noted in the [challenge timeline](#timeline).

**The full challenge description can be found [here](https://zenodo.org/record/7844908).**

**The challenge data is accessible [here](https://doi.org/10.5281/zenodo.7870104).**

**Sample baseline models for training and testing on the challenge data are accessible [here](https://github.com/muregpro/Baseline-Networks).**


## Timeline

| Date          | Challenge Milestone                              |
| ------------- | ------------------------------------------------ |
| Apr. 3 2023   | Registration Opens                               |
| Apr. 28 2023  | Training Data Release                            |
| Jun. 5 2023   | Validation Data Release                          |
| Jul. 3 2023   | Test Data Evaluation Begins ("Submissions Open") |
| Jul. 3 2023   | Baseline Algorithm Performance Released          |
| Jul. 17 2023  | Test Data Evaluation Closes                      |
| Jul. 24 2023  | Winners Announced and Speaker Invitations        |
| TBD @ MICCAI  | &micro;-RegPro Challenge Event @ MICCAI 2023     |

The Challenge will take place on either October 8th or 12th 2023. Location (online/in-person/hybrid) details / presentation details / event format are TBA. 

## The Task

The outcome of this challenge is the development of a method which produces an accurate alignment of the prostate gland and other anatomical structures, such as those provided as landmarks for localizing relevant anatomical and potentially pathological targets during guided prostate biopsies, and for treatment/intervention planning or decision support.

For further information on the task [input and output](task.html), challenge [dataset](data.html), and [assessment methods](assessment.html), please see their associated pages. For information about the submission process, please see [here](submission.html).

Before participating in the challenge, we ask all participants to read our [participation and data use policies, as well as our code of conduct](policies.html). Additionally, we request that participants register by e-mailing us with their intent to participate at [`muregpro@gmail.com`](mailto:muregpro@gmail.com).

## Awards

All results will be announced publicly unless errors were made in the data processing. Teams will be permitted to make multiple distinct submissions (must not be a simple change of hyperparameters). The leaderboards will be available to view publicly [here](leaderboard.html).

- The first-place and runner-up participants will receive additional certificates.
- All successful participants will receive certificates of participation.

## Discussion Board 

TBA on GitHub

## Organizers

Zachary M. C. Baum, MSc, University College London

Shaheer U. Saeed, BEng, University College London

Zhe Min, PhD, University College London

Yipeng Hu, PhD, University College London

Dean C. Barratt, PhD, University College London

Challenge Contact E-Mail: [`muregpro@gmail.com`](mailto:muregpro@gmail.com)
## Sponsors

<div align=center>
  <a href="https://www.ucl.ac.uk/interventional-surgical-sciences/wellcome-epsrc-centre-interventional-and-surgical-sciences-weiss" target="_blank"><img style="padding: 20px;" src="img/weiss.png" width=300px></a>
</div>

---

<div align=center>
  <a href="https://conferences.miccai.org/2023/" target="_blank"><img style="padding: 20px;" src="img/miccai2023-logo.png" width=200px></a>
</div>