# Clinic Appointment Booking System

A web-based clinic appointment management system developed using Next.js, React, Prisma, and SQLite.

The system supports three user roles: patients, doctors, and receptionists. It provides user authentication, appointment booking, appointment management, and medical consultation notes.

## 1. Technologies Used

- Next.js – Application framework
- React – User interface
- JavaScript – Application programming
- Tailwind CSS – Styling
- Prisma ORM – Database management
- SQLite – Database
- bcryptjs – Password hashing
- jose – JWT authentication
- Zod – Input validation
- Node.js – Runtime environment

## 2. Main Features

### User Authentication
- Patient registration.
- Login for patients, doctors, and receptionists.
- Password hashing using bcryptjs.
- JWT-based session management.
- HTTP-only session cookies.

### Patient Features
- Patient dashboard.
- View personal appointments.
- Book appointments with registered doctors.
- Submit appointment reasons.

### Doctor Features
- Doctor dashboard.
- View assigned appointments.
- Record and update medical consultation notes.
- Access protected consultation notes page.

### Receptionist Features
- Receptionist dashboard.
- View clinic appointments.
- View associated patient and doctor information.

## 3. Security Features

The application implements several foundational security controls:

- Password hashing using bcryptjs with a cost factor of 12.
- JWT session authentication using jose.
- HTTP-only cookies.
- Role-based access control.
- Server-side user verification.
- Appointment ownership verification.
- Input validation using Zod.
- Protected API endpoints.
- Security headers to help prevent clickjacking and MIME-type sniffing.

## 4. Project Structure

```text
clinic-system/
│
├── app/
│   ├── api/
│   │   ├── appointments/
│   │   │   └── route.js
│   │   ├── doctors/
│   │   │   └── route.js
│   │   ├── login/
│   │   │   └── route.js
│   │   ├── notes/
│   │   │   └── route.js
│   │   └── register/
│   │       └── route.js
│   │
│   ├── doctor/
│   │   ├── notes/
│   │   │   ├── page.js
│   │   │   └── NotesForm.js
│   │   └── page.js
│   │
│   ├── patient/
│   │   ├── book/
│   │   │   └── page.js
│   │   └── page.js
│   │
│   ├── receptionist/
│   │   └── page.js
│   │
│   ├── login/
│   │   └── page.js
│   │
│   ├── register/
│   │   └── page.js
│   │
│   └── page.js
│
├── lib/
│   ├── auth.js
│   └── prisma.js
│
├── prisma/
│   ├── schema.prisma
│   └── seed.js
│
├── .env
├── next.config.ts
├── package.json
└── README.md
```

*Note: This is the intended structure based on the implemented features. Your actual project may contain additional files.*

## 5. Installation and Setup

### Requirements

Install the following:

- Node.js
- npm
- Visual Studio Code

### Step 1: Clone or download the project

Open the project folder in Visual Studio Code.

### Step 2: Install dependencies

Open the terminal inside the project directory and run:

```bash
npm install
```

### Step 3: Configure environment variables

Create a `.env` file in the project root directory.

Add:

```env
DATABASE_URL="file:./dev.db"
SESSION_SECRET="replace-with-a-long-random-secret"
```

Use a strong, randomly generated session secret of at least 32 characters.

Never commit the `.env` file or expose the session secret publicly.

### Step 4: Set up the database

Run:

```bash
npx prisma migrate dev
```

Generate the Prisma client if necessary:

```bash
npx prisma generate
```

### Step 5: Create test accounts

Run:

```bash
node prisma/seed.js
```

This creates development test accounts for the three user roles.

### Step 6: Start the application

Run:

```bash
npm run dev
```

Open your browser and visit:

```text
http://localhost:3000
```

## 6. Development Test Accounts

The following accounts are created by the development seed script.

| Role | Email | Password |
|---|---|---|
| Patient | trev@clinic.com | Clinic123! |
| Doctor | Collins@clinic.com | Clinic123! |
| Receptionist | Abaho@clinic.com | Clinic123! |

**Important:** These are development-only credentials. They must not be used in a production environment.

## 7. Database Models

The application currently contains three main Prisma models:

- **User:** Stores user information, roles, and hashed passwords.
- **Appointment:** Stores appointment dates, reasons, statuses, and patient/doctor relationships.
- **MedicalNote:** Stores consultation notes associated with appointments.

## 8. Testing

Manual functional checks have been performed during development.

The following features have been verified:

- User registration and login.
- Role-based dashboard access.
- Patient appointment booking.
- Appointment listing for patients.
- Appointment listing for doctors.
- Appointment listing for receptionists.
- Medical consultation note submission.
- Doctor-only access to the consultation notes page.
- Authorization checks on selected API endpoints.
- Application startup after security header configuration.

Formal static analysis, OWASP ZAP testing, and comprehensive penetration testing have not yet been completed.

## 9. Known Limitations and Future Improvements

The following improvements are still required:

1. Implement login rate limiting.
2. Add appropriate CSRF protection.
3. Implement security audit logging.
4. Add receptionist appointment booking with patient selection.
5. Implement appointment cancellation and status management.
6. Improve appointment scheduling and conflict prevention.
7. Perform static security analysis using Semgrep.
8. Perform dynamic security testing using OWASP ZAP.
9. Complete STRIDE threat modelling.
10. Prepare a Data Flow Diagram.
11. Complete the final security assessment and documentation.

## 10. Project Status

The project currently has a functional prototype with:

- Three user roles.
- User authentication.
- Appointment booking.
- Role-specific dashboards.
- Medical consultation notes.
- Foundational application security controls.

Further development and security testing are required before production deployment.

---

**Project:** Clinic Appointment Booking System  
**Framework:** Next.js  
**Database:** SQLite  
**ORM:** Prisma