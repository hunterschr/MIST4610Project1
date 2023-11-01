# Team 3 Mist 4610 Group Project 1 

## Team Name:
29704 3

## Team Members:
#### 1. Hunter Schramm [@hunterschr](https://github.com/hunterschr)
#### 2. Will Hensley  [@Willhens15](https://github.com/willhens15)
#### 3. Shweta Sainathan [@ShwetaSainathan](https://github.com/ShwetaSainathan)
#### 4. Aidan Davies [@aidan.davies@uga.edu](https://github.com/AidanDavies117)
#### 5. Lauren Prisock [@laurenPrisock](https://github.com/laurenPrisock)

## Problem Description:
We are tasked with modeling and building a relational database for an emergency health clinic. The database will revolve around the ``Patient`` and ``Appointments`` entities, with all other entities playing a critical role in one of the two. We will accurately model the relationships between entities, populate their attributes with sample data, and create working queries to adequately test our database's ability to provide the information our customer needs.


## Data Model:
Explanation of data model:

Our database model is based on the structure of an emergency healthcare clinic. The central entity in the model is the ``Patient`` table, which contains important information about all patients who visit the clinic, such as their patient ID, phone number, email, and date of birth. The patient's ID is used as the primary identifier for patients throughout the database, so it is referenced in many other tables.

The first table that references the patient ID is the ``MedicalRecords`` table. Each patient has one medical record and each medical record belongs to one patient. The ``MedicalRecords`` table contains information such as the record ID, diagnosis, and test results.

As each patient sees their assigned doctor they might be prescribed medications. The result of this relationship is the ``Prescriptions`` table. Each patient can have many prescriptions, and each doctor can prescribe many medications. The ``Prescriptions`` table,  includes the patient ID, staff ID, dosage, prescriptionID, expiration, etc.

When checking into the clinic, each patient provides their insurance information. Each patient has one insurance provider, and each insurance provider has a single policy per patient. The ``Insurance`` table contains information about each insurance provider, such as the insurance ID, policy number, and provider name.

The next crucial entity in the model is ``Appointments``, which is another result of a many-to-many relationship between Employee and Patient. The ``Appointments`` table contains the time, date, staff ID, and patient ID associated with the appointment.

Each appointment can have a varying amount of payments, which are tracked via the ``Payments`` table. ``Payments`` keeps track of the amount for a payment, payment type, invoice date, and any other attributes essential for a payment invoice. 

Appointments also provide services to each patient. These services logged within the ``ServiceForAppointment`` table, which is a result of a a many-to-many relationship with servicesProvided. ``ServiceForAppointment`` houses information about what service was used during an appointment as well as what staff member and patient were involved. 

``ServicesProvided`` contains important information about a particular service given during an appointment like the name of the service, its cost, its ID, etc. ServicesProvided then connects to ``Inventory`` to form ``ItemForService``, which keeps track of what items within the inventory were used for a service. The ``Inventory`` table keeps track of the name of equipment, the quantity in stock, the type of equipment, etc. 

The ``EmployeeType`` table keep track of the types of employees through the type ID attributes as well as a description of their role. Each employee type can have a multitude of employee within it, but an employee can only belong to one type. The ``Employee`` table contains information about an employee such as their name, ID, email, phone number, etc.

## Data Dictionary:

### Table: Appointments

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| medical staff_staffID  | Part of composite PK, unique ID identifying each medical staff   | VARCHAR | 5 | | Part of PK |
| patient_patientID  | Part of composite PK, unique ID identifying each patient  | VARCHAR | 5 | | Part of PK |
| date  | Date of appointment  | DATETIME | | | |
| time  | Time of appointment  | DATETIME | | | |

### Table: EmployeeType

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| typeID  | PK, unique name identifying employee type   | VARCHAR | 10 | | PK |
| roleDescription  | Description of the role for the employee type  | VARCHAR | 45 | | |

### Table: Insurance

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| insuranceID  | PK, unique number identifying insurance provider   | VARCHAR | 10 | | PK |
| policyNo  | Number of policy on file  | VARCHAR | 45 | | |
| coverage  | Amount paid each month  | VARCHAR | 45 | | |
| providerName  | Name of insurance provider  | VARCHAR | 45 | | |
| providerPhone  | Phone number for insurance provider  | VARCHAR | 45 | | |


### Table: Inventory

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| inventoryID  | PK, unique ID identifying the different equipments   | VARCHAR | 5 | | PK |
| equipmentID | # to determine equipment | VARCHAR | 45 | 
| equipmentName  | Name of Equipment  | VARCHAR | 45 | | |
| equipmentType  | Branch of Medicine associated with equipment  | VARCHAR | 45 | | |
| quantityInStock  | Number of the equipment remaining  | INT | | | |



### Table: ServicesProvided

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| serviceID  | PK, unique ID identifying each service provided   | VARCHAR | 45 | | PK |
| serviceName  | Name of service  | VARCHAR | 45 | | |
| department  | Department that handles the service  | VARCHAR | 45 | | |
| description  | Description of the service  | VARCHAR | 45 | | |
| cost  | Cost of the service  | VARCHAR | 10 | | |

### Table: Payments

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| paymentID  | PK, Primary key for payments table   | VARCHAR | 5 | | PK |
| amount | The total payment amount | INT | | 
| paymentNumber | The credit card number on file | VARCHAR | 45 | | |
| insurancePayment  | How much the insurance company pays out of the total payment  | VARCHAR | 45 | | |
| patientPayment | How much the Patient pays out of pocket for the total payment | VARCHAR | 45| | |
| invoiceDate | Date the charge was made | DATETIME ||||
| paymentDate | Date the payment was processed and completed | DATETIME ||||
| staffID |The staff who will be paid from this action  | VARCHAR |5||FK|
| paymentID | The Patient who will be making the payment  | VARCHAR |5||FK|
| providerID | The Insurance provider who will be making the payment  | VARCHAR|5||FK|


### Table: Prescriptions
| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| prescriptionID | PK, unique ID identifying each prescription   | VARCHAR | 45 | | PK |
| prescriptionDate | Date of filling  | DATE |
| prescriptionExpiration | Date it Expires | DATE |
| dosage | # of milligrams  | VARCHAR | 45 | 
| pharmacyLocation | Location of filling| VARCHAR | 45 | | |


## Queries:

| Feature   | Query 1  | Query 2  | Query 3  | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |     
| ----------| ---------| ---------| -------- | ------- | ------- | ------- | ------- | ------- | ------- | -------- |
| Multiple table join  | X |  |  |  |  |  |  |  |  |  |
| Subquery  |  |  |  |  |  |  |  |  |  |  |
| GROUP BY  |  |  |  |  |  |  |  |  |  |  |
| GROUP BY with HAVING  |  |  |  |  |  |  |  |  |  |  |
| Multi conditional WHERE  | X |  |  |  |  |  |  |  |  |  |
| Built in functions  | X |  |  |  |  |  |  |  |  |  |
| REGEXP  |  |  |  |  |  |  |  |  |  |  |
| NOT EXISTS  |  |  |  |  |  |  |  |  |  |  |

### Query 1:
  Query 1 lists out the patient names and their diagnosis for any patients seen at the clinic within the last year. The results are ordered by diagnosis.

<img width="600" alt="Screenshot 2023-11-01 at 12 30 05 PM" src="https://github.com/hunterschr/MIST4610Project1/assets/105222813/40e9e6e1-905c-4507-a763-0c6e5ebbdb12">


  This query allows staff at the clinic to view the names of all patients that have come in within the past year, as well as their diagnosis. This query will help the clinic track trends in disease incidence and prevalence, which can help them allocate resources more effectively and identify patients who may need preventive care. 

## Database Information:
