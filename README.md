# Team 3 Mist 4610 Group Project 1 

## Team Name:
29704 3

## Team Members:
#### 1. Hunter Schramm [@hunterschr](https://github.com/hunterschr)
#### 2. Will Hensley  [@Willhens15](https://github.com/willhens15)
#### 3. Shweta Sainathan [@ShwetaSainathan](https://github.com/ShwetaSainathan)
#### 4. Aidan Davies [@aidan.davies@uga.edu](https://github.com/AidanDavies117)
#### 5. Lauren Prisock [@laurenPrisock](https://github.com/laurenPrisock)
#### 6. Sohum Rane [@srane05](https://github.com/srane05)

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

![image](https://github.com/hunterschr/MIST4610Project1/assets/105222813/bbbc7ff3-d784-4714-9583-14861512fd38)


## Data Dictionary:

### Table: Appointments

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| staffID  | Part of composite PK, unique ID identifying each medical staff   | VARCHAR | 5 | 1| Part of PK |
| patientID  | Part of composite PK, unique ID identifying each patient  | VARCHAR | 5 | P##| Part of PK |
| time  | Time of appointment  | DATETIME | | | |


### Table: Employee

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| staffID  | PK, Primary key for medical staff  | INT | 10 | 1| PK |
| staffName | The first and last name of the employee | VARCHAR |45 | |
| staffPhone | The phone number of the employee | VARCHAR | 45 | | |
| staffEmail  | The email address of the employee  | VARCHAR | 45 | | |
| specialization | The area of medicine the employee specializes in | VARCHAR | 45| | |
| shiftSchedule | The time of day the employee usually works | VARCHAR|45|||
| credentials | The highest level of medical recognition for the employee | VARCHAR|45|||
| salary |The annual salary of the employee  | VARCHAR |45|||
| typeID | The type of employee they are  | VARCHAR |10||FK|


### Table: EmployeeType

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| typeID  | PK, unique name identifying employee type   | VARCHAR | 10 | | PK |
| roleDescription  | Description of the role for the employee type  | VARCHAR | 45 | | |

### Table: Insurance

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| insuranceID  | PK, unique number identifying insurance provider   | VARCHAR | 10 |IN## | PK |
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


### Table: medicalRecords

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| recordID  | PK, The unique identifier for each patient’s medical record   | VARCHAR | 45 | | PK |
| description | The description of the patient’s medical history | VARCHAR | 200 | 
| diagnosis  | The diagnosis that the medical staff made for the patient  | VARCHAR | 100 | | |
| treatment  | The type of treatment given for one instance  | VARCHAR | 200 | | |
| testResults | Any type of test given to the patient  | varchar | 200| | |
| prescription  | Ant type of medicine that has been or is currently prescribed to the patient  | VARCHAR | 45 | | |
| patientID  | The patient linked to the individual medical record | VARCHAR | 5| | |


### Table: Patients

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| patientID  | PK, Primary key for patient   | VARCHAR | 10 | | PK |
| patientName | The first and last name of the patient | VARCHAR |45 | |
| patientPhone | The phone number of the patient | VARCHAR | 45 | | |
| patientEmail  | The email address of the patient  | VARCHAR | 45 | | |
| patientAddress | The home address of the patient | VARCHAR | 45| | |
| doB | The date of birth of the patient | DATETIME ||||
| emergencyContactName | The first and last name of the emergency contact for the patient | VARCHAR|45|||
| emergencyContactPhone |The phone numbeer of the emergency contact for the patient  | VARCHAR |45|||
| insuranceID | The insurance provider of the patient  | VARCHAR |10||FK|



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
| staffID | FK, the staff member who ordered prescription filled | INT |  | | FK |
| patientID | FK, patient who recieved prescription   | VARCHAR | 45 | | FK |
| prescriptionID | PK, unique ID identifying each prescription   | VARCHAR | 45 | | PK |
| prescriptionDate | Date of filling  | DATE |
| prescriptionExpiration | Date it Expires | DATE |
| dosage | # of milligrams  | VARCHAR | 45 | 
| pharmacyLocation | Location of filling| VARCHAR | 45 | | |

### Table: ServicesProvided

| Column Name   | Description   | Data Type  | Size  | Format | Key? |   
| ------------- | ------------- | ---------- | ----- | ------ | ---- |
| serviceID  | PK, unique ID identifying each service provided   | VARCHAR | 45 | | PK |
| serviceName  | Name of service  | VARCHAR | 45 | | |
| department  | Department that handles the service  | VARCHAR | 45 | | |
| description  | Description of the service  | VARCHAR | 45 | | |
| cost  | Cost of the service  | VARCHAR | 10 | | |


## Queries:

| Feature   | Query 1  | Query 2  | Query 3  | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |     
| ----------| ---------| ---------| -------- | ------- | ------- | ------- | ------- | ------- | ------- | -------- |
| Multiple table join  | X |  |  |  |  |  | X |  | X | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | X |
| Subquery  |  |  |  | X | X |  |  |  |  | X |  |  |  | X |  |  |  |  |  |  |  |  |  |  | |  |  |  |  |  |   | X |  
| GROUP BY  |  | X | X |  |  |  | X |  | X | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | | X |
| GROUP BY with HAVING  |  |  |  |  | X |  |  |  |  |  |
| Multi conditional WHERE  | X |  |X  |  |  | X |  |  |  |  |
| Built in functions  | X | X |  |  | X |  |  |  |  |  |
| REGEXP  |  |  | X | X |  | X |  |  |  |  |
| NOT EXISTS  |  |  |  | X |  |  |  |  |  |  |

### Query 1:
  Query 1 lists out the patient names and their diagnosis for any patients seen at the clinic within the last year. The results are ordered by diagnosis.

<img width="600" alt="Screenshot 2023-11-01 at 12 30 05 PM" src="https://github.com/hunterschr/MIST4610Project1/assets/105222813/40e9e6e1-905c-4507-a763-0c6e5ebbdb12">


  This query allows staff at the clinic to view the names of all patients that have come in within the past year, as well as their diagnosis. This query will help the clinic track trends in disease incidence and prevalence, which can help them allocate resources more effectively and identify patients who may need preventive care. 

### Query 2:
  Query 2 lists out the average age of patients with particular diagnoses.

![image](https://github.com/hunterschr/MIST4610Project1/assets/105222813/64a7a393-46ef-49e5-aadc-e669575d475f)

  This query can be used to identify patterns in diagnoses based on age, which can be used to improve patient care and develop more effective treatment plans. 

  ### Query 3:
  Query 3 lists out the number of patients who are insured by a certain Insurance Provider. 

![A2E0DB8D-A542-4F5E-B637-92CCF3FB0378](https://github.com/hunterschr/MIST4610Project1/assets/148145159/6829d7dc-f260-4d25-ab4a-607ee37ab235)


  This query allows staff at the clinic to view how many patients at the hospital are insured by a specific insurance provider. For example, Humana currently insures 5 patients and Anthem insures 17. This makes it easier ot staff to tell which provider is most widely used among patients, and can determine future contracts with these providers. 

  
 ### Query 4:
  Query 4 lists out the names of patients who have never required surgery. 
  
![D39F3891-9D25-4BE2-9769-2EC23991393F](https://github.com/hunterschr/MIST4610Project1/assets/148145159/e5710c7b-95a8-4db9-a74f-f6cad400cf3e)


  This query allows staff at the clinic to view which patients have never needed any type of surgery. This query will help determine those who come in to the clinic for regular check-ups and therefore, have a history of being generally healthy. Surgery is very intensive, and requires an additional medical staff member (surgeon), only a few patients will need this type of care. The majority of patients will not fall under this category, so the clinic can determine who those patients are through this query. Additionally, the clinic could insert an EXISTS clause to determine which patients have needed surery in the past. 


 ### Query 5:
  Query 5 lists out the job in the hospital with an average salary that is greater than the average of all salaries for employees at the hospital. 
  
<img width="804" alt="Screenshot 2023-11-02 at 10 44 57 PM" src="https://github.com/hunterschr/MIST4610Project1/assets/148081356/4a2a4d3b-4993-42ed-814d-db82d0b9aea1">


  This query allows for identification of which job/jobs are higher paid than the average employee at the hospital and what the average salary looks loke for that job or those jobs. This information is useful as it is an important data point that the hospital can leverage as they hire new employees, promote existing employees, and plan their budget for salaries. This data point also allows the hospital to quantify their investment in highly-paid talent, which can be used as a reference for their future planning.


   ### Query 6:
  Query 6 lists out the staff at the hospital that are on call and their id, name, phone number, and credentials. The query is filtered by the input, which is the credential that is being searched for. 
  
<img width="930" alt="Screenshot 2023-11-03 at 9 47 08 AM" src="https://github.com/hunterschr/MIST4610Project1/assets/148081356/b6e5fd58-2f3d-42f8-a8ed-4583f85f85ce">


  This query allows for hospital management and administration to quicky identify the medical staff that is on call and available to be called in. The contact information, the staff's phone number, is the crucial piece of information necessary to call them in. Their ID, name, and credentials are also displayed. The query is filtered by the input which is the credential of the staff. This speeds up the process of finding the right people to call in. Management can directly ask for an MD (Doctor), RN (Nurse), LPN (Licensed Practical Nurse), or PharmD (Pharmacist) and can view who among the credential they searched for matches the credential and what their contact information is in order to be called in.

### Query 7
  Query 7 lists out the name of the doctor, their specialization, and the number of patients they had an appointment with.

![image](https://github.com/hunterschr/MIST4610Project1/assets/148078185/20bfde52-e3c6-4d25-94a3-b854085fa36f)

  This query allows for staff to compare the number of patients each doctor had an appointment with. This query also helps to recognize which departments are treating a high volume of patients compared to other departments, which would let the administrative staff allocate the proper funding and resources to the departments that need it. On the other hand, this query would also help determine which departments and doctors are not meeting patient or appointment expectations.

### Query 9
  Query 9 lists out the type of employee, their description, and the amount of those employees in the clinic.

![image](https://github.com/hunterschr/MIST4610Project1/assets/148078185/3e46d192-0a19-4bc2-8b51-2c93eef8a451)

  This query allows for a comparison of the different types of employees working at the clinic currently. As a result, the administrative staff can reference this query before making any new hires, when considering to downsize, and it helps administrative staff to determine which employees are more needed than others as well.

### Query 10
  Query 10 lists out the different services and the number of appointments In which each service was provided.
  
<img width="754" alt="Screenshot 2023-11-03 at 1 05 49 PM" src="https://github.com/hunterschr/MIST4610Project1/assets/148081620/eb1a2133-e6e1-43ec-b4d3-fc6bff6aea87">

  This query allows staff members to compare which procedures are the most common and uncommon. This information can help the hospital understand where inventory is moving around, which departments of the hospital have the most patients and highest traffic, and which services are more of a priority to the hospital/core to the hospital's main focuses.

  
## Database Information:
Name of the database: ns_F2329704Group3

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
