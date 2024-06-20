# HospitalManagementSystem

Hospital Management System Report
Overview
The Hospital Management System is a comprehensive application designed to streamline and manage various aspects of hospital operations. It provides distinct interfaces for different roles including Admin, Patient, Nurse, and Doctor. Additionally, the system includes a feature for generating comprehensive reports that provide insights into the hospital's operations.
Main Features
1.	User-Specific Panels
o	Patient Panel: Provides patients with access to their profiles, appointments, and medical records.
o	Doctor Panel: Enables doctors to view patient profiles, input diagnoses, prescriptions, and treatments.
Nurse Panel: Facilitates nurses in managing patient care, updating medical records, and handling patient-related tasks.
o	Admin Panel: Allows administrators to manage hospital data, including staff, departments, rooms, and billing information.
2.	Generate Reports
o	The system can generate detailed reports that summarize the total count of staff, appointments, departments, rooms, patients, and bills stored in the database. This feature is critical for administrators to get an overview of the hospital's performance and operational metrics.
Detailed Breakdown of the Main Application
Main Application Class: This serves as the entry point of the system. It sets up the primary stage and provides a main menu with buttons to navigate to different user panels and generate reports.
•	UI Setup: Uses JavaFX to create a user-friendly interface with a VBox layout that includes buttons for each panel and a report generation button.
•	Button Actions: Each button is associated with an action that opens the corresponding user panel or generates reports.
•	Report Generation: The generateReports method collects data from various tables in the database and compiles a report, displaying it in an alert dialog.





Patient Panel Report
Overview
The Patient Panel within the Hospital Management System provides patients with access to their appointments, profiles, and medical records. It is designed to empower patients by allowing them to view and manage their healthcare information efficiently.
Features
1.	View Patient Profile
o	Patients can enter their name and view their profile details including address, phone number, medical history, and ward number.
2.	View Appointments
o	Patients can see their scheduled appointments with details such as appointment ID, date/time, and the doctor's name.
3.	View Medical Records
o	Access to medical records allows patients to review their diagnosis, prescribed medications, and ongoing treatments.
4.	Add Appointment
o	Patients can request new appointments by specifying the doctor's name, appointment time, and department.

PatientDAO Class
The PatientDAO class provides methods that interact with the database to retrieve patient-related information and manage appointments.
•	Database Connection: Establishes a connection to the database upon instantiation.
•	View Patient Profile
o	Method: viewPatientProfile(String patientName)
o	Description: Retrieves the patient's profile information based on the provided name from the patients table.
o	Returned Data: Constructs and returns a Patient object containing profile details.
•	View Appointments
o	Method: viewAppointments(String patientName)
o	Description: Retrieves a list of appointments for the patient from the appointments table.
o	Returned Data: Returns a list of Appointment objects, each representing a scheduled appointment.
•	View Medical Record
o	Method: viewMedicalRecord(String patientName)
o	Description: Fetches the medical record of the patient from the medical_records table.
o	Returned Data: Returns a MedicalRecord object encapsulating diagnosis, prescription, and treatment details.
•	Add Appointment
o	Method: addAppointment(String patientName, String doctorName, Timestamp appointmentTime, String department)
o	Description: Inserts a new appointment record into the appointments table.
o	Parameters: Includes patient name, doctor name, appointment time, and department for the new appointment.
Implementation Details
•	Exception Handling: Proper handling of SQLException ensures robustness when interacting with the database.
•	Database Queries: Utilizes parameterized queries to prevent SQL injection and securely retrieve specific patient data.
Conclusion
The Patient Panel of the Hospital Management System enhances patient engagement and healthcare delivery by providing easy access to critical information and appointment scheduling. It ensures patients have control over their healthcare journey and facilitates efficient management of medical records and appointments through a user-friendly interface.

Doctor Panel
The Doctor Panel within the Hospital Management System provides doctors with essential functionalities to manage patient records and view relevant hospital data.
Features
1.	View Patient Profile
o	Doctors can search for patients by name to view detailed profiles including their address, phone number, medical history, and ward number.
o	Functionality: Utilizes the viewPatientProfile method in the DoctorDAO class to fetch patient information from the database based on the entered name.
2.	Input Diagnosis, Prescription, and Treatment
o	Doctors can input and update diagnosis, prescription, and treatment information for patients.
o	Functionality: Employs methods like inputDiagnosis, inputPrescription, and inputTreatment in the DoctorDAO class to update the respective fields in the medical_records table.
3.	Tables Display
o	Displays tables for patients, departments, and appointments to provide doctors with quick access to relevant hospital data.
o	Implementation: Utilizes TableView components in the Doctor GUI (DoctorGUI) class to populate and display data fetched from the database using the DoctorDAO methods.
Code Integration
1.	DoctorDAO Class
o	Manages database interactions specific to doctors, including fetching patient profiles, updating medical records, and retrieving data for patients, departments, and appointments.
o	Key Methods:
	viewPatientProfile: Retrieves patient details based on the provided name.
	inputDiagnosis, inputPrescription, inputTreatment: Updates medical records with diagnosis, prescription, and treatment information respectively.
	getAllPatients, getAllDepartments, getAllAppointments: Retrieves lists of patients, departments, and appointments from the database.
2.	DoctorGUI Class
o	Implements the graphical user interface for the Doctor Panel.
o	SetupUI Method:
	Configures the UI layout with components such as text fields for patient name input, buttons for actions like viewing profiles and inputting medical information (diagnosis, prescription, treatment), and table views for displaying patient, department, and appointment data.
	Event Handling: Defines actions for button clicks to trigger database operations through DoctorDAO methods, and handles exceptions with appropriate error messages.
User Interaction
The Doctor Panel enhances user interaction by providing an intuitive interface that allows doctors to efficiently manage patient care through streamlined access to medical records and hospital data. This ensures that doctors can make informed decisions and provide optimal healthcare services to patients.





NurseDAO Class
The Nurse Panel in the Hospital Management System empowers nurses to manage and update patients' medical records efficiently. This panel is facilitated by the NurseDAO class, which handles database interactions related to recording vital signs, updating patient progress, and managing diagnosis and prescription information.
Functionality
1.	Record Vital Signs
o	Method: recordVitalSigns(String patientName, String vitalSigns)
	Updates the vital signs for a specified patient in the medical records.
	Checks if the patient exists in the database before updating.
	Displays an alert indicating the success or failure of the operation.
2.	Update Patient Progress
o	Method: updatePatientProgress(String patientName, String progress)
	Updates the patient's progress notes by appending new information to the existing progress.
	Checks if the patient exists and updates the medical records accordingly.
	Notifies the nurse with an alert about the success or failure of the update operation.
3.	Update Diagnosis and Prescription
o	Method: updateDiagnosisAndPrescription(String patientName, String diagnosis, String prescription)
	Updates the diagnosis and prescription fields for a specified patient.
	Directly updates the database records without additional checks for patient existence.
	Executes the update query based on the provided patient name, diagnosis, and prescription.
4.	Add New Patient
o	Method: addNewPatient(String patientName)
	Adds a new patient to the medical records table if the patient does not already exist.
	Verifies patient existence before inserting new records into the database.
	Executes an insert query to add the new patient with the provided patient name.
5.	Check Patient Existence
o	Private Method: isPatientExists(String patientName)
	Checks if a patient exists in the medical records table based on the provided patient name.
	Executes a SELECT query to check for the existence of any records matching the patient name.
	Returns a boolean value indicating whether the patient exists (true) or not (false).
6.	Alert Handling
o	Private Method: showAlert(String message)
	Displays an alert dialog box with information messages for various operations.
	Used to inform the nurse about the outcome of database operations such as record updates or patient existence checks.
Database Interaction
•	Connection Management: The NurseDAO class establishes a connection to the database using the DatabaseConnection class, ensuring that all interactions are handled securely and efficiently.
•	Prepared Statements: Utilizes prepared statements to execute SQL queries, which enhances security and performance by parameterizing inputs and preventing SQL injection attacks.
Conclusion
The Nurse Panel and its associated NurseDAO class play a crucial role in the Hospital Management System by enabling nurses to maintain accurate and up-to-date medical records for patients. These functionalities ensure streamlined communication and collaboration among healthcare professionals, ultimately improving patient care and hospital operations.

Administrator Panel

Overview
The Administrator Panel within the Hospital Management System offers comprehensive functionality for managing patients, staff, departments, rooms, appointments, and billing. This module is crucial for administrators to maintain the hospital's operations efficiently.
Features
1.	Patient Management
o	Add Patient: Allows administrators to add new patients with details such as name, address, phone number, medical history, and ward number. The patient's medical record is automatically created upon addition.
o	Remove Patient: Enables administrators to remove patients from the system, including deletion of their corresponding medical records.
2.	Staff Management
o	Add Staff: Provides functionality to add new staff members with details like name, role, phone number, and address.
o	Remove Staff: Allows removal of staff members from the system after checking for existence.
3.	Department Management
o	Add Department: Allows administrators to create new departments with a name and description.
o	Remove Department: Provides the capability to delete existing departments.
4.	Room Management
o	Add Room: Allows addition of rooms associated with existing departments. Rooms are added with details such as room number and type.
o	Remove Room: Enables removal of rooms based on room number.
5.	Appointment Management
o	Add Appointment: Allows scheduling of appointments for patients with specific doctors at given date and time.
o	Remove Appointment: Provides functionality to cancel appointments based on the patient's name.
6.	Billing Management
o	Add Billing: Allows creation of billing records for patients, including details such as patient name, billing amount, and status (e.g., pending, paid).
o	Update Billing Status: Provides functionality to update the billing status for a patient.
Detailed Description
Patient Management
•	Add Patient: The addPatient method inserts a new patient record into the patients table and concurrently adds a corresponding entry into the medical_records table using insertMedicalRecord.
•	Remove Patient: The removePatientByName method deletes a patient's record from the patients table and also removes the associated medical record from the medical_records table using deleteMedicalRecord.
Staff Management
•	Add Staff: The addStaff method inserts a new staff member into the staff table with details such as name, role, phone number, and address.
•	Remove Staff: The removeStaffByName method deletes a staff member from the staff table after verifying their existence using isStaffExists.
Department Management
•	Add Department: The addDepartment method adds a new department with a name and description to the departments table.
•	Remove Department: The removeDepartmentByName method deletes a department from the departments table based on its name.
Room Management
•	Add Room: The addRoom method adds a new room to the rooms table, associating it with an existing department by specifying the room number, type, and department name.
•	Remove Room: The removeRoomByNumber method deletes a room from the rooms table based on its room number.
Appointment Management
•	Add Appointment: The addAppointment method schedules a new appointment for a patient with a specified doctor at a given date and time.
•	Remove Appointment: The removeAppointmentByPatientName method cancels an appointment based on the patient's name.
Billing Management
•	Add Billing: The addBilling method creates a billing record for a patient in the bills table, specifying the patient's name, billing amount, and initial status.
•	Update Billing Status: The updateBillingStatusByPatientName method updates the billing status (e.g., pending, paid) for a patient based on their name.

Conclusion
The Administrator Panel in the Hospital Management System plays a pivotal role in overseeing and managing critical aspects of hospital operations. By providing robust functionality for patient, staff, department, room, appointment, and billing management, administrators can ensure smooth and efficient hospital administration. This module enhances operational efficiency and improves patient care through systematic management of hospital resources and services.



