# Team 3 Mist 4610 Group Project 1 

## Team Name:
29704 3

## Team Members:
#### 1. Hunter Schramm [@hunterschr](https://github.com/hunterschr)
#### 2. Will Hensley  [@Willhens15](https://github.com/willhens15)
#### 3. Shweta Sainathan [@ShwetaSainathan](https://github.com/ShwetaSainathan)

## Problem Description:


## Data Model:
Explanation of data model:

Our model is based on the structure of an emergency healthcare clinic. 
## Data Dictionary:

### Table: Appointment

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| medical staff_staffID  | Part of composite PK, unique ID identifying each medical staff   | VARCHAR | 5 | | Part of PK |
| patient_patientID  | Part of composite PK, unique ID identifying each patient  | VARCHAR | 5 | | Part of PK |
| date  | Date of appointment  | DATETIME | | | |
| time  | Time of appointment  | DATETIME | | | |

### Table: InsuranceProviders

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| insuranceID  | PK, unique number identifying insurance provider   | INT | | | PK |
| policyNo  | Number of policy on file  | VARCHAR | 45 | | |
| coverage  | Coverage of policy  | VARCHAR | 45 | | |
| providerName  | Name of insurance provider  | VARCHAR | 45 | | |
| providerPhone  | Phone number for insurance provider  | VARCHAR | 45 | | |
| providerEmail  | Email for insurance provider  | VARCHAR | 45 | | |
| insuranceRate  | Cost of insurance  | INT | | | |
| patient_patientID  | FK - Patient, specifies ID of patient attached to insurance policy  | INT | | | FK - Patient |

## Queries:

## Database Information:
