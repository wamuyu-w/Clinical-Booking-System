# Clinical-Booking-System   
This is a relational database developed using **MySQL** to manage core clinic activities. 
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
- **MySQL** 
- A database client like MySQL Workbench
  
Alternatively,you can import it either via CLI or GUI (adding it directly to workbench)

### ✅ Steps to Setup

1. **Create the Database**
   ```sql
    CREATE DATABASE ClinicBookingSystem;
    USE ClinicBookingSystem;

1. **Create the tables**
   ```sql
    CREATE TABLE Specializations (
    specialization_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE
    );

    -- Create Doctors table
    CREATE TABLE Doctors (
      doctor_id INT AUTO_INCREMENT PRIMARY KEY,
      full_name VARCHAR(100) NOT NULL,
      email VARCHAR(100) NOT NULL UNIQUE,
      phone VARCHAR(15),
      specialization_id INT,
      FOREIGN KEY (specialization_id) REFERENCES Specializations(specialization_id)
    );

    -- Create Patients table
    CREATE TABLE Patients (
      patient_id INT AUTO_INCREMENT PRIMARY KEY,
      full_name VARCHAR(100) NOT NULL,
      dob DATE NOT NULL,
      gender ENUM('Male', 'Female', 'Other') NOT NULL,
      phone VARCHAR(15) UNIQUE,
      email VARCHAR(100) UNIQUE
    );

    -- Create Appointments table
    CREATE TABLE Appointments (
      appointment_id INT AUTO_INCREMENT PRIMARY KEY,
      patient_id INT NOT NULL,
      doctor_id INT NOT NULL,
      appointment_date DATE NOT NULL,
      appointment_time TIME NOT NULL,
      status ENUM('Scheduled', 'Completed', 'Cancelled') DEFAULT 'Scheduled',
      FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
      FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
    );

    -- Create Medications table
    CREATE TABLE Medications (
      medication_id INT AUTO_INCREMENT PRIMARY KEY,
      name VARCHAR(100) NOT NULL UNIQUE,
      description TEXT
      );

    -- Create Prescriptions table
    CREATE TABLE Prescriptions (
      prescription_id INT AUTO_INCREMENT PRIMARY KEY,
      appointment_id INT NOT NULL,
      medication_id INT NOT NULL,
      dosage VARCHAR(50),
      instructions TEXT,
      FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id),
      FOREIGN KEY (medication_id) REFERENCES Medications(medication_id)
    );
