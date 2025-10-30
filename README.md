```markdown
# SMART EXIT - GatePass Management System

SMART EXIT is a student gatepass management system that enables CBIT students to register, apply for leaves, and receive approvals securely. The system is built using the MERN stack, MongoDB Atlas for cloud database storage, and Nodemailer (Gmail App Password) for OTP verification.

---

## Technologies Used

- Node.js
- Express.js
- MongoDB Atlas (Cloud Database)
- Mongoose (MongoDB ODM)
- Nodemailer (Gmail App for OTP)
- React.js (Frontend)
- Python (optional for future integration)

---

## Project Structure
```

/client React.js frontend
/server Node.js + Express backend
Server.js Entry point of backend server
app.py Python server

````

---

## Database Setup: MongoDB Atlas

1. Create a free cluster on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
2. Create a Database named `GatePass_DB`.
3. Inside the database, create two Collections:
   - `StudentRegisters_db` for storing student registration details.
   - `StudentGatePass_db` for storing leave application records.
4. Similarly create the faculty and Security collections
5. Replace the placeholder in `Server.js` with your actual MongoDB URI connection string.

Example:
```javascript
const MONGODB_URI = 'your-mongodb-atlas-connection-string';
````

---

## Email Setup: Gmail App Password

1. Go to Google Account settings and enable 2-Step Verification.
2. Under "Security," create an App Password for "Mail".
3. Update the following fields inside `Server.js`:

```javascript
const EMAIL_USER = "your-email@gmail.com";
const EMAIL_PASS = "your-app-password";
```

---

## Running the Project

### 1. Running the Client (React Application)

```bash
cd client
npm install
npm start
```

This will start the React client at `http://localhost:3000`.

---

### 2. Running the Server (Node.js + Express)

```bash
cd server
npm install
node Server.js
```

This will start the backend server at `http://localhost:5000` or your specified PORT.

---

### 3. Running the Python Server (Tetrolet Transformations)

```bash
cd server
pip install -r requirements.txt
set FLASK_APP=app.py
flask run
```

---

## Available APIs

| Method | Endpoint                | Description                                                   |
| :----: | :---------------------- | :------------------------------------------------------------ |
|  POST  | `/StudentRegister`      | Register a student and send OTP to email.                     |
|  POST  | `/StudentVerify`        | Verify OTP and save the student record.                       |
|  POST  | `/StudentLogin`         | Authenticate a student using email and password.              |
|  GET   | `/StudentPage/:rollNo`  | Retrieve student profile data using roll number.              |
|  POST  | `/StudentLeave`         | Submit a new leave application.                               |
|  GET   | `/StudentLeave/:rollNo` | Retrieve all leave applications for a specific student.       |
|  PUT   | `/StudentLeave/:rollNo` | Update the status of a leave application (approved/rejected). |

---

## Environment Variables Setup

It is recommended to create a `.env` file in the `server` folder with the following content:

```
MONGODB_URI=your-mongodb-atlas-connection-string
EMAIL_USER=your-email-address
EMAIL_PASS=your-app-password
PORT=5000
```

Make sure you add the `.env` file to `.gitignore` to avoid exposing sensitive information.

---

## Important Notes

- CORS is enabled for cross-origin communication between frontend and backend.
- Body-parser middleware is used for parsing JSON request bodies.
- OTPs are temporarily stored in server memory; for production, a more secure caching solution like Redis should be used.
- MongoDB indexes should be used for better performance when scaling.
- Sensitive data must never be hardcoded inside the source files.

---
