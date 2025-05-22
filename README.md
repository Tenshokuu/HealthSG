**Caleb Tinonas**
EGL301 – Assignment 1

# 🏥 HealthySG – Clinic System Simulator


**HealthySG.js** is a simple Node.js module that simulates a basic clinic system. It helps you register patients, book or cancel appointments, and handle billing – including grants and partial payments.

> 💬 *"Be healthy, everyone!"*

---

## ✅ What You Can Do

* Register new patients
* Book and cancel appointments
* View a patient’s appointments
* Make bill payments (full, partial, or with grants)
* Check outstanding bills

---

## 🛠️ Getting Started

### 1. Requirements

* Node.js (LTS version is best)

### 2. File Setup

1. Save your module file as `HealthySG.js`.
2. Create a file called `app.js` in the same folder.
3. Add this sample code to try out the system:

```js
const healthySG = require("./HealthySG");

// Register a patient
console.log(healthySG.registerPatient("T1234567Z", "Jane Doe", "91111222", "1985-09-20", "789 Clementi Ave 3"));

// Book an appointment
console.log(healthySG.bookAppointment("T1234567Z", "2025-06-10", "10:00", "Dr. Lim"));

// View appointments
console.log(healthySG.getAPTbyNRIC("T1234567Z"));

// Make a partial payment
console.log(healthySG.payDaBill("S7654321B", 70));

// Apply for a grant
console.log(healthySG.payDaBill("S7654321B", 0, true));

// View outstanding bills
console.log(healthySG.billsbyNRIC("S7654321B"));

// Cancel an appointment
console.log(healthySG.cancelAppointment("APTNO2"));
```

### 3. Run the App

```bash
node app.js
```

---

## 🧩 Functions Explained

### `registerPatient(nric, name, phone, dob, address)`

Adds a new patient if they’re not already registered.

### `bookAppointment(nric, date, time, doctor)`

Books a new appointment and auto-generates an appointment ID.

### `getAPTbyNRIC(nric)`

Shows all appointments for a patient.

### `payDaBill(nric, amount, grant = false)`

Handles bill payments:

* Pay fully or partially
* Optionally apply for a grant (marks bill as "in progress")

### `cancelAppointment(appointmentId)`

Cancels an appointment using its ID.

### `billsbyNRIC(nric)`

Shows unpaid or partially paid bills. If everything is paid, it says so!

---

## 🧾 Sample Data

### Patient

```js
{
  nric: "S1234567A",
  fullName: "Caleb Tinonas",
  phone: "91234567",
  dob: "1993-01-01",
  address: "123 Orchard Road"
}
```

### Appointment

```js
{
  appointmentId: "APTNO1",
  nric: "S1234567A",
  appointmentDate: "2025-06-01",
  appointmentTime: "09:00",
  doctor: "Dr. Lim"
}
```

### Bill

```js
{
  nric: "S7654321B",
  totalAmount: 150,
  paidAmount: 50,
  status: "partial"
}
```

---

## 💡 Notes

* Appointment IDs are auto-created (e.g., `APTNO6`).
* Each payment updates the bill automatically.
* Grant requests don’t reduce the amount but change the status to `"in progress"`.


---

## 🔗 Useful Links

* [HealthHub Singapore](https://www.healthhub.sg/)
* [Zocdoc – Appointment Booking](https://www.zocdoc.com/)
* Special thanks to ChatGPT for guidance.

---

Let me know if you'd like to make it even more visual or turn it into a GitHub-style README!
