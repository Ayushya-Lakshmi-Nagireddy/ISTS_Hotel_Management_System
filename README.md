# ISTS Hotel Management System

A web-based **Hotel Management System** developed using **Python Flask, SQLite, HTML5, CSS3, JavaScript, and Jinja2 templates**.

The application is designed to help hotel staff manage customer bookings, employees, room availability, and basic hotel operations from a single web interface.

## Project Overview

The ISTS Hotel Management System provides a centralized interface for hotel staff to:

- Register and log in securely
- View hotel statistics through a dashboard
- Add, edit, search, and delete customer booking records
- Book one or multiple rooms for a customer
- Check out customers and release their rooms
- Add, edit, search, and delete employee records
- View room availability floor by floor
- Prevent rooms that are already occupied from being selected again
- Switch between light and dark themes
- Store application data in an SQLite database

The system contains **45 rooms arranged across 5 floors, with 9 rooms on each floor**.

---

## Features

### 1. Authentication

- Staff registration
- Staff login
- Password hashing
- Session-based protected pages
- Logout functionality

### 2. Dashboard

The dashboard provides an overview of the hotel, including:

- Total customers
- Total employees
- Total rooms
- Available rooms
- Occupied rooms
- Total bookings
- Room status chart
- Recent bookings
- Quick actions

### 3. Customer Management

Customer records can be:

- Added
- Edited
- Searched
- Checked out
- Deleted

Customer information includes:

- Full name
- Email
- Phone
- Address
- Gender
- Date of birth
- ID proof type
- ID proof number
- Room number(s)
- Check-in date
- Check-out date
- Number of guests
- Booking status
- Payment status

### 4. Multiple Room Booking

A single customer booking can contain more than one room.

For example:

```text
Rooms: 507, 508
```

Available rooms can be selected during booking, while occupied rooms cannot be selected.

### 5. Room Availability

The system displays rooms floor by floor.

- Green = Available
- Red = Occupied

The hotel contains:

```text
5 Floors × 9 Rooms = 45 Rooms
```

A room remains occupied while it is associated with an active booking. When a customer checks out, the associated rooms become available again.

### 6. Employee Management

Employee records can be:

- Added
- Edited
- Searched
- Deleted

Employee information includes:

- Full name
- Email
- Phone
- Address
- Gender
- Date of birth
- Department
- Position
- Salary
- Joining date
- Employee status

### 7. Search

Customer search supports:

- Name
- Email
- Phone
- Room number

Employee search supports:

- Name
- Email
- Phone
- Department
- Position

### 8. Light and Dark Theme

The application provides both light and dark themes.

The selected theme is stored in the browser so the interface can retain the user's preference.

---

## Technologies Used

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript |
| Backend | Python 3, Flask |
| Templates | Jinja2 |
| Database | SQLite |
| Security | Werkzeug password hashing |
| Session Management | Flask Sessions |

No frontend framework is required.

---

## Database

The application uses SQLite for persistent data storage.

The main tables are:

### `users`

| Column |
|---|
| id |
| full_name |
| email |
| username |
| password_hash |
| created_at |

### `customers`

| Column |
|---|
| id |
| full_name |
| email |
| phone |
| address |
| gender |
| date_of_birth |
| id_proof_type |
| id_proof_number |
| check_in_date |
| check_out_date |
| room_number |
| number_of_guests |
| booking_status |
| payment_status |
| created_at |

### `employees`

| Column |
|---|
| id |
| full_name |
| email |
| phone |
| address |
| gender |
| date_of_birth |
| department |
| position |
| salary |
| joining_date |
| employee_status |
| created_at |

The database file is created automatically when the application is initialized.

---

## Project Structure

```text
hotel_management_system/
│
├── app.py
├── requirements.txt
│
├── database/
│   └── database.py
│
├── templates/
│   ├── base.html
│   ├── login.html
│   ├── register.html
│   ├── dashboard.html
│   ├── rooms.html
│   ├── _room_picker.html
│   ├── customers.html
│   ├── add_customer.html
│   ├── edit_customer.html
│   ├── employees.html
│   ├── add_employee.html
│   └── edit_employee.html
│
└── static/
    ├── css/
    │   └── style.css
    │
    ├── js/
    │   └── script.js
    │
    └── images/
```

---

## Application Workflow

```text
Start
  │
  ▼
Register / Login
  │
  ▼
Dashboard
  │
  ├───────────────┐
  ▼               ▼
Customers       Employees
  │               │
  ├─ Add           ├─ Add
  ├─ Edit          ├─ Edit
  ├─ Search        ├─ Search
  ├─ Check Out     └─ Delete
  └─ Delete
  │
  ▼
Room Availability
  │
  ├─ Available
  └─ Occupied
  │
  ▼
Logout
```

---

# Screenshots

The screenshots below are included in the repository under `screenshots/`.

## Login

![Login Page](screenshots/login.png)

## Registration

![Registration Page](screenshots/register.png)

## Dashboard - Light Theme

![Dashboard Light Theme](screenshots/dashboard-light.png)

## Dashboard - Dark Theme

![Dashboard Dark Theme](screenshots/dashboard-dark.png)

## Customer Management

![Customer Management](screenshots/customers.png)

## Edit Customer

![Edit Customer](screenshots/customer-edit.png)

## Employee Management

![Employee Management](screenshots/employees.png)

## Edit Employee

![Edit Employee](screenshots/employee-edit.png)

## Room Management

![Room Management](screenshots/rooms.png)

---

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/your-username/hotel-management-system.git
cd hotel-management-system
```

Replace `your-username` and the repository name with the actual GitHub repository details.

### 2. Create a virtual environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the application

```bash
python app.py
```

The Flask development server can then be opened in the browser using the local address shown by Flask, typically:

```text
http://127.0.0.1:5000/
```

---

## How to Use

### Staff Registration

1. Open the registration page.
2. Enter the staff member's details.
3. Create an account.
4. Return to the login page.

### Staff Login

1. Enter the username or email.
2. Enter the password.
3. Click **Login**.
4. The dashboard will open after successful authentication.

### Add a Customer

1. Open **Customers**.
2. Click **Add Customer**.
3. Enter customer and booking details.
4. Select the required available room or rooms.
5. Save the booking.

### Check Out a Customer

1. Open **Customers**.
2. Locate the booking.
3. Click **Check Out**.
4. The booking status changes to `Checked-out`.
5. The associated rooms become available again.

### Manage Employees

1. Open **Employees**.
2. Add a new employee or edit an existing record.
3. Use the search box to locate employees.
4. Delete records when required.

### Check Room Availability

1. Open **Rooms**.
2. View rooms grouped by floor.
3. Green rooms are available.
4. Red rooms are occupied.

---

## Room Booking Logic

The room availability logic is designed to prevent double booking.

A room is considered occupied when it belongs to an active customer booking and the booking has not been checked out or cancelled.

When a customer checks out:

```text
Booking Status → Checked-out
        ↓
Associated Rooms Released
        ↓
Rooms Become Available
```

This allows the same rooms to be used for future bookings after checkout.

---

## Security

The application uses:

- Password hashing with Werkzeug
- Session-based authentication
- Protected application pages
- Form validation

Passwords are stored as password hashes rather than plain-text passwords.

---

## Key Project Objectives

The project was developed to:

1. Build a complete hotel management web application.
2. Provide secure staff registration and login.
3. Manage customer bookings using CRUD operations.
4. Support multiple rooms in a single booking.
5. Prevent double booking of rooms.
6. Manage employee records.
7. Display hotel statistics and room availability.
8. Demonstrate Flask routing, templates, database connectivity, and CRUD operations.

---

## Future Improvements

Possible extensions for future versions include:

- Online payment integration
- Email/SMS booking notifications
- Customer invoice generation
- Reports and analytics
- Role-based access control
- Reservation history
- Export to PDF/Excel
- Automated backup and restore
- REST API integration
- Improved mobile responsiveness

---

## Project Information

**Project:** ISTS Hotel Management System

**Institution:** ISTS Women's Engineering College, Rajanagaram

**Application Type:** Web-based Hotel Management System

**Backend:** Python Flask

**Database:** SQLite

**Frontend:** HTML5, CSS3, JavaScript

---

## License

This project is intended for academic and educational purposes.

If you reuse or modify the project, please provide appropriate attribution to the original project authors.

---

## Acknowledgement

This project demonstrates practical implementation of web development concepts including:

- Flask web application development
- HTML and CSS interface design
- JavaScript-based interactions
- SQLite database management
- CRUD operations
- Authentication and sessions
- Form validation
- Room availability management
