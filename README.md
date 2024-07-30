# AAA repair classification NLP model

This repository hosts the scripts used to develop a multi-tiered NLP classification model for the identification and classification of patients who have undergone abdominal aortic aneurysm (AAA) repair and if so whether it was a primary or revision repair using electronic health records (EHRs)

# Classification stages

1. Identification of vascular patients
2. Identification of patients who have under AAA repair
3. Classification of AAA repair - primary vs revision

# Types of model
There have been 4 models trained/fine-tuned:
1. ScispaCy
2. BERT-base
3. Bio-clinicalBERT
4. Ensemble model of scispaCy and Bio-clinicalBERT

# Training
The models have been trained using EHRs from MIMIC-IV clinical notes dataset - https://physionet.org/content/mimic-iv-note/2.2/

The EHRs were annotated by a Vascular Surgery Specialist Registrar/Resident. A sliding window approach was used for BERT models considering the size of EHRs and the 512 token window.

# Performance
**This is a proof of concept. The models have not been externally validated using an alternative EHR dataset so models must not be used outside of research**

