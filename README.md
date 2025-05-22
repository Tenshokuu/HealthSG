


# HealthySG – Healthcare Management Simulation
--- 

Caleb Tinonas
EGL301 – Assignment 1




HealthySG.js is a Node.js module that simulates a basic healthcare system. It allows patient registration, appointment booking and cancellation, and simple billing functions including grant support and partial payments.

---

## Features

- Patient registration  
- Appointment booking and cancellation  
- View appointments by NRIC  
- Pay bills (full, partial, or with grant)  
- View outstanding bills  

---

## How to Use

### 1. Requirements

- Node.js (any stable version)

### 2. Setup

1. Save the module as `HealthySG.js`
2. Create a test file called `app.js` in the same directory
3. Add the following code in `app.js` to test:

```javascript
const healthySG = require("./HealthySG");

console.log(healthySG.registerPatient("T1234567Z", "Jane Doe", "91111222", "1985-09-20", "789 clementi ave 3"));
console.log(healthySG.bookAppointment("T1234567Z", "2025-06-10", "10:00", "dr. lim"));
console.log(healthySG.getAPTbyNRIC("T1234567Z"));
console.log(healthySG.payDaBill("S7654321B", 70));
console.log(healthySG.payDaBill("S7654321B", 0, true));
console.log(healthySG.billsbyNRIC("S7654321B"));
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
{
  nric: "S1234567A",
  fullName: "caleb tinonas",
  phone: "91234567",
  dob: "1993-01-01",
  address: "123 orchard road"
}
```

### Appointment

```js
{
  appointmentId: "APTNO1",
  nric: "S1234567A",
  appointmentDate: "2025-06-01",
  appointmentTime: "09:00",
  doctor: "dr. lim"
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



