-- Clinic Appointments Project
-- You: Isha Nepal
-- This file shows basic SQL skills (table design, inserts, queries)

-- 1. Create a table for patients
CREATE TABLE Patients (
    patient_id   INTEGER PRIMARY KEY,
    first_name   VARCHAR(50),
    last_name    VARCHAR(50),
    date_of_birth DATE,
    phone        VARCHAR(20)
);

-- 2. Create a table for appointments
CREATE TABLE Appointments (
    appointment_id INTEGER PRIMARY KEY,
    patient_id     INTEGER,
    appointment_date DATE,
    reason         VARCHAR(100),
    status         VARCHAR(20),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id)
);

-- 3. Insert some sample data
INSERT INTO Patients (patient_id, first_name, last_name, date_of_birth, phone)
VALUES
(1, 'Ava', 'Lopez', '1995-02-10', '555-111-2222'),
(2, 'Noah', 'Singh', '1990-07-25', '555-333-4444'),
(3, 'Mia', 'Chen', '1988-11-05', '555-555-6666');

INSERT INTO Appointments (appointment_id, patient_id, appointment_date, reason, status)
VALUES
(101, 1, '2025-01-10', 'Routine cleaning', 'Completed'),
(102, 2, '2025-01-12', 'Follow-up exam', 'Scheduled'),
(103, 3, '2025-01-15', 'Tooth pain', 'Cancelled');

-- 4. Example queries

-- a) See all patients
SELECT * FROM Patients;

-- b) See all upcoming appointments
SELECT *
FROM Appointments
WHERE status = 'Scheduled';

-- c) Join patients with their appointments
SELECT
    p.first_name,
    p.last_name,
    a.appointment_date,
    a.reason,
    a.status
FROM Patients p
JOIN Appointments a
    ON p.patient_id = a.patient_id;
