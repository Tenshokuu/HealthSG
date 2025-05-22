


# HealthySG – Healthcare Management Simulation
Caleb Tinonas
EGL301 – Assignment 1
--- 

HealthySG.js is a Node.js module that simulates a basic healthcare system. It allows patient registration, appointment booking and cancellation, and simple billing functions including grant support and partial payments.

---
## Features

### Patient Management

**Register New Patients**  
Add new patients to the system using their NRIC and personal details.

**Duplicate Check**  
Prevents duplicate registrations by checking existing NRICs.

### Appointment Management

**Book Appointments**  
Schedule appointments for registered patients with specified doctors, dates, and times.

**Automatic Appointment IDs**  
Generates unique appointment IDs (e.g., APTNO1, APTNO2) for each new booking.

**Cancel Appointments**  
Allows patients to cancel appointments using their appointment ID.

**View Appointments by NRIC**  
Retrieves all appointments associated with a specific NRIC.

### Billing System

**Bill Tracking**  
Stores total amount, paid amount, and status (unpaid, partial, paid) for each patient.

**Partial and Full Payment**  
Supports both full and partial bill payments.

**Grant Application**  
Allows patients to apply for a grant, marking the bill as "in progress".

**Bill Summary by NRIC**  
Displays all outstanding bills for a patient or confirms if all are settled.

---

## How to Use

### 1. Requirements

- Node.js

### 2. Setup

1. Save the module as `HealthySG.js`
2. Create a test file called `app.js` in the same directory
3. Add the following code in `app.js` to test:

```javascript
const healthySG = require("./HealthySG");

// Register a new patient who is not already in the system
console.log(healthySG.registerPatient("T1234567Z", "Jane Doe", "91111222", "1985-09-20", "789 clementi ave 3"));

// Book an appointment for the newly registered patient
console.log(healthySG.bookAppointment("T1234567Z", "2025-06-10", "10:00", "dr. lim"));

// Retrieve and display all appointments made by this patient's NRIC
console.log(healthySG.getAPTbyNRIC("T1234567Z"));

// Make a partial bill payment for an existing patient
console.log(healthySG.payDaBill("S7654321B", 70));

// Apply a government grant to the same patient's bill (status set to "in progress")
console.log(healthySG.payDaBill("S7654321B", 0, true));

// View the current billing status for the patient
console.log(healthySG.billsbyNRIC("S7654321B"));

// Cancel an existing appointment by its appointment ID
console.log(healthySG.cancelAppointment("APTNO2"));

````

### 3. Run the App

```bash
node app.js
```

---

## Module Functions

### registerPatient(nric, fullName, phone, dob, address)

Registers a patient if they are not already in the system.

### bookAppointment(nric, appointmentDate, appointmentTime, doctor)

Books an appointment for a registered patient and assigns a new appointment ID.

### getAPTbyNRIC(nric)

Returns all appointments linked to a patient's NRIC.

### payDaBill(nric, amount, Grant = false)

Handles bill payment:

* Adds to paid amount
* If a grant is applied, marks the bill as "in progress"

### cancelAppointment(appointmentId)

Cancels an appointment by appointment ID.

### billsbyNRIC(nric)

Displays unpaid or partially paid bills. Returns a confirmation if all bills are fully paid.

---

## Sample Data

### Patient

```js
const patients = [
    {
        nric: "S1234567A",
        fullName: "caleb tinonas",
        phone: "91234567",
        dob: "1993-01-01",
        address: "123 orchard road"
    },
    {
        nric: "S7654321B",
        fullName: "zoe bethel",
        phone: "98765432",
        dob: "1978-05-15",
        address: "456 bukit timah road"
    },
    {
        nric: "12938401C",
        fullName: "nicholas sim jun yong",
        phone: "90123145",
        dob: "1990-12-13",
        address: "322 serangoon road"
    }
];
```

### Appointment

```js
const appointments = [
    {
        appointmentId: "APTNO1",
        nric: "S1234567A",
        appointmentDate: "2025-06-01",
        appointmentTime: "09:00",
        doctor: "dr. lim"
    },
    {
        appointmentId: "APTNO2",
        nric: "S7654321B",
        appointmentDate: "2025-06-02",
        appointmentTime: "10:30",
        doctor: "dr. tan"
    },
    {
        appointmentId: "APTNO3",
        nric: "12938401C",
        appointmentDate: "2025-06-03",
        appointmentTime: "14:00",
        doctor: "dr. ong"
    },
    {
        appointmentId: "APTNO4",
        nric: "S1234567A",
        appointmentDate: "2025-06-04",
        appointmentTime: "11:00",
        doctor: "dr. lee"
    },
    {
        appointmentId: "APTNO5",
        nric: "S7654321B",
        appointmentDate: "2025-06-05",
        appointmentTime: "15:30",
        doctor: "dr. tan"
    }
];
```

### Bill

```js
const Bills = [
    {
        nric: "S1234567A",
        totalAmount: 100,
        paidAmount: 0,
        status: "unpaid"
    },
    {
        nric: "S7654321B",
        totalAmount: 150,
        paidAmount: 50,
        status: "partial"
    },
    {
        nric: "12938401C",
        totalAmount: 200,
        paidAmount: 200,
        status: "paid"
    }
];
```

---

## Notes

* Appointment IDs are auto-generated in the format APTNO1, APTNO2, etc.
* Grant applications do not reduce the bill amount but update the status to "in progress".
* Bill status updates automatically based on total paid.

---


## References


* https://www.healthhub.sg/
* https://www.zocdoc.com/
* ChatGPT for the development of the sample data

:) saranghaeyo
```



