
# 📊 Axon Healthcare Dashboard — Power BI Project

🧠 Project Objective

To analyze patient demographics, doctor performance, treatment outcomes, and hospital operational metrics using Power BI.
This dashboard transforms healthcare data into actionable insights for improving patient care, optimizing clinical efficiency, and enhancing decision-making across the healthcare ecosystem.

## 📁 Dataset Details

The healthcare dataset was initially cleaned and structured in Excel, then imported into MySQL for relational storage, and finally connected to Power BI for building the interactive dashboard.


* Patients → PatientID, Name, Gender, Age, Address, BloodType, Insurance, EmergencyContacts, MedicalHistory, ChronicConditions, Allergies, AgeCategory, Demographics

* Visits → VisitID, PatientID, DoctorID, VisitDate, Diagnosis, DiagnosisCode, VisitStatus, VisitType, ReasonForVisit, FollowUpRequired, PrescribedMedications

* Treatments → TreatmentID, VisitID, TreatmentName, TreatmentType, TreatmentDescription, Cost, MedicationPrescribed, Dosage, Outcome, Status

* LabResults → LabResultID, VisitID, TestName, TestDate, Units, ReferenceRange, TestResult (Normal/Abnormal), Comments

* Doctors → DoctorID, DoctorName, Specialty, Experience, ContactInfo, HospitalClinicAffiliation

Data Connection: The cleaned dataset stored in MySQL was connected to Power BI Desktop using the built-in MySQL database connector, enabling direct querying and automated data refresh.
## ⚙️Data Modeling
| **From**            | **To**              | **Relationship** |
| ------------------- | ------------------- | ---------------- |
| Patients[PatientID] | Visits[PatientID]   | One-to-many      |
| Doctors[DoctorID]   | Visits[DoctorID]    | One-to-many      |
| Visits[VisitID]     | Treatments[VisitID] | One-to-many      |
| Visits[VisitID]     | LabResults[VisitID] | One-to-many      |

All tables cleaned and transformed in Power Query before loading 
to the data model. 


## 📈 Key Performance Indicators (KPIs)

| **KPI**                    | **Value** | **Description**                                            |
| -------------------------- | --------- | ---------------------------------------------------------- |
| **Total Patients**         | 10K      | Total number of patients in the healthcare system          |
| **Follow-Up Required**     | 49.4%        | Number of patients who require follow-up visits            |
| **Total Doctors**          | 1000        | Total number of active doctors                             |
| **Average Patient Age**    | 48.94        | Average age across all patients                            |
| **Average Treatment Cost** | 524.75        | Avg. cost of all treatments performed                      |
| **Total Revenue**          | 30.65M        | Total revenue generated from treatments                    |
| **Total Treatments**       | 10K      | Total number of treatments administered                    |
| **Doctor Success Rate**    | 33%      | Percentage of treatments completed successfully by doctors |
| **Doctor Workload**        | 10       | Number of visits/treatments handled per doctor             |
| **Treatment Success Rate** | 3K        | Overall success rate of treatments                         |

Each KPI is displayed as a Card visual at the top of the dashboard.



## 📊 Patients Dashboard — Visuals Overview

## 1️⃣ Age-Wise Diagnosis Distribution
Type: Clustered Column Chart

* X-axis → Diagnosis (Migraine, Hypertension, Asthma, Healthy, Diabetes)

* Y-axis → Patient Count

* Legend → Age Category (Adults, Elderly, Teenagers)

* Colors:

    * Adults: Cyan (#00D9FF)

    * Elderly: Light Green (#06FFA5)

    * Teenagers: Yellow (#FFD60A)

* Title: "Age-Wise Diagnosis Distribution"

Purpose:
Shows how common each diagnosis is across different age groups to identify clinical patterns.
## 2️⃣ Monthly Patient Visit Analysis
Type: Line Chart

* X-axis → Month (Jan–Dec)

* Y-axis → Number of Patient Visits

* Line Color: Orange (#FF6B35), 2.5px

* Markers: Enabled

* Title: "Monthly Patient Visit Analysis"

Purpose:
Tracks monthly patient footfall and seasonal visit variations.
## 3️⃣ Gender Distribution
Type: Donut Chart

* Values → Count of Patients

* Legend → Gender (Male, Female, Other)

* Colors:

    * Male — Yellow (#FFD60A)

    * Female — Purple (#9D4EDD)

    * Other — Orange (#FF6B35)

* Center Label: Percentage distribution

* Title: "Gender Distribution"

Purpose:
Breaks down patient demographics by gender.
## 4️⃣ Normal vs Abnormal Lab Results
Type: Pie / Donut Chart

* Values → Test Result Count

* Legend → Normal, Abnormal

* Colors:

    * Normal — Light Blue (#3A7DFF)

    * Abnormal — Dark Blue (#1A4CC5)

* Labels: Percentages displayed (50.4% vs 49.6%)

* Title: "Normal vs Abnormal"

Purpose:
Shows overall lab test result distribution indicating diagnostic trends.
## 👨‍⚕️ Doctors Dashboard — Visuals Overview
## 1️⃣ Top 10 Doctors by Success Rate
Type: Combo Chart (Column + Line)

* Columns → Successful Treatments (Blue #00D9FF)

* Line → Doctor Success Rate (Dark Blue #1A4CC5)

* X-axis → Doctor Names (Top 10)

* Y-axis → Treatment Count (left), Success Rate % (right)

* Markers: Enabled

* Title: "Top 10 Doctors by Success Rate"

Purpose:
Highlights best-performing doctors and clinical efficiency.
## 2️⃣ Department-wise Revenue & Cost Analysis
Type: Combo Chart (Column + Line)

* Columns → Total Revenue (Pink #FF99CC)

* Line → Total Cost (Purple #6A00A8)

* X-axis → Department (General Medicine, Pediatrics, Cardiology, Neurology, Orthopedics)

* Y-axis: Revenue (left) & Cost (right)

* Labels: Revenue and cost shown on bars and line points

* Title: "Department-wise Revenue & Cost Analysis"

Purpose:
Supports financial analysis of department performance.
## 3️⃣ Doctors by Specialty

Type: Donut Chart

* Values → Number of Doctors

* Legend → Specialty (Cardiology, Pediatrics, Orthopedics, etc.)

* Colors: Multi-color palette

* Labels: Count + Percentage

* Examples:

    * Cardiology: 212 (21.2%)

    * Pediatrics: 208 (20.8%)

    * Others segmented similarly

* Title: "Doctors by Specialty"

Purpose:
Shows staffing distribution and specialization mix.
## 🎯 Interactive Bookmark Navigation

## 1️⃣ Dashboard View Bookmarks
| **Button**   | **Action**                                                  | **Design Style**                                                       |
| ------------ | ----------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Patients** | Switches the report to show only Patients Dashboard visuals | Black background (#000000), White text (#FFFFFF), Cyan hover (#00D9FF) |
| **Doctors**  | Switches the report to show only Doctors Dashboard visuals  | Black background (#000000), White text (#FFFFFF), Cyan hover (#00D9FF) |

## 2️⃣ Gender Filter Bookmarks
| **Button** | **Action**                                            | **Design Style**                                     |
| ---------- | ----------------------------------------------------- | ---------------------------------------------------- |
| **Male**   | Filters entire dashboard to show only male patients   | Dark gray default (#333333), Cyan on hover (#00D9FF) |
| **Female** | Filters entire dashboard to show only female patients | Dark gray default (#333333), Cyan on hover (#00D9FF) |

## 💡 Key DAX Measures

* Total Patients = DISTINCTCOUNT(Patients[PatientID])

* Avg Patient Age = AVERAGE(Patients[Age])
* Follow Up Rate =DIVIDE(
    COUNTROWS(FILTER(Patients, Patients[FollowUp] = "Yes")),
    DISTINCTCOUNT(Patients[PatientID]))
* Avg Treatment Cost = AVERAGE(Treatments[TreatmentCost])
* Total Revenue = SUM(Treatments[AmountPaid])
* Monthly Visits = COUNTROWS(PatientVisits)
* Male Count = CALCULATE(COUNTROWS(Patients), Patients[Gender] = "Male")

  Female Count = CALCULATE(COUNTROWS(Patients), Patients[Gender] = "Female")

   Other Gender Count = CALCULATE(COUNTROWS(Patients), Patients[Gender] = "Other")
* Normal Results = CALCULATE(COUNTROWS(Tests), Tests[Result] = "Normal")

  Abnormal Results = CALCULATE(COUNTROWS(Tests), Tests[Result] = "Abnormal")
* Total Doctors = DISTINCTCOUNT(Doctors[DoctorID])
* Doctor Success Rate = DIVIDE(
    SUM(Doctors[SuccessfulTreatments]),
    SUM(Doctors[TotalTreatments]))
* Doctor Workload = DIVIDE(
    SUM(Doctors[TotalTreatments]),
    DISTINCTCOUNT(Doctors[DoctorID]))
* Total Treatments = SUM(Treatments[TotalCount])
* Successful Treatments = SUM(Treatments[SuccessCount])

## 💡 Business Insights
* Patient base remains strong at 10K, with balanced gender distribution and an average age of 48.94.

* Total revenue of $30.65M reflects solid financial performance across treatment categories.

* Follow-up rate at 49.84% highlights a major opportunity to improve patient engagement and continuity of care.

* Monthly visits show seasonal activity peaks, supporting targeted resource planning.

* Diagnostic outcomes show a near 50-50 split between normal and abnormal results, indicating balanced clinical load.

* Medical team consists of 1K doctors with evenly distributed specialties across all departments.

* Doctor success rate of 33% signals potential for performance enhancement and best-practice learning.

* Department revenues are strong, though high operational costs indicate opportunities for efficiency improvements.

## 🧰 Tools & Technologies Used
* MySQL → Database creation, relational modeling, and synthetic data generation

* SQL (MySQL Queries) → Building realistic business scenarios through custom query logic

* Excel → Data cleaning, preprocessing, and structured dataset preparation

* Power BI Desktop → Dashboard design, data modeling, and interactive visualization

* DAX (Data Analysis Expressions) → Custom KPIs, business metrics, and analytical calculations

* Power Query (M Language) → Data transformation, shaping, and automated data preparation

* MySQL Connector → Direct connection between Power BI and MySQL database

* Power BI Service → Publishing, sharing, report refresh, and collaboration

* Bookmarks & Buttons → Interactive report navigation and dynamic filtering experiences

* Star Schema Modeling → Optimized data model for performance and scalability

* GitHub → Portfolio hosting, version control, and project documentation
## 🚀 Live Interactive Dashboard
## 📂 Repository Contents
| **File Name**                              | **Description**                                                                                                                           |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Health_care_PowerBi_dashboard_com.pbix** | Complete Power BI report file containing all dashboards — Patients, Doctors, Clinics, and Treatments, with KPIs, measures, and bookmarks. |
| **Health_care_Analytics_Dashboard.xlsx**   | Cleaned healthcare dataset used to build the Power BI dashboards (Patients, Doctors, Treatments, Visits, Lab Results).                    |
| **dashboard-overview.png**                 | Full dashboard screenshot showing the overall Healthcare Analytics view.                                                                  |
| **Doctors.png**                            | Screenshot of the **Doctors Dashboard** highlighting doctor performance, specialties, success rate, and workload analytics.               |
| **Patient.png**                            | Screenshot of the **Patients Dashboard** showing patient demographics, follow-up analysis, age distribution, and diagnosis insights.      |

## 🎓 Skills Demonstrated
| **Skill Area**                                   | **Description**                                                                                                                        |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| **SQL & MySQL Database Design**                  | Table creation, relationships, indexing, and loading healthcare data (Patients, Doctors, Visits, Treatments, Lab Results).             |
| **Data Cleaning (Excel + Power Query)**          | Handling missing values, standardizing formats, deduplication, data enrichment, and preparing clean datasets for Power BI.             |
| **ETL Processes — Power Query**                  | Transforming datasets, merging tables, creating calculated columns, and shaping data for modeling.                                     |
| **Data Modeling (Star Schema)**                  | Creating optimized relationships between fact tables (Visits, Treatments, Labs) and dimensions (Patients, Doctors, Date).              |
| **DAX Measures**                                 | Building complex KPIs: Total Patients, Avg Age, Follow-up Required, Doctor Success Rate, Treatment Cost Analytics, Revenue metrics.    |
| **Business Intelligence & Healthcare Analytics** | Understanding clinical workflows and analyzing patient journeys, treatment outcomes, doctor performance, and operational insights.     |
| **Data Visualization**                           | Selecting appropriate visuals: age distribution, diagnosis insights, gender breakdown, doctor success rate, specialty-level analytics. |
| **UX/UI Dashboard Design**                       | Designing a clean layout using dark theme, visual hierarchy, spacing, and clustering related insights.                                 |
| **Color Theory**                                 | Using accessible, meaningful colors: cyan (primary), mint green (success), orange (critical), blue/pink (gender).                      |
| **Interactive Design**                           | Implementing bookmarks for Patients, Doctors, Treatments, Male/Female filters, and follow-up segmentation.                             |
| **Technical Documentation**                      | Creating structured README.md including objective, dataset details, visuals, KPIs, and file overview.                                  |
| **Power BI Publishing**                          | Publishing to Power BI Service, enabling refresh, and sharing dashboards for collaboration.                                            |

## 🚀 Outcome
A recruiter-ready Healthcare Analytics Power BI Dashboard that analyzes patient demographics, doctor performance, treatment outcomes, lab results, follow-up trends, and hospital operational metrics — demonstrating strong skills in Excel-based data cleaning, MySQL data handling, data modeling, DAX calculations, interactive navigation, and modern dashboard design principles.

This project showcases the complete end-to-end BI development lifecycle:
Excel data cleaning → MySQL import → Data modeling → Power BI connection → DAX measures → Dashboard creation → Bookmarks & interactions → Publishing — making it an ideal portfolio project for Data Analyst, Healthcare Analyst, Business Intelligence Analyst, and Power BI Developer roles.
## 🙏 Acknowledgments
* Built as part of a Power BI portfolio project to demonstrate end-to-end business intelligence capabilities in a healthcare setting.

* Healthcare dataset prepared using Excel-based cleaning and MySQL import, ensuring realistic patient, doctor, treatment, and lab data structure.

* Designed following Microsoft Power BI best practices, including optimized modeling, performance tuning, and accessible visual design.

* Color palette inspired by modern healthcare dashboards, using medically intuitive colors like cyan (information), green (success), and orange (alerts).

* Interactive bookmark navigation showcases advanced Power BI user experience design, enabling fast switching between Patients, Doctors, and Treatments dashboards.