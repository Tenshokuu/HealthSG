// HealthySG.js
//BE HEALTHY EVERYONE !!

// array to contain the data of patients (simulates patient records stored in a database)
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

// array to contain the data of appointments (stores all appointments)
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

// array to contain the data of bill records (fake billing information)
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

module.exports = {

    // register a new patient if they haven't already
    registerPatient: function (nric, fullName, phone, dob, address) {
        const found = patients.find(patient => patient.nric === nric);
        if (found) {
            return "patient has already registered.";
        }
        // add new patient to the list
        patients.push({
            nric,
            fullName,
            phone,
            dob,
            address
        });
        return "patient has been registered successfully. :)";
    },

    // book a new appointment for a registered patient
    bookAppointment: function (nric, appointmentDate, appointmentTime, doctor) {
        // check if the patient exists
        const patient = patients.find(patient => patient.nric === nric);
        if (!patient) {
            return "patient not found. please register first before booking an appointment.";
        }

        // create a new appointment id based on total number of appointments
        const appointmentID = `APTNO${appointments.length + 1}`;

        // add appointment details
        appointments.push({
            appointmentId: appointmentID,
            nric,
            appointmentDate,
            appointmentTime,
            doctor
        });

        return `appointment booked successfully. appointment id: ${appointmentID} on ${appointmentDate} at ${appointmentTime} with dr. ${doctor}`;
    },

    // get all appointments for a patient using their nric
    getAPTbyNRIC(nric) {
        const patientAppointments = appointments.filter(apt => apt.nric === nric);
        if (patientAppointments.length > 0) {
            return patientAppointments; // return list of appointments
        } else {
            return { error: "error retrieving appointments", message: "no appointments found for NRIC: " + nric };
        }
    },

    // pay the bill for a patient or check if a grant is being applied
    payDaBill: function (nric, amount, Grant = false) {
        // find the bill by nric
        const bill = Bills.find(bill => bill.nric === nric);
        if (!bill) {
            return "no bill found for this patient.";
        }

        // if already paid, do nothing
        if (bill.status === "paid") {
            return "the bill is already fully paid.";
        }

        // apply a grant (government or subsidy)
        if (Grant) {
            bill.status = "in progress";
            return `a grant is being applied. your bill is currently : '${bill.status}'.`;
        }

        // normal payment process
        bill.paidAmount += amount;

        // if paid in full or more, mark as paid
        if (bill.paidAmount >= bill.totalAmount) {
            bill.status = "paid";
            bill.paidAmount = bill.totalAmount; // avoid overpaying
            return "bill fully paid. thank you! ;)";
        } else {
            // still has balance
            bill.status = "partial";
            return `partial payment made. amount paid: $${bill.paidAmount.toFixed(2)}. remaining: $${(bill.totalAmount - bill.paidAmount).toFixed(2)}. please remember to pay the remaining amount.`;
        }
    },

    // cancel an appointment using the appointment id
    cancelAppointment(appointmentId) {
        const index = appointments.findIndex(apt => apt.appointmentId === appointmentId);
        if (index > -1) {
            // remove appointment from the list
            appointments.splice(index, 1);
            return `appointment ${appointmentId} has been cancelled.`;
        } else {
            return "error: no appointment with that id is found.";
        }
    },

    // view all bills for a patient
    // if all bills are paid, show a success message
    billsbyNRIC(nric) {
        const DBill = Bills.filter(bill => bill.nric === nric);

        // if no bills exist
        if (DBill.length === 0) {
            return "no bills found for this nric.";
        }

        // filter bills that are not fully paid
        const partialunpaid = DBill.filter(bills => bills.status !== "paid");

        // all bills are settled
        if (partialunpaid.length === 0) {
            return "no more bills to pay. all bills are settled! ;)";
        }

        // return details of unpaid/partial bills
        return partialunpaid.map(bill => ({
            totalAmount: `$${bill.totalAmount}`,
            paidAmount: `$${bill.paidAmount}`,
            status: bill.status
        }));
    }

};
