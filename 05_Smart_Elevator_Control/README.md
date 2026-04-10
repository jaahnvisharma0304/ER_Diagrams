# Parking Management System – ER Diagram

## Project Overview
This project represents the Entity-Relationship (ER) Diagram for a Parking Management System. It models how different components of a parking system interact, including vehicles, parking spots, sessions, payments, and access control.

The goal is to design a structured database system that efficiently manages parking operations.

---

## Entities and Description

### 1. Vehicle Category
Stores types of vehicles.
- `category_id` (PK)
- `category_name`
- `description`

### 2. Vehicle
Stores vehicle details.
- `vehicle_id` (PK)
- `license_plate`
- `owner_name`
- `owner_contact`
- `category_id` (FK)

---

### 3. Parking Zone
Represents different parking areas.
- `zone_id` (PK)
- `zone_name`
- `zone_code`
- `total_levels`

### 4. Parking Level
Represents levels within a zone.
- `level_id` (PK)
- `zone_id` (FK)
- `level_number`
- `level_label`

---

### 5. Spot Category
Defines types of parking spots.
- `spot_category_id` (PK)
- `category_name`
- `access_type`
- `description`

### 6. Parking Spot
Represents individual parking spots.
- `spot_id` (PK)
- `level_id` (FK)
- `spot_category_id` (FK)
- `spot_code`
- `is_available`
- `is_reserved`

---

### 7. Parking Session
Tracks parking activity.
- `session_id` (PK)
- `vehicle_id` (FK)
- `spot_id` (FK)
- `entry_time`
- `exit_time`
- `status`

---

### 8. Parking Ticket
Generated for each session.
- `ticket_id` (PK)
- `session_id` (FK)
- `ticket_number`
- `issued_at`
- `issued_by`

---

### 9. Payment
Handles payment details.
- `payment_id` (PK)
- `session_id` (FK)
- `amount`
- `payment_method`
- `payment_status`
- `paid_at`

---

### 10. Access Category
Defines access permissions.
- `access_id` (PK)
- `access_name`
- `description`

### 11. Vehicle Access
Maps vehicles to access rights.
- `va_id` (PK)
- `vehicle_id` (FK)
- `access_id` (FK)
- `valid_date`

---

## Relationships

- A Vehicle Category classifies multiple Vehicles  
- A Vehicle can have multiple Parking Sessions  
- A Parking Zone contains multiple Levels  
- A Level contains multiple Parking Spots  
- A Spot Category defines types of Parking Spots  
- A Parking Spot is used in Parking Sessions  
- A Parking Session generates a Ticket  
- A Parking Session is settled by a Payment  
- A Vehicle is granted access via Vehicle Access  
