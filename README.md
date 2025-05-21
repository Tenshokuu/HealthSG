# GL301 Healthcare System Simulation

A Node.js module simulating a healthcare management system. It handles patient registration, appointment booking, and bill payment (including grants and partial payments).

---

## Features

✅ Patient Registration  
✅ Appointment Booking and Cancellation  
✅ Payment Processing (Full, Partial, and Grant Support)  
✅ Data Retrieval and Status Tracking

---

## Prerequisites

- [Node.js](https://nodejs.org/en) (Latest LTS version recommended)

---

## Setup Instructions

1. Download or clone the project.
2. Save the module file as `healthcare_system.js`.
3. Create an `app.js` file in the same directory.
4. Add the following sample code to `app.js`:

```javascript
const healthcare = require("./healthcare_system");

// Register a patient
healthcare.registerPatient("S1234567A", "John Doe", 30, "M");

// Book an appointment
healthcare.bookAppointment("S1234567A", "2025-06-01T10:00");

// View all appointments
console.log("All Appointments:");
console.log(healthcare.getAllAppointments());

// Pay the bill (partial with grant)
healthcare.payBill("S1234567A", 50, 20); // $50 paid, $20 grant

// View payment status
console.log("Payment Status:");
console.log(healthcare.getPaymentStatus("S1234567A"));

// Cancel an appointment
healthcare.cancelAppointment("S1234567A", "2025-06-01T10:00");
In your terminal, run:

bash
Copy
Edit
node app.js
API Reference
registerPatient(nric, name, age, gender)
Registers a new patient with the given NRIC.

bookAppointment(nric, datetime)
Books an appointment for a patient on the specified datetime (YYYY-MM-DDTHH:mm format).

getAllAppointments()
Returns a list of all scheduled appointments.

cancelAppointment(nric, datetime)
Cancels the specified appointment for the patient.

payBill(nric, amountPaid, grant)
Processes a payment. Accepts partial payments and applies a grant if provided.

getPaymentStatus(nric)
Returns the current payment status (Paid, Unpaid, or Partially Paid) for the given NRIC.

Data Structures
Patients
js
Copy
Edit
{
  nric: "S1234567A",
  name: "John Doe",
  age: 30,
  gender: "M",
  bill: 100,         // Default charge per visit
  paid: 50,          // Amount paid so far
  grant: 20          // Grant/discount applied
}
Appointments
js
Copy
Edit
{
  nric: "S1234567A",
  datetime: "2025-06-01T10:00"
}
Notes
The NRIC is used as the unique patient identifier.

You can pay bills over time or all at once.

If the total (paid + grant) equals the bill, status becomes "Paid".

References
Carousell Order Management Node Module – Assignment Reference

Watsons, Guardian & Unity – Healthcare Process Inspiration

ChatGPT (2025, May 21) – Payment Simulation Design Help

Node.js Documentation – https://nodejs.org
