# MIST-4610-Group-Project
Repository for the SQL group project hospital management database.

# Team Name

Sp25_21479_Group2

# Team Members

Buckner, Alexa @amb21398

Eloore, Neha @neloore

Nguyen, Hung @triumviratesys

Spraker, Dabney @dps24510

Dorrien, Leah @leahdorrien2

# Scenario Description

The Hospital Management system was made as a digital system to efficiently manage information regarding the employees working in the hospital and the patients entering and leaving. In a modern hospital setting, managing a large volume of patients, staff, billing, and medical processes requires an integrated system to meet medical regulations and optimize resources. Through this system the hospital is able to manage patient care, staff scheduling, medical records, prescriptions, and department operations within a hospital environment. This system serves as a central database for tracking appointments, patient history, prescriptions, staff shifts, and billing information, ensuring smooth operations and effective healthcare delivery.

# Data Model Explanation
[
](https://private-user-images.githubusercontent.com/198940325/424273154-ee616e47-91e5-462e-baac-93bc3480af98.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjczMTU0LWVlNjE2ZTQ3LTkxZTUtNDYyZS1iYWFjLTkzYmMzNDgwYWY5OC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04OTQ5MmY1ZDg4MmE5NmUyZmM0OTYzYTA4YjU0ZGJkNTc0NWVhZjkxZWVhNTFjODI0NGRhZjc0ZjJhZmMyZTZkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.6fdGygVQlBh5JkkJE9yZwniWASA5ZPjtoPdqJXrEi0E)![image](https://github.com/user-attachments/assets/e09a87e9-51f8-44a5-a8e8-4c9600d6be46)
Our model is based on the structure of a hypothetical hospital system. The Departments entity represents different departments within the hospital, such as Cardiology, Emergency, or Pediatrics. Each department can have multiple staff members and doctors, reflected in one to many, non-identifying relationships between Departments and Staff and Departments and Doctors. These relationships are non-identifying because staffID and doctorID remain the same even if a staff member or doctor changes departments.

We chose to have separate Staff and Doctor entities because not all employees should be classified as doctors. Only doctors are associated with entities such as Appointments, MedicalRecords, and Prescriptions.

The Staff entity represents hospital employees, including nurses, administrative workers, and technicians, with job titles and department assignments. Staff schedules are captured in the StaffSchedule entity, linking staff members to shifts recorded in the Shifts entity, which includes start times, end times, and shift types. The relationship between Staff and StaffSchedule is one to many and identifying. The relationship between StaffSchedule and Shifts is also a one to many, identifying relationship. This is because each schedule record depends on both a specific staff member and a specific shift. Each staff member can appear multiple times on the schedule (one to many), and each schedule entry must be linked to exactly one staff member and one shift (identifying). Each of the schedule entities also include a shift status to show whether a shift is completed, cancelled, or active.

Similarly, the Doctors entity contains doctor names, specializations, and department assignments. Doctor shift schedules are managed through the DoctorSchedule entity, which functions identically to StaffSchedule, forming one to many, identifying relationships with both Doctors and Shifts. The Patients entity stores patient demographics, contact information, medical details (such as blood type and allergies), and links to their pharmacy and insurance information. There is a one to many, non-identifying relationship between Patients and Appointments, since each patient can have multiple appointments, but each appointment has its own identity and simply references the patient. The relationship between Doctors and Appointments is also a one to many, non-identifying relationship, as each doctor may have multiple appointments, but each appointment only points to one doctor.

The same applies to EmergencyContacts, where patients can have many emergency contacts, but said records and contacts can exist independently of the patient. Conversely, pharmacies and insurance companies also have a 1-M relationship with Patients, but they are referenced as foreign keys on the Patients entity. These firms can accommodate many patients, but each patient only needs to go to one pharmacy and be on one insurance plan. Patient medical history is stored in the MedicalRecords entity, recording diagnoses, treatments, dates, and links to the patient and doctor responsible. This is a one to many, identifying relationship between Patients and MedicalRecords because each medical record is uniquely tied to a patient and cannot exist without them. The relationship between Doctors and MedicalRecords is one to many, non-identifying, since each doctor may have multiple records associated with them, but the records are independent entities with their own primary keys. As such, the MedicalRecords entity contains patientID and doctorID as foreign keys.

The Appointments entity records reasons, dates, statuses, and links to both the doctor and patient. Billing for these appointments is tracked in the Billings entity. There is a one to many, non-identifying relationship between Appointments and Billings, as one appointment may have multiple billing records (for partial payments or adjustments), but each billing entry exists independently and only references one appointment. Prescriptions are recorded in the Prescriptions entity, with details on medication name, dosage, duration, prescribing doctor, patient, and prescription date. There is a one to many, non-identifying relationship between Patients and Prescriptions and Doctors and Prescriptions. A patient can have multiple prescriptions, and each prescription is issued by one doctor, but each prescription exists independently with its own unique ID. The Pharmacies entity stores pharmacy details. There is a one to many, non-identifying relationship between Pharmacies and Patients, as each pharmacy can serve multiple patients, but each patient is linked to only one pharmacy. The pharmacy exists independently of any patient.

The InsurancePolicies entity holds policy numbers and company details. It has a one to many, non-identifying relationship with Patients, where one insurance policy may cover multiple patients, but the policy exists independently of any single patient.

Lastly, the EmergencyContacts entity allows each patient to have multiple emergency contacts, with phone numbers, addresses, and relation types recorded. This is a one to many, non-identifying relationship, as emergency contacts can exist as independent entries linked to only one patient.

# Data Dictionary
[
](https://private-user-images.githubusercontent.com/198940325/424240598-c577dd8a-a663-45f8-aaf9-05ce2f25f982.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQwNTk4LWM1NzdkZDhhLWE2NjMtNDVmOC1hYWY5LTA1Y2UyZjI1Zjk4Mi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMTk3ZGFhMmRmMTNmZmIyOTMyNTVkYjRjMTVhMGMzYTYwODcyNjYxNTVjY2JmNjE0NmEwMjliYjEwMTJlNThiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.mTsc6_c6E0-yHRslL-8yF6nz7D7CVt7wIq3bdH6eN0k)![image](https://github.com/user-attachments/assets/518d77bd-ef97-4956-8e6b-57431ea3a2b0)

[
](https://private-user-images.githubusercontent.com/198940325/424240778-ea0ceb2e-861c-497c-859a-7eed8c483859.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQwNzc4LWVhMGNlYjJlLTg2MWMtNDk3Yy04NTlhLTdlZWQ4YzQ4Mzg1OS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lMWU3MDU3MzBmYjkyNzk2ODcyZjBlOGM3ZWRjZjAxZDhjYzg3ZmZhZDJkMmY2OGUzMTNkZmJjODc4MjZhMjA2JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.FyaU_dTgyDobQAD7Du9pLel9FTKV50EF-EMe4O6tpm0)![image](https://github.com/user-attachments/assets/439b1dfa-894a-4ba2-9e32-f4adf5ce38b2)

[
](https://private-user-images.githubusercontent.com/198940325/424240912-af2a6f21-2106-4852-a086-87dc294e2553.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQwOTEyLWFmMmE2ZjIxLTIxMDYtNDg1Mi1hMDg2LTg3ZGMyOTRlMjU1My5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03ZjdkODFmN2QyNWUyM2NiMDY3M2Q3ZDBlZjcyMDE4NDNlMmY3NGFhMGNhMDcyYWFhOGE3MThlYTExY2M4NzZjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.tQcrPBUUlvLlwj8P8_JtH878lX-wxecMv63ggzP1Wy8)![image](https://github.com/user-attachments/assets/8dd67235-9047-4567-9d5a-773098622806)

[
](https://private-user-images.githubusercontent.com/198940325/424241011-8a2406f7-29a4-41ef-a0b7-2fd1cbac5f0f.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxMDExLThhMjQwNmY3LTI5YTQtNDFlZi1hMGI3LTJmZDFjYmFjNWYwZi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jM2ViNWM3NWY4MWI1MGEwZjhjOWRiNWM4MTEzNDcyODU1ZTVkMTkxZjE2M2RkMjY3ZTFmM2UwOTIyYzgxY2M0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.5aA8xpBHyEAFVsqme8742VFstbq_P5-nQ8p7Wuvi-XY)![image](https://github.com/user-attachments/assets/35318a79-9813-45e3-9a7b-19e5332349f4)

[
](https://private-user-images.githubusercontent.com/198940325/424241385-8c3ddf93-dbd9-46d5-a176-e30a8c71bd9e.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxMzg1LThjM2RkZjkzLWRiZDktNDZkNS1hMTc2LWUzMGE4YzcxYmQ5ZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hZWRlMWMxZWYyNWJjY2Y1OWUxMmM5MDE3ZDljN2JhZDg0ZTM1YTE4NGE5MDM0NzdmMDQzYjk1ZDE1ZWY2ZTFiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.QYtpC9K5EVjRXYOMv47xTzv24eHoKpZ3TtIwoW6sZNY)![image](https://github.com/user-attachments/assets/df2b8c58-0b51-4f23-b53d-56e3e47230bd)

[
](https://private-user-images.githubusercontent.com/198940325/424241460-2987054f-1ee4-4227-93d5-0bb522cd84b6.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxNDYwLTI5ODcwNTRmLTFlZTQtNDIyNy05M2Q1LTBiYjUyMmNkODRiNi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMDk3YmFjOGIyYzI5ZDE4M2U4ZDllNTJlMzIxOWZiODU2YTIwMWYwMDQ4MzUyMGNhMWNjYjExMDkzZmM1ZDUzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.zbsv2Pb4km3sPje95sXeZKuvHAeje9r6SUcqapqIhzM)![image](https://github.com/user-attachments/assets/1f8403ea-e818-47b3-bd94-8e749382a400)

[
](https://private-user-images.githubusercontent.com/198940325/424241548-8f0054a1-d76b-457a-961c-8e5480b03817.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxNTQ4LThmMDA1NGExLWQ3NmItNDU3YS05NjFjLThlNTQ4MGIwMzgxNy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMjdjMzAyYmJlNzIyZjMwMDY1YTdjN2UxNjNmZDY0NDcxZmRmMmY0Y2FmNGQzZjAxODc0OTNjNTQzOTJkYzk2JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.QDsAxv3Dp2okir05v5dm7RgCeR0rs-6FzDkMchenptI)![image](https://github.com/user-attachments/assets/8c1baa14-7eec-4584-94dd-c3248415ce52)

[
](https://private-user-images.githubusercontent.com/198940325/424241619-d35b7872-bba6-4ba1-a566-0c39f85eacbc.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxNjE5LWQzNWI3ODcyLWJiYTYtNGJhMS1hNTY2LTBjMzlmODVlYWNiYy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kNzc1Y2I2ZGRhMjNiNzVhMGZhZjFkM2U4MWI4MTA3ZDUzNWFlYmQxNDdlZTk3YjIwZWY3ZGM1ZDkyZTE0NjVkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.gNK0VAS6jAeh2mKP9BtFZVQcpEXtJcMQjLtEXXX0Kto)![image](https://github.com/user-attachments/assets/25a39a04-2124-4253-8b55-8fcdbd5e2a11)

[
](https://private-user-images.githubusercontent.com/198940325/424241685-bdbf74f4-4a60-4641-be5b-f050af9b57b8.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxNjg1LWJkYmY3NGY0LTRhNjAtNDY0MS1iZTViLWYwNTBhZjliNTdiOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0wZDNiNTQ0ZTAwNzA5YzVlOWZkYzZiMjE5NTI3MDdiNTEyNGVhNWJiYmY1Nzk2ZGFmZjYwMjlmNjA3NmNkZmIxJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.NvadEmlBYp8cqnVFZ6s_4TPV6v6OC-L-nSSJv5dXliY)![image](https://github.com/user-attachments/assets/31ae31e4-892b-46cd-b152-430566e8f5dc)

[
](https://private-user-images.githubusercontent.com/198940325/424241724-ad20a977-44cb-4da7-b5ee-ee0f1d4c3d6e.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxNzI0LWFkMjBhOTc3LTQ0Y2ItNGRhNy1iNWVlLWVlMGYxZDRjM2Q2ZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMGFmOWYyNjA3YjdmOTA5NDEyNzIxMGQzOTJmMjdlOGUyNzgwOGUxYmNhNWJiYzlmNGU5ZDQyYjJkZjM1OGQ5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.KunpU74uNCoDMLGTXhY-4o8rqkgawyxRbQhnCYzYY80)![image](https://github.com/user-attachments/assets/6463f085-2564-4e62-b14b-2b21d66e1e3d)

[
](https://private-user-images.githubusercontent.com/198940325/424241850-c02270ed-32d6-43ac-a973-571013918dfc.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxODUwLWMwMjI3MGVkLTMyZDYtNDNhYy1hOTczLTU3MTAxMzkxOGRmYy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01NGY5OWY0NTk3YTA5YzI2ZTI2ZjZhNjM1NDg3ODhkMmYyMDM2MzA2ZTYxM2NmNDYxYzQ5MTFkZGJlOWY1NDhjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.NlFa826YMtB5HQEkw9-GrAQV9MCeuad6Soh4OrO2uuY)![image](https://github.com/user-attachments/assets/245aa436-8d5d-479f-9a8e-885a28b10b99)

[
](https://private-user-images.githubusercontent.com/198940325/424241921-f39beebe-f444-4597-a2a3-869fcebe5c91.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQxOTIxLWYzOWJlZWJlLWY0NDQtNDU5Ny1hMmEzLTg2OWZjZWJlNWM5MS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02MGIyOWNhN2NkNGQ4MzcwZTVjMmQ2ZDgzMjBlNGJhNmI2ZGE3MGNkZDA1MzE4MTQwYjQ1YzQ4ZTEyMWU0ZTk0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.UXFOykQ4eqLdd8iDIIl8CJHKEcsxXLmmG7t1uyqob7o)![image](https://github.com/user-attachments/assets/fadbd564-0b43-405b-810f-36bb547db96a)

[
](https://private-user-images.githubusercontent.com/198940325/424242007-da188559-bfbb-4c24-85f7-1d5e52229cb8.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQyMDA3LWRhMTg4NTU5LWJmYmItNGMyNC04NWY3LTFkNWU1MjIyOWNiOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yZTNmNTc2NmI0YmQ2MjFhYTY2ZmE2YjI4ZWEzYWQwNzhkN2JmNDU1YjI2MDMzMTUxMjgzYTNkY2U5NDdlM2FkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.MsuOywLXjV2LsunBlUtpn9MaxzdC3GpWhugJgNbFImU)![image](https://github.com/user-attachments/assets/b920bafe-e1d3-4504-9e4e-8348fc87a706)

[
](https://private-user-images.githubusercontent.com/198940325/424242074-51313593-9d65-4747-8d13-05d936bc91c1.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQyMDc0LTUxMzEzNTkzLTlkNjUtNDc0Ny04ZDEzLTA1ZDkzNmJjOTFjMS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05ZTNmM2MyZGZhMjE0NDk2ODZlZGRiOGNlMDQyNmI3NGY3YzY5Yzk0YjI5MzcxZDliMDlkODZlZTYxYzgxMGExJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.-M3LbEQIVKO_1owC9gVJyGD8ShNN32JL9YAy5I9jrCE)![image](https://github.com/user-attachments/assets/7f6f5f96-a909-46c0-8cdb-7a4570b902af)

[
](https://private-user-images.githubusercontent.com/198940325/424242145-9504b846-1fa5-4e1d-b966-eef54d5b00f8.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQyMTQ1LTk1MDRiODQ2LTFmYTUtNGUxZC1iOTY2LWVlZjU0ZDViMDBmOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0wY2I2Y2NhZDA0MGM4ZWFmOWEwZDIwOTQxYjFhMzE0ZmMwOWIzZjgwMWFhMDRhZjdlNTdkYWU3MjcxNzcwZTZhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.cCQSINo3pZ9OOzzNs-qkSMCd0GDrfBnHO80HXGEBRiA)![image](https://github.com/user-attachments/assets/e0f73b52-6dd2-4f3b-ab2e-d40e88ac9fa2)

[
](https://private-user-images.githubusercontent.com/198940325/424242211-1721af4a-2b24-4ecd-942e-9e38bd742be4.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQyMjExLTE3MjFhZjRhLTJiMjQtNGVjZC05NDJlLTllMzhiZDc0MmJlNC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04MGM5MThjNWVmMjkwOTNhODk2YjU4YTAyMjcwNThjMTE0ZDlmOTZiYTM4ZmM3ZGM2OTRmNzM2OTQ2ZmNmYzgxJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.COizWdgY0l5zd-Br8cI0tjWozAnx7Dn8ceDyL1WmO7M)![image](https://github.com/user-attachments/assets/9014b483-2a5a-41cf-b38f-2cd3d6dce9c9)

[
](https://private-user-images.githubusercontent.com/198940325/424242283-74062d94-9a07-461e-a9d0-22332271b6bb.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjQyMjgzLTc0MDYyZDk0LTlhMDctNDYxZS1hOWQwLTIyMzMyMjcxYjZiYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kZmUxMWM0NTFlOWM1NGQxMzhhYWIyNWE4ODA2NmYxMzBhNTU0NjQ0ODk1MzM1NmJiZWFhYThmODMwN2RjM2VkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.gH1_ozC2CCR454gWDfGqR28NM_b5VvaVrg7oIiZzR2Y)![image](https://github.com/user-attachments/assets/e61a977d-978e-4d10-825b-e6dbac1ec9c6)



# Queries

[
](https://private-user-images.githubusercontent.com/198940325/424276316-849aa4a9-184c-4385-baac-aa813dd44739.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0Mjc2MzE2LTg0OWFhNGE5LTE4NGMtNDM4NS1iYWFjLWFhODEzZGQ0NDczOS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02YTRmOWNhYzE3Yzg5ZDRkYTAyN2YyYTEyN2ZlNjU4NGExNWJjYTNjZGIwNzE5YjUyYTFlZjEzMGY0Y2VhMjVlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Pe0EwrhjkjZs875FiN1JunYR8HLXiRTUmEvwalwnPXg)![image](https://github.com/user-attachments/assets/6679db60-20ed-461b-ba71-d72835d0004a)

1. Query 1 lists the patient’s first name, last name, and their emergency contact’s name if their blood type is O negative. The results are also listed in descending order based on the patient’s last name.

[
](https://private-user-images.githubusercontent.com/198940325/424257945-e765655d-ee3e-4088-bc75-6d1f1897b19e.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjU3OTQ1LWU3NjU2NTVkLWVlM2UtNDA4OC1iYzc1LTZkMWYxODk3YjE5ZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05YzU1ODE3ODI2MWRlYTgzNTY3YTI5NzhhZDI4ZWRiMWFjODQ2Mzg0ZjU0ZTQxM2NiNTY5YzE1Mzc2YjM0ZmNhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.PGksvtN8DfAFPqE4nA5Jpu_DQXce8TsrJAIEqp4PKPg)![image](https://github.com/user-attachments/assets/27c38258-36d1-4b19-aff9-dcaf32c52a63)

Query 1 allows the hospital management system to see which of their patients has an O negative blood type. O negative is considered the “universal donor” as any individual can receive this blood type. People with O negative blood are often sought out to see if they'd be willing to donate their blood, which could potentially save hundreds of others lives.

2. Query 2 lists the patient's first and last time and their total outstanding billing amount for bills that are pending or overdue. The results are listed in descending order by the total outstanding billing amount.

[
](https://private-user-images.githubusercontent.com/198940325/424259584-18562218-1d99-43f9-9488-237ef0ebd1c7.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTQyMzUsIm5iZiI6MTc0MjM1MzkzNSwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjU5NTg0LTE4NTYyMjE4LTFkOTktNDNmOS05NDg4LTIzN2VmMGViZDFjNy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzEyMTVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05NWE3ZDE4YWZmODNlOTY3MWY1MTAzOGU3OWYxZGU5NTRmODg5YjgwNzgwMTA1OWQ1YmRhNDg3MTQyMjRhNDJjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.XmTpKzBwHMDjJjc7uLpnbZ5TT9ERlpD6YYfgM0l7GQs)![image](https://github.com/user-attachments/assets/bc4ce214-6e10-4af1-8174-81fc9a8ebb17)

Query 2 allows the staff in charge of billings to oversee how much money they are still waiting to receive from the patients in their care. Including both pending and overdue payments, the system can contact these individuals to check in on their payments and keep track of who they are owed money from.

3. Query 3 lists out the pharmacy’s name and the number of patients at each pharmacy.

[
](https://private-user-images.githubusercontent.com/198940325/424261441-07a45dc2-c191-4ee3-9b4a-c2e283bdf3db.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTUyMjIsIm5iZiI6MTc0MjM1NDkyMiwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjYxNDQxLTA3YTQ1ZGMyLWMxOTEtNGVlMy05YjRhLWMyZTI4M2JkZjNkYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzI4NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01MTAwOTk1YzFmMDBmMzkyYmI1MzFmZWQxNWY3YjQ3MjAzMjlkMjc2ZDg5MTIyNjlhMWU1MTA4YThjMmQ4MDBhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.FnOhr3_IUykycBG1DPw4WNHSrAuadK3LRJlNfr-YPos)![image](https://github.com/user-attachments/assets/e760ec6d-5986-4108-801b-63f60b9d3e0b)


Query 3 allows the billing staff to look over all of the different pharmacies that their patients are assigned to. Based on the pharmacy, they can make certain deals with the hospital if enough patients are assigned and receiving medication orders/refills. They can also maintain their business relationships with these suppliers, which will strengthen their business overal

4. Query 4 lists out the patient’s first name, last name, ID, appointment reason, and bill for their appointment if it is greater than the average billing amount in the hospital.

[
](https://private-user-images.githubusercontent.com/198940325/424262359-a19e8f30-add9-4aed-a95c-28bde17eb6ea.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTUyMjIsIm5iZiI6MTc0MjM1NDkyMiwicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjYyMzU5LWExOWU4ZjMwLWFkZDktNGFlZC1hOTVjLTI4YmRlMTdlYjZlYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzI4NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMDkwZTkwNGY2N2MzOTUxNWIxN2ZhY2IxODU2YmFkN2I5MDNkZDRjMjFiNmRhNGQ2NWIyNTg3ZmI1OTZjODMzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.8gJYF7yULTs0wvF_x2Sz1uYOryS5aitUqWOtFSMipWQ)![image](https://github.com/user-attachments/assets/9242e60a-05be-4bce-b2d5-b654e85c8a9c)

Query 4 allows the hospital billing staff to see the patient’s name, their ID number, their appointment reason, and the bill for their appointment if it is greater than the average bill amount for the hospital. This gives a general idea for the staff to see which appointments cost more than the typical average of all appointments within the hospital. This also brings forth important information such as which patients are bringing more than the average revenue from appointments, future budgeting plans, and whether or not resources need to be allocated more.

5. Query 5 lists the patients ID, first name, last name, and their phone number if they do not have any allergies, they are not a minor, and they are not taking any medications.

[
](https://private-user-images.githubusercontent.com/198940325/424278661-0cb320a6-a2eb-4562-9b0d-d7f589d7f2c8.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTU0NzcsIm5iZiI6MTc0MjM1NTE3NywicGF0aCI6Ii8xOTg5NDAzMjUvNDI0Mjc4NjYxLTBjYjMyMGE2LWEyZWItNDU2Mi05YjBkLWQ3ZjU4OWQ3ZjJjOC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzMyNTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yMzdkYjMzMzAyYzExYjdjOWQ0NmYzYzQ1NzVkN2NhYzMyZjY0ZTRlY2M3YTNjYjMxYzA5NGZjZGU2NWIxMTY5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.onPhxmkKYr06xwp85Qxkd6J5hXI2FOQWE_YDELHxElk)![image](https://github.com/user-attachments/assets/93d33526-5174-49e6-8686-265995e788ce)

Query 5 allows the hospital staff who are in charge of keeping data and improving upon the hospital itself to possibly give patients surveys and record their experiences. In order to get the best results while taking the survey, the patient must not have any allergies, must be older than 18, and not currently taking medication. They then can have a list of patients to ask if they’d be willing to take the survey and use their data to better improve the hospital.

6. Query 6 lists the doctors ID, first name, last name, and the amount of overtime hours they have worked. Overtime is considered to be above 40 hours within a working week and they will be paid time and a half.

[
](https://private-user-images.githubusercontent.com/198940325/424263557-7d1e9a04-8c11-4831-ab25-2667a8e017ba.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTU0NzcsIm5iZiI6MTc0MjM1NTE3NywicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjYzNTU3LTdkMWU5YTA0LThjMTEtNDgzMS1hYjI1LTI2NjdhOGUwMTdiYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzMyNTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xMzg5NjY2ZDI1MTBmMDNlMmYyYzdmODk4Yzc1MGUyMDg3NTMzYzUyOGMwZDVkNzZiMGI0YTUwYmU4OTkzZTA4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.5eaARsurdxQ62XzuAwRIaivPqLGTMfBJrS7rIhZWSt0)![image](https://github.com/user-attachments/assets/c92f5493-36c6-450f-9a1e-d35439da5271)

Query 6 allows the hospital staff in charge of the doctor’s payroll to see who needs to be compensated properly for any time worked above the normal 40 hours a week. If a doctor has worked more than 40 hours, then they can be paid extra money for any additional hours worked. This makes it a lot easier to see who has worked overtime and who has not.

7. Query 7 lists the names of all of the staff members such as their ID, first name, last name, job title, and department name (not including doctors) who work less than 2 night shifts.

[
](https://private-user-images.githubusercontent.com/198940325/424264070-7a2582c0-f855-4b4f-9699-087d9048640a.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTU0NzcsIm5iZiI6MTc0MjM1NTE3NywicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjY0MDcwLTdhMjU4MmMwLWY4NTUtNGI0Zi05Njk5LTA4N2Q5MDQ4NjQwYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzMyNTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xNmQ2NDhhZTU3YjgyMDg3ODAxODhiMzZjNjZiMTExZDM0ZmRkNDYyMDFlYTM4ZTU0ODhjMzE4NTYyMzM3ODQ4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.umS0rcW4J03cTA32HmUNi2zpDdbEuqnw9KrYEiHaNPs)![image](https://github.com/user-attachments/assets/b259392f-b4ac-421d-8a89-2703d6546885)

Query 7 allows any shift supervisors to see which staff members work less than 2 night shifts for a work week. Supervisors can use this to determine if there is anyone in the department that can possibly pick up more night shifts due to them working less than 2.

8. Query 8 lists the patients’ first name, last name, and medication name for each medication of those who are taking more than 1 prescription. Order by the patient’s names.

[
](https://private-user-images.githubusercontent.com/198940325/424270300-063e1aa4-ba39-421c-8a4c-b08297ba3a58.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTU0NzcsIm5iZiI6MTc0MjM1NTE3NywicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjcwMzAwLTA2M2UxYWE0LWJhMzktNDIxYy04YTRjLWIwODI5N2JhM2E1OC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzMyNTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kMjUzZGYxMDVkYmQyOTU4YTY1YjFjMTY4MDk2ODgwZjYyNDQyM2MxMDI4MWQ1ODM0NjExZWZiNWI3NGU4MDBmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Wx7hXk990_t-Iw1i9i0huiceM8b4tl_rmAdB26BtfLA)![image](https://github.com/user-attachments/assets/1406abcb-66cf-4b24-94e6-014c67912cbb)

Query 8 allows doctors to look through their patients and know which patients are taking more than one medication and the names of those medications. Taking multiple medications at the same time can increase the risk of dangerous side effects occurring, so it is very important for doctors to know what their patients are taking in order to keep their patient safe. It is also helpful in determining if the patient can take more medications based on what they are already taking.

9. Query 9 determines the distribution of insurance companies among insured patients in the hospital

[
](https://private-user-images.githubusercontent.com/198940325/424268150-e843edd0-5c20-4261-bf42-0f3e8178286c.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTU0NzcsIm5iZiI6MTc0MjM1NTE3NywicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjY4MTUwLWU4NDNlZGQwLTVjMjAtNDI2MS1iZjQyLTBmM2U4MTc4Mjg2Yy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzMyNTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xNmQ5MjYwZWM5ZDA2YjkwODNiZjM5ZWU2ZmI2ZjNjNTBlNzExZDBkNzIzZWRiZDZjNGNmYWYwY2Y0MmZkNmRiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.Z3bhB8VaQVTYhSrMAcQM7DUM1xrLlr3rhVsecXKyaEg)![image](https://github.com/user-attachments/assets/b307f829-73c5-40f0-a5c4-76f85a338a25)

Query 9 allows the hospital to understand who their top insurance providers are (in terms of patients insured). With this information, the management staff can better optimize the billing system, know the prominent insurance company among patients, and streamline the insurance process by understanding how the prominent insurance companies work. If the providers are in equal proportion, the query also sorts providers alphabetically.

10. Query 10 lists the patient’s first name, last name, age, and their diagnosis if they are born after 01/01/1997

[
](https://private-user-images.githubusercontent.com/198940325/424266164-24a0dbf0-e385-4e85-99c0-22881b4df0b2.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDIzNTU0NzcsIm5iZiI6MTc0MjM1NTE3NywicGF0aCI6Ii8xOTg5NDAzMjUvNDI0MjY2MTY0LTI0YTBkYmYwLWUzODUtNGU4NS05OWMwLTIyODgxYjRkZjBiMi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMzE5JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDMxOVQwMzMyNTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00MGNiMmEwYTI4NTNkYmQyZDczYTlmNGNhZGFlMjY1ZWQxNWZlYTc5YzE2YTNmYTgzYzdjMDYzOTJhYjYxYzFiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.ARhLbSWCTkiRApqfJjz8_EHq4jNnhwuK3Gkd4quGYn4)![image](https://github.com/user-attachments/assets/8bb177c5-d7e8-4486-bf18-b0b44ddf0e76)

Query 10 is useful for the hospital staff to relay important information to doctors on how to treat younger patients that are a part of Generation Z or Alpha. Knowing your patient’s age difference is key in helping understand them and what can be different in their treatment compared to individuals who are Millennials or Generation X.

# Database Information

Name of the database: ns_Sp25_21479_Group2

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
