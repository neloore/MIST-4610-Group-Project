# MIST-4610-Group-Project
Repository for the SQL group project hospital management database.

Team Name

Sp25_21479_Group2

Team Members

Buckner, Alexa @amb21398
Eloore, Neha @neloore
Nguyen, Hung @triumviratesys
Spraker, Dabney @dps24510
Dorrien, Leah @leahdorrien2
Scenario Description

The Hospital Management system was made as a digital system to efficiently manage information regarding the employees working in the hospital and the patients entering and leaving. In a modern hospital setting, managing a large volume of patients, staff, billing, and medical processes requires an integrated system to meet medical regulations and optimize resources. Through this system the hospital is able to manage patient care, staff scheduling, medical records, prescriptions, and department operations within a hospital environment. This system serves as a central database for tracking appointments, patient history, prescriptions, staff shifts, and billing information, ensuring smooth operations and effective healthcare delivery.

Data Model Explanation

image
Our model is based on the structure of a hypothetical hospital system. The Departments entity represents different departments within the hospital, such as Cardiology, Emergency, or Pediatrics. Each department can have multiple staff members and doctors, reflected in one to many, non-identifying relationships between Departments and Staff and Departments and Doctors. These relationships are non-identifying because staffID and doctorID remain the same even if a staff member or doctor changes departments.

We chose to have separate Staff and Doctor entities because not all employees should be classified as doctors. Only doctors are associated with entities such as Appointments, MedicalRecords, and Prescriptions.

The Staff entity represents hospital employees, including nurses, administrative workers, and technicians, with job titles and department assignments. Staff schedules are captured in the StaffSchedule entity, linking staff members to shifts recorded in the Shifts entity, which includes start times, end times, and shift types. The relationship between Staff and StaffSchedule is one to many and identifying. The relationship between StaffSchedule and Shifts is also a one to many, identifying relationship. This is because each schedule record depends on both a specific staff member and a specific shift. Each staff member can appear multiple times on the schedule (one to many), and each schedule entry must be linked to exactly one staff member and one shift (identifying). Each of the schedule entities also include a shift status to show whether a shift is completed, cancelled, or active.

Similarly, the Doctors entity contains doctor names, specializations, and department assignments. Doctor shift schedules are managed through the DoctorSchedule entity, which functions identically to StaffSchedule, forming one to many, identifying relationships with both Doctors and Shifts. The Patients entity stores patient demographics, contact information, medical details (such as blood type and allergies), and links to their pharmacy and insurance information. There is a one to many, non-identifying relationship between Patients and Appointments, since each patient can have multiple appointments, but each appointment has its own identity and simply references the patient. The relationship between Doctors and Appointments is also a one to many, non-identifying relationship, as each doctor may have multiple appointments, but each appointment only points to one doctor.

The same applies to EmergencyContacts, where patients can have many emergency contacts, but said records and contacts can exist independently of the patient. Conversely, pharmacies and insurance companies also have a 1-M relationship with Patients, but they are referenced as foreign keys on the Patients entity. These firms can accommodate many patients, but each patient only needs to go to one pharmacy and be on one insurance plan. Patient medical history is stored in the MedicalRecords entity, recording diagnoses, treatments, dates, and links to the patient and doctor responsible. This is a one to many, identifying relationship between Patients and MedicalRecords because each medical record is uniquely tied to a patient and cannot exist without them. The relationship between Doctors and MedicalRecords is one to many, non-identifying, since each doctor may have multiple records associated with them, but the records are independent entities with their own primary keys. As such, the MedicalRecords entity contains patientID and doctorID as foreign keys.

The Appointments entity records reasons, dates, statuses, and links to both the doctor and patient. Billing for these appointments is tracked in the Billings entity. There is a one to many, non-identifying relationship between Appointments and Billings, as one appointment may have multiple billing records (for partial payments or adjustments), but each billing entry exists independently and only references one appointment. Prescriptions are recorded in the Prescriptions entity, with details on medication name, dosage, duration, prescribing doctor, patient, and prescription date. There is a one to many, non-identifying relationship between Patients and Prescriptions and Doctors and Prescriptions. A patient can have multiple prescriptions, and each prescription is issued by one doctor, but each prescription exists independently with its own unique ID. The Pharmacies entity stores pharmacy details. There is a one to many, non-identifying relationship between Pharmacies and Patients, as each pharmacy can serve multiple patients, but each patient is linked to only one pharmacy. The pharmacy exists independently of any patient.

The InsurancePolicies entity holds policy numbers and company details. It has a one to many, non-identifying relationship with Patients, where one insurance policy may cover multiple patients, but the policy exists independently of any single patient.

Lastly, the EmergencyContacts entity allows each patient to have multiple emergency contacts, with phone numbers, addresses, and relation types recorded. This is a one to many, non-identifying relationship, as emergency contacts can exist as independent entries linked to only one patient.

Data Dictionary

image image image image image image image image image image image image image image image image image
Queries

image
Query 1 lists the patient’s first name, last name, and their emergency contact’s name if their blood type is O negative. The results are also listed in descending order based on the patient’s last name.
image Query 1 allows the hospital management system to see which of their patients has an O negative blood type. O negative is considered the “universal donor” as any individual can receive this blood type. People with O negative blood are often sought out to see if they'd be willing to donate their blood, which could potentially save hundreds of others lives.
Query 2 lists the patient's first and last time and their total outstanding billing amount for bills that are pending or overdue. The results are listed in descending order by the total outstanding billing amount.

image
Query 2 allows the staff in charge of billings to oversee how much money they are still waiting to receive from the patients in their care. Including both pending and overdue payments, the system can contact these individuals to check in on their payments and keep track of who they are owed money from.

Query 3 lists out the pharmacy’s name and the number of patients at each pharmacy.
image
Query 3 allows the billing staff to look over all of the different pharmacies that their patients are assigned to. Based on the pharmacy, they can make certain deals with the hospital if enough patients are assigned and receiving medication orders/refills. They can also maintain their business relationships with these suppliers, which will strengthen their business overal

Query 4 lists out the patient’s first name, last name, ID, appointment reason, and bill for their appointment if it is greater than the average billing amount in the hospital.
image
Query 4 allows the hospital billing staff to see the patient’s name, their ID number, their appointment reason, and the bill for their appointment if it is greater than the average bill amount for the hospital. This gives a general idea for the staff to see which appointments cost more than the typical average of all appointments within the hospital. This also brings forth important information such as which patients are bringing more than the average revenue from appointments, future budgeting plans, and whether or not resources need to be allocated more.

Query 5 lists the patients ID, first name, last name, and their phone number if they do not have any allergies, they are not a minor, and they are not taking any medications.
image
Query 5 allows the hospital staff who are in charge of keeping data and improving upon the hospital itself to possibly give patients surveys and record their experiences. In order to get the best results while taking the survey, the patient must not have any allergies, must be older than 18, and not currently taking medication. They then can have a list of patients to ask if they’d be willing to take the survey and use their data to better improve the hospital.

Query 6 lists the doctors ID, first name, last name, and the amount of overtime hours they have worked. Overtime is considered to be above 40 hours within a working week and they will be paid time and a half.
image
Query 6 allows the hospital staff in charge of the doctor’s payroll to see who needs to be compensated properly for any time worked above the normal 40 hours a week. If a doctor has worked more than 40 hours, then they can be paid extra money for any additional hours worked. This makes it a lot easier to see who has worked overtime and who has not.

Query 7 lists the names of all of the staff members such as their ID, first name, last name, job title, and department name (not including doctors) who work less than 2 night shifts.
image
Query 7 allows any shift supervisors to see which staff members work less than 2 night shifts for a work week. Supervisors can use this to determine if there is anyone in the department that can possibly pick up more night shifts due to them working less than 2.

Query 8 lists the patients’ first name, last name, and medication name for each medication of those who are taking more than 1 prescription. Order by the patient’s names.
image
Query 8 allows doctors to look through their patients and know which patients are taking more than one medication and the names of those medications. Taking multiple medications at the same time can increase the risk of dangerous side effects occurring, so it is very important for doctors to know what their patients are taking in order to keep their patient safe. It is also helpful in determining if the patient can take more medications based on what they are already taking.

Query 9 determines the distribution of insurance companies among insured patients in the hospital
image
Query 9 allows the hospital to understand who their top insurance providers are (in terms of patients insured). With this information, the management staff can better optimize the billing system, know the prominent insurance company among patients, and streamline the insurance process by understanding how the prominent insurance companies work. If the providers are in equal proportion, the query also sorts providers alphabetically.

Query 10 lists the patient’s first name, last name, age, and their diagnosis if they are born after 01/01/1997
image
Query 10 is useful for the hospital staff to relay important information to doctors on how to treat younger patients that are a part of Generation Z or Alpha. Knowing your patient’s age difference is key in helping understand them and what can be different in their treatment compared to individuals who are Millennials or Generation X.

Database Information

Name of the database: ns_Sp25_21479_Group2

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
