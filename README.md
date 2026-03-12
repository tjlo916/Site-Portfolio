# Data Analysis Portfolio

Interactive Excel Dashboard - Patient Satisfaction, Orthopedics, 2023

<img width="1023" height="770" alt="image" src="https://github.com/user-attachments/assets/acfc0922-84d7-4ddd-9cdb-3748661ad73c" />

# SQL Projects
Patient Readmission & Hospital Operations Analysis
Role: Data Analyst (SQL Focus)

**Objective: To identify patterns in patient readmissions and optimize hospital resource allocation.**

**Key Deliverables & Insights:**

**Patient Frequency Analysis:** Developed complex JOIN queries and GROUP BY aggregations to identify "High-Utilizer" patients (those with >1 admission), uncovering that X% of the patient population accounted for Y% of total hospital stays.

**Operational Efficiency:** Calculated average "Length of Stay" (LOS) using DATEDIFF and identified the top 5 medical diagnoses driving hospital volume, allowing for better-targeted staffing.

**Data Integrity & Cleaning:** Implemented COUNT(DISTINCT) audits to ensure patient identity accuracy and utilized MOD logic to segment patient populations for pilot study A/B testing.

**Workload Optimization:** Created reporting scripts using LIMIT and ORDER BY logic to monitor doctor-to-patient ratios, highlighting potential bottlenecks in care delivery.

**SQL Code**

**Count total records vs. unique individuals**  
```
SELECT  
    COUNT(*) AS total_admissions,
    COUNT(DISTINCT patient_id) AS unique_patients,
    COUNT(DISTINCT attending_doctor_id) AS staff_count
FROM admissions;
```
**Rank the top 5 reasons for admission**
```
SELECT 
    diagnosis, 
    COUNT(*) AS admission_count
FROM admissions
GROUP BY diagnosis
ORDER BY admission_count DESC
LIMIT 5;
```
**Filter by city and even-numbered IDs**
```
SELECT 
    p.first_name, 
    p.last_name, 
    p.city
FROM patients p
WHERE p.city = 'Toronto' 
  AND p.patient_id % 2 = 0;
```
  **Find patients with multiple admissions and calculate their average length of stay**
```
SELECT 
    p.patient_id,
    p.first_name,
    p.last_name,
    COUNT(a.admission_date) AS visit_count,
    AVG(DATEDIFF(a.discharge_date, a.admission_date)) AS avg_stay_days
FROM patients p
JOIN admissions a ON p.patient_id = a.patient_id
GROUP BY p.patient_id
HAVING COUNT(a.admission_date) > 1
ORDER BY visit_count DESC;
```
**Using the LIMIT logic**
**Doctor with the highest patient load**
```
SELECT d.first_name, d.last_name, COUNT(a.patient_id) as load
FROM doctors d
JOIN admissions a ON d.doctor_id = a.attending_doctor_id
GROUP BY d.doctor_id
ORDER BY load DESC
LIMIT 1;
```


