## Sample selection and retrieval

### 00-R_Sample_Selection.ipynb
In this notebook, we query the HISE database to identify samples from healthy subjects. We use only baseline samples from our flu vaccine treatment courses (usually labeled "Flu Year 1 Day 0") from 3 cohorts:  
UP1: Healthy pediatric samples from subjects 11-12 yr old; n = 16  
BR1: Healthy adult samples from subjects 25-35 yr old; n = 45  
BR2: Healthy adult samples from subjects 55-65 yr old; n = 47

After selection, we store the metadata for these samples in HISE for downstream steps.

### 01-Python_retrieve_cmv_bmi.ipynb
In this notebook, we retrieve CMV infection status and compute BMI for each subject based on clinical lab data stored in HISE (where available - no BMI for pediatric subjects). We then store this data in HISE for downstream steps.
