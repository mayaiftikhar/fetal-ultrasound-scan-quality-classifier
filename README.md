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
Phase 1 in progress: setting up data loading and initial exploration in Google Colab.

## Dataset
[FETAL_PLANES_DB](https://zenodo.org/record/3904280), a public dataset of fetal ultrasound images labelled by anatomical plane, released via Zenodo.

## Background
Built by a physician (MBBS, MRCP Part 1) transitioning into clinical AI, with no prior coding experience, as part of a structured effort to build practical, demonstrable ML skills.
