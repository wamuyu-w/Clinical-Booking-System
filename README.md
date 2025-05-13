# Clinical-Booking-System -  a relational database developed using **MySQL** to manage core clinic activities. 
# It supports:
- Management of doctors and their specializations
- Registration of patients and their demographic details
- Scheduling and tracking of appointments
- Issuing and tracking of prescriptions
- Recording of medications prescribed to patients

The system is built with referential integrity, normalization, and efficient relationships (1:1, 1:N, M:N) to reflect real-world clinic operations.
---

## 🛠️ How to Run / Setup the Project

### ✅ Prerequisites
- **MySQL** installed (Download: https://dev.mysql.com/)
- A database client like:
  - MySQL CLI
  - MySQL Workbench
  - phpMyAdmin

### ✅ Steps to Setup

1. **Create the Database**
   ```sql
    CREATE DATABASE ClinicBookingSystem;
    USE ClinicBookingSystem;
