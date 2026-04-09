#  Clinic Management System – ER Diagram

##  Overview

This project represents the **Entity Relationship (ER) Diagram** for a modern clinic system.
The system manages doctors, patients, appointments, consultations, diagnostic tests, reports, and payments in a structured and scalable way.

---

##  Objective

To design a database that supports:

* Appointment booking and tracking
* Patient consultations (visits)
* Diagnostic test prescriptions
* Report generation
* Payment handling (including partial and test-wise payments)

---

##  Core Entities

###  Patient

* `patient_id (PK)`
* name, age, gender, contact details

###  Doctor

* `doctor_id (PK)`
* name, experience, contact details

###  Specialty

* `specialty_id (PK)`
* name
* `doctor_id (FK)`

---

##  Appointment

Stores booking details before an actual visit.

* `appointment_id (PK)`
* patient_id (FK)
* doctor_id (FK)
* scheduled_at
* status

---

##  Consultation

Represents the actual doctor visit.

* `consultation_id (PK)`
* appointment_id (FK, optional)
* patient_id (FK)
* doctor_id (FK)
* consultation_date
* diagnosis
* consultation_fee

---

##  Diagnostic Tests

### Diagnostic_Test (Master)

* `test_id (PK)`
* name, description, cost

### Prescribed_Test

* `prescribed_test_id (PK)`
* consultation_id (FK)
* test_id (FK)
* status

---

##  Report

Generated after test completion.

* `report_id (PK)`
* prescribed_test_id (FK)
* result_summary
* report_file

---

##  Payments

### Payment

* `payment_id (PK)`
* patient_id (FK)
* payment_date
* status

### Payment_Item

* `payment_item_id (PK)`
* payment_id (FK)
* consultation_id (FK, optional)
* prescribed_test_id (FK, optional)
* amount

---

##  Relationships Summary

* One patient can have multiple appointments and consultations
* One doctor can attend multiple patients
* One appointment may or may not result in a consultation
* One consultation can have multiple prescribed tests
* Each prescribed test may generate one report
* One payment can include multiple payment items
* Payment items can be linked to consultation or individual tests
