# fetal-ultrasound-scan-quality-classifier
ML classifier to assess fetal ultrasound scan plane adequacy, built as a clinical AI portfolio project.
# Fetal Ultrasound Scan Plane Quality Classifier

## What this is
A machine learning project to classify whether a fetal ultrasound image captures an adequate, standard scan plane, not a diagnostic tool, purely a quality/adequacy check. Built as a hands on portfolio project to develop practical ML skills alongside clinical training.

## Why it matters
Fetal ultrasound quality depends heavily on operator skill and scan plane accuracy. An inadequate or non standard plane can lead to missed or inaccurate findings downstream, well before any diagnostic AI model is even involved. An automated adequacy check could act as a real time quality gate during scanning, flagging whether the correct view has actually been captured, rather than relying solely on operator judgement.

## Project phases
**Phase 1 (current): Static image classifier**
Train a model on the public FETAL_PLANES_DB dataset to classify standard fetal anatomical planes and assess image adequacy.

**Phase 2 (planned): Frame by frame video feedback**
Apply the trained classifier to recorded ultrasound video, frame by frame, to simulate real time feedback on whether the correct plane is being captured during a scan.

## Current status
## Current status: Phase 1 complete

Trained a binary classifier (standard plane vs. Other) using transfer learning on a pretrained ResNet18, fine tuned on FETAL_PLANES_DB.

**Results on the held out test set (5,271 images never seen during training):**
- Overall accuracy: 91% (baseline for always guessing "standard": 66%)
- AUC: 0.97
- Recall on standard planes: 0.97
- Recall on "Other" (non standard) images: 0.79

**Per plane accuracy:**
| Plane | Accuracy |
|---|---|
| Fetal brain | 99.8% |
| Maternal cervix | 98.1% |
| Fetal abdomen | 95.8% |
| Fetal thorax | 93.6% |
| Fetal femur | 92.2% |
| Other | 78.7% |

**Key limitation:** the model is noticeably weaker at catching non-standard ("Other") images than at confirming standard ones. In a real scan quality check, a missed non-standard image is the more costly error, since a bad scan would be wrongly accepted as adequate. This is the clearest next area for improvement, for example by adjusting the decision threshold or weighting training to penalize this type of mistake more heavily.

**Methodology note:** the train/validation split was done by patient, not by image, so that images from the same patient never appear in both sets. Splitting by image alone can make a model look better than it really is, since it may be partly recognizing a specific patient rather than a genuine standard plane.

## Dataset
[FETAL_PLANES_DB](https://zenodo.org/record/3904280), a public dataset of fetal ultrasound images labelled by anatomical plane, released via Zenodo.

