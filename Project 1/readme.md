# Project 1: LLMs in the Health Sciences

### Overview
Researchers have initiated a challenge centered around Clinical Trial Reports (CTRs) related to breast cancer treatments to enhance how artificial intelligence interprets and utilizes medical reports. These reports are critical for medical professionals to determine the safety and efficacy of new treatments. Still, they are voluminous and complex, making it challenging for individuals to review each one thoroughly. The challenge involves the AI analyzing summaries of these reports, focusing on key aspects such as eligibility criteria, treatment specifics, trial outcomes, and observed adverse effects. Researchers crafted statements about these summaries, requiring the AI to assess whether these statements are true or false or if there's insufficient information to decide. To further test the AI's capabilities, these statements were intentionally altered by modifying numbers, changing words, or restructuring sentences. The ultimate goal is to refine the AI's consistency in understanding and ability to logically deduce information, thereby supporting medical professionals in making informed decisions about patient care. This underscores the potential of AI to significantly contribute to medical science, particularly in the realm of personalized medicine, by streamlining the interpretation and application of extensive clinical trial data.

This task is based on a collection of breast cancer CTRs (extracted from https://clinicaltrials.gov/ct2/home), statements, explanations, and labels annotated by domain expert annotators. 

### Task: Textual Entailment

For the task, we have CTRs into 4 sections:
- Eligibility criteria - A set of conditions for patients to be allowed to take part in the clinical trial
- Intervention - Information concerning the treatment type, dosage, frequency, and duration being studied.
- Results - Number of participants in the trial, outcome measures, units, and the results.
- Adverse events - These are signs and symptoms observed in patients during the clinical trial.

For this task, each CTR may contain 1-2 patient groups, called cohorts or arms. These groups may receive different treatments, or have different baseline characteristics. Below is an example CTR from the dataset 

```
{
    "Clinical Trial ID": "NCT02429427",
    "Intervention": [
        "INTERVENTION 1: ",
        "  Celecoxib",
        "  Patients in this arm will receive 400mg of celecoxib once daily. In addition, Hormone Receptor (+) patients will receive endocrine treatment according to local practice.",
        "  Celecoxib: Patients will receive 400mg of Celecoxib once daily for two years or until disease progression (if before the two years limit) or until development of unacceptable toxicities. In addition ER(+) patients will receive endocrine treatment according to local practice.",
        "INTERVENTION 2: ",
        "  Placebo",
        "  Patients in this arm will receive 2 tablets once daily. In addition Hormone Receptor (+) patients will receive endocrine treatment according to local practice.",
        "  Placebo: Two capsules once daily with food"
    ],
    "Eligibility": [
        "Inclusion Criteria:",
        "  Completely resected (greater or equal 1mm), histologically or cytologically proven unilateral breast cancer",
        "  Female greater or equal 18 years of age",
        "  If (neo) adjuvant chemotherapy received, patient must have received at least 4 cycles. Chemotherapy must be completed prior to study entry",
        "  Hormone Receptor negatives must have received prior chemotherapy",
        "  Study entry must be within any of the following timelines: 3 months of the end of definitive breast surgery OR between 3 weeks and 4 months after day 1 of the last cycle of adjuvant chemotherapy OR 6 weeks of the end of radiotherapy.",
        "  WHO performance status 0 or 1",
        "  Pre-treatment haematology and biochemistry values within acceptable local limits: Haemoglobin, white blood cell greater or equal to 3.0 x 109/l or absolute neutrophil count greater or equal to 1.51 x 109/l, Platelets greater or equal to 100 x 109/l, Serum bilirubin less than 1.5 x upper normal limit , Alkaline phosphatase less or equal to 1.5 x upper normal limit , Serum creatinine less than 1.5 x upper normal limit",
        "  Negative pregnancy test for patients with child-bearing potential",
        "  Normal baseline ECG and clinical cardiovascular assessment after completion of all (neo) adjuvant chemotherapy",
        "  No previous or current evidence for metastatic disease",
        "  Be accessible for and consent to long term follow-up",
        "  Written informed consent prior to commencement of specific protocol procedures must be obtained and documented according to the local regulatory requirements",
        "  Exclusion Criteria",
        "  Patients with node negative, T1, Grade 1 breast cancer",
        "  Unresectable, metastatic or bilateral breast cancer",
        "  Active or previous peptic ulceration or gastrointestinal bleeding in the last year",
        "  Active or previous history of inflammatory bowel disease",
        "  A past history of adverse reaction/hypersensitivity to NSAIDs, including celecoxib and salicylates, or sulphonamides",
        "  On current or planned chronic NSAIDs therapy (except low dose aspirin 100 mg four times per day or 325mg once daily).",
        "  Current or long-term use of oral corticosteroids",
        "  Known or suspected congestive heart failure (greater than New York Heart Association I) and/or coronary heart disease, previous history of myocardial infarction, uncontrolled arterial hypertension (ie BP greater than 160/90mmHg) under treatment with two anti-hypertensive drugs, rhythm abnormalities requiring permanent treatment.",
        "  Patients with diabetes controlled by diet and oral medication are eligible for the study however patients with insulin dependent diabetes are excluded",
        "  Past history of stroke/Transient ischaemic attack, symptomatic peripheral vascular disease or carotid disease",
        "  Previously entered into an adjuvant chemotherapy trial for which approval for entry into REACT has not been granted",
        "  ER receptor status unknown, Human epidermal growth factor receptor 2 or FISH positive, or Human epidermal growth factor receptor 2 status unknown",
        "  14. Hormone Receptor negative and not received (neo)adjuvant chemotherapy 15. Use of hormone replacement therapy within the last 6 weeks 16. Pregnant or lactating women or women of childbearing potential unwilling/unable to use non-hormonal contraception 17. No previous or concomitant malignancies except adequately treated squamous cell / basal cell carcinoma of the skin, in situ carcinoma of the cervix or ductal carcinoma in situ/lobular carcinoma in situ of the breast, unless there has been a disease-free interval of 10 years or more 18. Psychiatric or addictive disorders which could preclude obtaining informed consent 19. Clinical evidence of severe osteoporosis and/or history of osteoporotic fracture"
    ],
    "Results": [
        "Outcome Measurement: ",
        "  Disease Free Survival (DFS) Benefit of Two Years Adjuvant Therapy With the COX-2 Inhibitor Celecoxib Compared With Placebo in Primary Breast Cancer Patients.",
        "  From time of randomisation to the date of first event; with events contributing to the analysis defined as loco-regional and distant breast cancer recurrence, new primary breast cancer (ipsilateral or contralateral) and death without disease relapse (intercurrent death)",
        "  Time frame: Patients will be followed up to 10 years. DFS will be calculated from date of randomization until the date of first documented DFS event, this will be assessed at 2 and 5 years",
        "Results 1: ",
        "  Arm/Group Title: Celecoxib",
        "  Arm/Group Description: Patients in this arm will receive 400mg of celecoxib once daily. In addition, Hormone Receptor (+) patients will receive endocrine treatment according to local practice.",
        "  Celecoxib: Patients will receive 400mg of Celecoxib once daily for two years or until disease progression (if before the two years limit) or until development of unacceptable toxicities. In addition ER(+) patients will receive endocrine treatment according to local practice.",
        "  Overall Number of Participants Analyzed: 1763",
        "  Measure Type: Number",
        "  Unit of Measure: Percentage of participants  2 Year DFS rate: 91        (90 to 93)",
        "  5 Year DFS rate: 84        (82 to 86)",
        "Results 2: ",
        "  Arm/Group Title: Placebo",
        "  Arm/Group Description: Patients in this arm will receive 2 tablets once daily. In addition Hormone Receptor (+) patients will receive endocrine treatment according to local practice.",
        "  Placebo: Two capsules once daily with food",
        "  Overall Number of Participants Analyzed: 876",
        "  Measure Type: Number",
        "  Unit of Measure: Percentage of participants  2 Year DFS rate: 90        (87 to 92)",
        "  5 Year DFS rate: 83        (81 to 86)"
    ],
    "Adverse Events": [
        "Adverse Events 1:",
        "  Total: 148/1755 (8.43%)",
        "  Anaemia * 1/1755 (0.06%)",
        "  Neutropenia * 0/1755 (0.00%)",
        "  Thrombocytopenia * 0/1755 (0.00%)",
        "  Thrombocytopenic purpura * 1/1755 (0.06%)",
        "  Acute cardiac event * 1/1755 (0.06%)",
        "  Aortic valve incompetence * 1/1755 (0.06%)",
        "  Arrhythmia * 1/1755 (0.06%)",
        "  Atrial fibrillation * 1/1755 (0.06%)",
        "  Cardiac failure * 0/1755 (0.00%)",
        "  Cardiac tamponade * 0/1755 (0.00%)",
        "Adverse Events 2:",
        "  Total: 64/868 (7.37%)",
        "  Anaemia * 2/868 (0.23%)",
        "  Neutropenia * 2/868 (0.23%)",
        "  Thrombocytopenia * 1/868 (0.12%)",
        "  Thrombocytopenic purpura * 0/868 (0.00%)",
        "  Acute cardiac event * 0/868 (0.00%)",
        "  Aortic valve incompetence * 0/868 (0.00%)",
        "  Arrhythmia * 1/868 (0.12%)",
        "  Atrial fibrillation * 0/868 (0.00%)",
        "  Cardiac failure * 1/868 (0.12%)",
        "  Cardiac tamponade * 1/868 (0.12%)"
    ]
}
```

### Example of Tasks
Do not refer to the previous data, here are examples of contradiction and entailment

#### Example 1

| Statement | Label | Section |
| --- | --- | --- |
| The primary trial and the secondary trial both used MRI for their interventions. | Entailment | Intervention |

##### Primary Trial

INTERVENTION 1:
- Letrozole, Breast Enhancement, Safety
- Single arm of healthy postmenopausal women to have two breast MRI (baseline and post-treatment). Letrozole of 12.5 mg/day is given for three successive days just prior to the second MRI.

##### Secondary Trial

INTERVENTION 1:
- Healthy Volunteers
- Healthy women will be screened for Magnetic Resonance Imaging (MRI) contraindications, and then undergo contrast injection, and SWIFT acquisition.
- Magnetic resonance imaging: Patients and healthy volunteers will be first screened for MRI contraindications. The SWIFT MRI workflow will be performed as follows:

#### Example 2

| Statement | Label | Section |
| --- | --- | --- |
| More than 1/3 of patients in cohort 1 of the primary trial experienced an adverse event. | Contradiction | Adverse events |

##### Primary Trial
Adverse Events 1:
- **Total: 69/258 (26.74%)**
- Anaemia 3/258 (1.16%)
- Febrile neutropenia 13/258 (5.04%)
- Neutropenia 5/258 (1.94%)
- Thrombocytopenia 1/258 (0.39%)
- Atrial fibrillation 0/258 (0.00%)
- Mitral valve incompetence 1/258 (0.39%)
- Pericardial effusion 0/258 (0.00%)
- Sinus tachycardia 0/258 (0.00%)
- Abdominal pain 3/258 (1.16%)
- Abdominal pain upper 1/258 (0.39%)
- Colitis 1/258 (0.39%)

Adverse Events 2:
- Total: 64/224 (28.57%)
- Anaemia 2/224 (0.89%)
- Febrile neutropenia 4/224 (1.79%)
- Neutropenia 1/224 (0.45%)
- Thrombocytopenia 0/224 (0.00%)
- Atrial fibrillation 1/224 (0.45%)
- Mitral valve incompetence 0/224 (0.00%)
- Pericardial effusion 2/224 (0.89%)
- Sinus tachycardia 1/224 (0.45%)
- Abdominal pain 3/224 (1.34%)
- Abdominal pain upper 0/224 (0.00%)
- Colitis 0/224 (0.00%)

### Data Formatting
Read here: https://sites.google.com/view/nli4ct/semeval-2024/data-formatting?authuser=0

### Evaluation
Read here: https://sites.google.com/view/nli4ct/semeval-2024/evaluation?authuser=0

### Submission Format
Read here: https://sites.google.com/view/nli4ct/semeval-2024/submission-format?authuser=0

You will also need to provide all codes and model details, it will be later announced in Piazza.






