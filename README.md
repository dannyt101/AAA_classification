# AAA repair classification NLP model

This repository hosts the scripts used to develop a multi-tiered NLP classification model for the identification and classification of patients who have undergone abdominal aortic aneurysm (AAA) repair during a hospital admission and if so whether it was a primary or revision repair using unstructured electronic health records (EHRs)

# Classification stages

Task 1 - Identification of vascular-related admission
Task 2 - Identification of patients who have undergone a AAA repair during their admission
Task 3 - Classification of AAA repair - primary vs revision

# Types of model
There have been 4 models trained/fine-tuned:
1. ScispaCy
2. BERT-base
3. Bio-clinicalBERT
4. Ensemble model of scispaCy and Bio-clinicalBERT

# Training
The models have been trained using EHRs from MIMIC-IV clinical notes dataset - https://physionet.org/content/mimic-iv-note/2.2/

The EHRs were annotated by a Vascular Surgery Specialist Registrar/Resident. A sliding window approach was used for BERT models considering the size of EHRs and the 512-token limit.

# Performance
**This is a proof of concept. The models have not been externally validated using an alternative EHR dataset so models must not be used outside of research**

| Model             | Accuracy | Precision (Vascular) | Recall (Vascular) | F1-Score (Vascular) | Precision (Non-Vascular) | Recall (Non-Vascular) | F1-Score (Non-Vascular) |
|-------------------|----------|----------------------|-------------------|---------------------|--------------------------|-----------------------|-------------------------|
| BERT-base         | 0.92     | 0.74                 | 0.79              | 0.76                | 0.96                     | 0.95                  | 0.95                    |
| Bio-clinicalBERT  | 0.94     | 0.88                 | 0.70              | 0.78                | 0.95                     | 0.98                  | 0.96                    |
| ScispaCy          | 0.97     | 0.92                 | 0.89              | 0.90                | 0.98                     | 0.98                  | 0.98                    |
| Ensemble          | 0.97     | 0.93                 | 0.89              | 0.91                | 0.98                     | 0.99                  | 0.98                    |

**Table 1**: Table showing classification report for Task 1 – classifying admissions for patients with acute vascular conditions with a threshold of 0.5.

| Model             | Accuracy | Precision (AAA) | Recall (AAA) | F1-Score (AAA) | Precision (Non-AAA) | Recall (Non-AAA) | F1-Score (Non-AAA) |
|-------------------|----------|-----------------|--------------|----------------|---------------------|------------------|--------------------|
| BERT-base         | 0.98     | 0.99            | 0.97         | 0.98           | 0.98                | 0.99             | 0.99               |
| Bio-clinicalBERT  | 0.99     | 0.99            | 0.98         | 0.98           | 0.99                | 0.99             | 0.99               |
| ScispaCy          | 0.99     | 0.97            | 1.00         | 0.99           | 1.00                | 0.98             | 0.99               |
| Ensemble          | 0.99     | 0.97            | 1.00         | 0.99           | 1.00                | 0.98             | 0.99               |

**Table 2**: Table showing classification report for stage 2 – classifying admissions for patients who underwent AAA repair during their admission with a threshold of 0.5.

| Model             | Accuracy | Precision (Non-AAA) | Recall (Non-AAA) | F1-Score (Non-AAA) | AUROC (Non-AAA) | Precision (Primary AAA repair) | Recall (Primary AAA repair) | F1-Score (Primary AAA repair) | AUROC (Primary AAA repair) | Precision (Revision AAA repair) | Recall (Revision AAA repair) | F1-Score (Revision AAA repair) | AUROC (Revision AAA repair) |
|-------------------|----------|---------------------|------------------|--------------------|----------------|---------------------------------|-----------------------------|-------------------------------|----------------------------|--------------------------------|------------------------------|--------------------------------|-----------------------------|
| BERT-base         | 0.89     | 0.96                | 0.92             | 0.94               | 1.00           | 0.84                            | 0.94                        | 0.88                          | 0.98                       | 0.86                           | 0.73                         | 0.79                           | 0.96                        |
| Bio-clinicalBERT  | 0.92     | 0.97                | 0.92             | 0.95               | 0.99           | 0.88                            | 0.94                        | 0.91                          | 0.98                       | 0.89                           | 0.86                         | 0.87                           | 0.96                        |
| ScispaCy          | 0.96     | 1.00                | 0.97             | 0.99               | 0.99           | 0.97                            | 0.94                        | 0.96                          | 1.00                       | 0.84                           | 0.96                         | 0.90                           | 0.99                        |
| Ensemble          | 0.97     | 1.00                | 0.97             | 0.99               | 1.00           | 0.97                            | 0.96                        | 0.96                          | 0.99                       | 0.87                           | 0.96                         | 0.92                           | 0.99                        |

**Table 3**: Table showing classification report for Task 3 – classifying type of AAA repair undertaken during admission with a threshold of 0.5.





