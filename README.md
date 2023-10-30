# Team 3 Mist 4610 Group Project 1 

## Team Name:
29704 3

## Team Members:
#### 1. Hunter Schramm [@hunterschr](https://github.com/hunterschr)
#### 2. Will Hensley  [@Willhens15](https://github.com/willhens15)
#### 3. Shweta Sainathan [@ShwetaSainathan](https://github.com/ShwetaSainathan)
#### 4. Aidan Davies [@aidan.davies@uga.edu](https://github.com/AidanDavies117)

## Problem Description:
We are tasked with modeling and building a relational database for an emergency health clinic. The database will revolve around the ``patient`` and ``Appointment`` entities, with all other entities playing a critical role in one of the two. We will accurately model the relationships between entities, populate their attributes with sample data, and create working queries to adequately test our database's ability to provide the information our customer needs.


## Data Model:
Explanation of data model:

Our database model is based on the structure of an emergency healthcare clinic. The central entity in the model is the ``patient`` table, which contains important information about all patients who visit the clinic, such as their patient ID, phone number, email, and date of birth. The patient's ID is used as the primary identifier for patients throughout the database, so it is referenced in many other tables.

The first table that references the patient ID is the ``MedicalRecords`` table. Each patient has one medical record and each medical record belongs to one patient. The ``MedicalRecords`` table contains information such as the record ID, diagnosis, and test results.

As each patient sees their assigned doctor they might be prescribed medications. The result of this relationship is the ``Prescription`` table. Each patient can have many prescriptions, and each doctor can prescribe many medications. The ``Prescription`` table,  includes the patient ID, staff ID, dosage, prescriptionID, expiration, etc.

When checking into the clinic, each patient provides their insurance information. Each patient has one insurance provider, and each insurance provider has a single policy per patient. The ``InsuranceProviders`` table contains information about each insurance provider, such as the insurance ID, policy number, and provider name.

The next crucial entity in the model is ``Appointment``, which is another result of a many-to-many relationship between Employee and Patient. The Appointment table contains the time, date, staff ID, and patient ID associated with the appointment.

Each appointment can have a varying amount of payments, which are tracked via the ``payments`` table. ``payments`` keeps track of the amount for a payment, payment type, invoice date, and any other attributes essential for a payment invoice. 

Appointments also provide services to each patient. These services logged within the ``serviceForAppointment`` table, which is a result of a a many-to-many relationship with servicesProvided. ``serviceForAppointment`` houses information about what service was used during an appointment as well as what staff member and patient were involved. 

``ServicesProvided`` contains important information about a particular service given during an appointment like the name of the service, its cost, its ID, etc. ServicesProvided then connects to ``Inventory`` to form ``itemForService``, which keeps track of what items within the inventory were used for a service. The ``inventory`` table keeps track of the name of equipment, the quantity in stock, the type of equipment, etc. 

The ``employeeType`` table keep track of the types of employees through the type ID attributes as well as a description of their role. Each employee type can have a multitude of employee within it, but an employee can only belong to one type. The ``employee`` table contains information about an employee such as their name, ID, email, phone number, etc.

## Data Dictionary:

### Table: Appointment

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| medical staff_staffID  | Part of composite PK, unique ID identifying each medical staff   | VARCHAR | 5 | | Part of PK |
| patient_patientID  | Part of composite PK, unique ID identifying each patient  | VARCHAR | 5 | | Part of PK |
| date  | Date of appointment  | DATETIME | | | |
| time  | Time of appointment  | DATETIME | | | |

### Table: employeeType

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| typeID  | PK, unique name identifying employee type   | VARCHAR | 5 | | PK |
| descriptionOfRole  | Description of the role for the employee type  | VARCHAR | 45 | | |

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

### Table: servicesProvided

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| serviceID  | PK, unique ID identifying each service provided   | VARCHAR | 5 | | PK |
| serviceName  | Name of service  | VARCHAR | 45 | | |
| department  | Department that handles the service  | VARCHAR | 45 | | |
| description  | Description of the service  | VARCHAR | 100 | | |
| cost  | Cost of the service  | VARCHAR | 45 | | |

### Table: Prescription
| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| prescriptionID | PK, unique ID identifying each prescription   | VARCHAR | 6 | | PK |
| medicationName | Name of medicine | VARCHAR | 45 | | |
| prescriptionDate | Date of filling  | VARCHAR | 8 | | |
| dosage | # of milligrams  | VARCHAR | 2 | | |
| pharmacyLocation | Location of filling| VARCHAR | 45 | | |

### Table: Inventory

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| inventoryID  | PK, unique ID identifying the different equipments   | VARCHAR | 5 | | PK |
| equipmentName  | Name of Equipment  | VARCHAR | 45 | | |
| equipmentType  | Branch of Medicine associated with equipment  | VARCHAR | 45 | | |
| quantityInStock  | Number of the equipment remaining  | INT | | | |

## Queries:

| Feature   | Query 1  | Query 2  | Query 3  | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |     
| ----------| ---------| ---------| -------- | ------- | ------- | ------- | ------- | ------- | ------- | -------- |
| Multiple table join  |  |  |  |  |  |  |  |  |  |  |
| Subquery  |  |  |  |  |  |  |  |  |  |  |
| GROUP BY  |  |  |  |  |  |  |  |  |  |  |
| GROUP BY with HAVING  |  |  |  |  |  |  |  |  |  |  |
| Multi conditional WHERE  |  |  |  |  |  |  |  |  |  |  |
| Built in functions  |  |  |  |  |  |  |  |  |  |  |
| REGEXP  |  |  |  |  |  |  |  |  |  |  |
| NOT EXISTS  |  |  |  |  |  |  |  |  |  |  |

## Database Information:
