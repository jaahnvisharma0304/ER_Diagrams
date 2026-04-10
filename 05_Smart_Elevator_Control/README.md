# Elevator Management System – ER Diagram

## Project Overview
This project represents the Entity-Relationship (ER) Diagram for an Elevator Management System. It models how different components of an elevator system interact, including buildings, floors, elevators, ride requests, assignments, and maintenance.

The goal is to design a structured database system to efficiently manage elevator operations in buildings.

---

## Entities and Description

### 1. Building
Stores building details.
- `building_id` (PK)
- `building_name`
- `address`
- `city`
- `building_type`
- `total_floors`
- `contact_person`
- `contact_phone`

---

### 2. Floor
Represents floors within a building.
- `floor_id` (PK)
- `building_id` (FK)
- `floor_number`
- `floor_label`
- `floor_type`

---

### 3. Elevator Shaft
Represents elevator shafts in a building.
- `shaft_id` (PK)
- `building_id` (FK)
- `shaft_code`
- `min_floor`
- `max_floor`

---

### 4. Elevator
Stores elevator details.
- `elevator_id` (PK)
- `shaft_id` (FK)
- `building_id` (FK)
- `elevator_code`
- `manufacturer`
- `capacity_kg`
- `capacity_persons`
- `installation_date`
- `current_status`

---

### 5. Elevator Floor
Maps elevators to floors they serve.
- `ef_id` (PK)
- `elevator_id` (FK)
- `floor_id` (FK)

---

### 6. Elevator Status Log
Tracks real-time elevator status.
- `status_log_id` (PK)
- `elevator_id` (FK)
- `status`
- `current_floor`
- `recorded_at`
- `notes`

---

### 7. Floor Request
Stores elevator requests from floors.
- `request_id` (PK)
- `floor_id` (FK)
- `building_id` (FK)
- `direction`
- `request_status`
- `requested_at`

---

### 8. Ride Assignment
Assigns elevators to requests.
- `assignment_id` (PK)
- `request_id` (FK)
- `elevator_id` (FK)
- `assigned_at`
- `assignment_status`

---

### 9. Ride Log
Stores completed ride details.
- `ride_id` (PK)
- `assignment_id` (FK)
- `elevator_id` (FK)
- `origin_floor_id` (FK)
- `destination_floor_id` (FK)
- `start_time`
- `end_time`
- `passenger_count`
- `ride_status`

---

### 10. Maintenance Record
Tracks elevator maintenance.
- `maintenance_id` (PK)
- `elevator_id` (FK)
- `maintenance_type`
- `technician_name`
- `scheduled_at`
- `started_at`
- `completed_at`
- `status`
- `remarks`

---

## Relationships

- A Building has multiple Floors  
- A Building has multiple Elevator Shafts  
- A Building has multiple Elevators  
- An Elevator Shaft can have one Elevator  
- An Elevator serves multiple Floors (via Elevator Floor)  
- An Elevator has multiple Status Logs  
- A Floor generates multiple Requests  
- A Request may be assigned to one Elevator  
- An Elevator handles multiple Assignments  
- An Assignment results in a Ride Log  
- An Elevator has multiple Maintenance Records  
