# Online Fitness Coaching Platform ER Diagram

##  Overview

This project represents the **Entity Relationship (ER) Diagram** for an online fitness coaching platform.
The system is designed for fitness influencers/trainers who manage clients digitally through coaching plans, consultations, and progress tracking.

---

##  Objective

To design a database structure that supports:

* Trainer and client management
* Fitness plans and subscriptions
* Session scheduling (consultations & live training)
* Progress tracking through check-ins
* Payment handling

---

##  Core Entities

###  User

Stores basic information for both trainers and clients.

* `user_id (PK)`
* name, email, password, role

###  Trainer Profile

* `trainer_id (PK, FK)`
* bio, experience, specialization

###  Client Profile

* `client_id (PK, FK)`
* age, height, fitness goals

---

##  Plans & Subscriptions

###  Plan

Created by trainers to offer coaching services.

* `plan_id (PK)`
* trainer_id (FK)
* name, price, duration, type

###  Subscription

Tracks which client purchased which plan.

* `subscription_id (PK)`
* client_id (FK)
* plan_id (FK)
* start_date, end_date, status

---

##  Payments

### Payment

Stores transaction details.

* `payment_id (PK)`
* subscription_id (FK)
* amount, method, status

---

##  Sessions

### Session

Handles consultations and live training.

* `session_id (PK)`
* trainer_id (FK)
* client_id (FK)
* scheduled_at, type, status

---

##  Progress Tracking

### Check-In

Submitted regularly by clients.

* `checkin_id (PK)`
* client_id (FK)
* date, notes

### Progress

Stores measurable fitness data.

* `progress_id (PK)`
* checkin_id (FK)
* weight, measurements

### Trainer Notes

Feedback given by trainers.

* `note_id (PK)`
* checkin_id (FK)
* trainer_id (FK)
* note_text

---

##  Relationships

* One trainer can manage many clients
* One trainer can create multiple plans
* One client can purchase multiple plans over time
* Many clients can enroll in the same plan
* One subscription can have multiple payments
* Sessions can be linked to subscriptions or be standalone
* Each check-in is linked to progress and trainer feedback

