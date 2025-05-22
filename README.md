Here is a **fully copy-pasteable `README.md` file** for your `HealthySG.js` project. It is clean, detailed, and follows best practices for student submissions:

````markdown
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
````

### 3. Run the app

```bash
node app.js
```

---

## 🧠 Module Functions

### `registerPatient(nric, fullName, phone, dob, address)`

Registers a patient if not already registered.

### `bookAppointment(nric, appointmentDate, appointmentTime, doctor)`

Creates a new appointment. Generates an automatic `appointmentId`.

### `getAPTbyNRIC(nric)`

Returns all appointments for the given NRIC. If none, returns an error message.

### `payDaBill(nric, amount, Grant = false)`

Processes bill payments. Supports:

* Full or partial payments
* Grant application (marks bill as "in progress")

### `cancelAppointment(appointmentId)`

Removes an appointment based on its ID.

### `billsbyNRIC(nric)`

Displays all unpaid or partially paid bills for a patient. Returns a success message if all bills are settled.

---

## 📁 Sample Data Overview

### 🧍 Patients

```js
{
  nric: "S1234567A",
  fullName: "caleb tinonas",
  phone: "91234567",
  dob: "1993-01-01",
  address: "123 orchard road"
}
```

### 🩺 Appointments

```js
{
  appointmentId: "APTNO1",
  nric: "S1234567A",
  appointmentDate: "2025-06-01",
  appointmentTime: "09:00",
  doctor: "dr. lim"
}
```

### 💰 Bills

```js
{
  nric: "S7654321B",
  totalAmount: 150,
  paidAmount: 50,
  status: "partial"
}
```

---

## 🗒️ Notes

* Each new appointment generates a unique ID like `APTNO6`.
* Bills are updated automatically with each payment.
* Grant applications don’t change paidAmount but change bill status to `"in progress"`.

---

## 🙋 Author

**Caleb Tinonas**
EGL301 – NTU Healthcare System Simulation (2025)

---

## 📚 References

* Carousell-style Object Management from Course Examples
* Guardian / Watsons UX Inspiration
* Node.js Docs – [https://nodejs.org](https://nodejs.org)
* ChatGPT Guidance – Payment Simulation & Design Logic

```

Let me know if you'd like me to create a demo or test version of `app.js` with even more sample cases!
```
