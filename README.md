# HealthySG – Healthcare Management Simulation

**HealthySG.js** is a Node.js module simulating core healthcare operations for a fictional clinic system. It includes functionalities like patient registration, appointment management, and a basic billing system with support for grants and partial payments.

> 💡 *“BE HEALTHY EVERYONE!!”*

---

## 📦 Features

- ✅ Patient Registration  
- ✅ Appointment Booking & Cancellation  
- ✅ View Appointments by NRIC  
- ✅ Bill Payment Handling (Full, Partial, with Grant Support)  
- ✅ View Outstanding Bills by NRIC  

---

## ⚙️ How to Use

### 1. Requirements

- Node.js (LTS recommended)

### 2. File Setup

- Save the main module file as `HealthySG.js`.
- Create a file called `app.js` in the same directory.
- Add the following code in `app.js` to test the system:

```javascript
const healthySG = require("./HealthySG");

// Register a new patient
console.log(healthySG.registerPatient("T1234567Z", "Jane Doe", "91111222", "1985-09-20", "789 clementi ave 3"));

// Book an appointment
console.log(healthySG.bookAppointment("T1234567Z", "2025-06-10", "10:00", "dr. lim"));

// View appointments
console.log(healthySG.getAPTbyNRIC("T1234567Z"));

// Pay a bill partially
console.log(healthySG.payDaBill("S7654321B", 70));

// Apply a grant
console.log(healthySG.payDaBill("S7654321B", 0, true));

// View bills
console.log(healthySG.billsbyNRIC("S7654321B"));

// Cancel an appointment
console.log(healthySG.cancelAppointment("APTNO2"));
