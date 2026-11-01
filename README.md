# SOFTWARE-ENGRIEERING-
doctors = ["Dr. Sharma", "Dr. Verma", "Dr. Singh"]

appointments = []

def book_appointment():
    name = input("Enter patient name: ")
    contact = input("Enter contact number: ")

    print("\nAvailable Doctors:")
    for i, doctor in enumerate(doctors, 1):
        print(i, doctor)

    choice = int(input("Select doctor (1-3): "))

    if choice < 1 or choice > 3:
        print("Invalid doctor selection!")
        return

    slot = input("Enter appointment time: ")

    # Check slot availability
    for appointment in appointments:
        if appointment["doctor"] == doctors[choice-1] and appointment["slot"] == slot:
            print("Sorry! Slot already booked.")
            return

    appointments.append({
        "patient": name,
        "contact": contact,
        "doctor": doctors[choice-1],
        "slot": slot
    })

    print("\nAppointment Booked Successfully!")
    print("Patient:", name)
    print("Doctor:", doctors[choice-1])
    print("Time:", slot)


while True:
    print("\n--- HOSPITAL APPOINTMENT SYSTEM ---")
    print("1. Book Appointment")
    print("2. View Appointments")
    print("3. Exit")

    choice = input("Enter choice: ")

    if choice == "1":
        book_appointment()

    elif choice == "2":
        for a in appointments:
            print(a)

    elif choice == "3":
        print("Thank you!")
        break

    else:
        print("Invalid choice!")
