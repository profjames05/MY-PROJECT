# University of Energy and Natural Resources - Student Attendance Tracker

A complete student attendance tracking system for the University of Energy and Natural Resources (UENR) with a Node.js/Express backend and SQLite database.

## Features

- **Student Module**
  - User registration and login
  - Attendance submission with course selection (IT, Computer Science, Biological Science, Hospitality Management)
  - Status tracking (Present, Absent, Excused Absence)
  - Class time selection

- **Admin Module**
  - Dashboard with statistics (total students, records, present/absent today)
  - View all attendance records
  - Filter records by course, status, and student name
  - Track individual student activities
  - Real-time data from database

- **Database**
  - SQLite database for persistent data storage
  - Encrypted password storage (bcryptjs)
  - Complete attendance history
  - Student and admin account management

## Project Structure

```
Attendance_Tracker/
├── index.html          # Main HTML file
├── styles.css          # CSS styling
├── script.js           # Frontend JavaScript with API calls
├── server.js           # Node.js/Express backend server
├── package.json        # Node.js dependencies
├── attendance.db       # SQLite database (auto-created)
└── README.md          # This file
```

## Installation

### Step 1: Install Node.js
Download and install Node.js from https://nodejs.org/ (LTS version recommended)

### Step 2: Install Dependencies

Navigate to the project folder and run:

```bash
npm install
```

This will install:
- **express**: Web framework for Node.js
- **sqlite3**: SQLite database driver
- **bcryptjs**: Password encryption
- **cors**: Cross-Origin Resource Sharing
- **body-parser**: JSON parsing middleware
- **nodemon**: Auto-restart on file changes (development)

## Running the Application

### Step 1: Start the Server

```bash
npm start
```

Or with auto-reload during development:

```bash
npm run dev
```

The server will start on `http://localhost:3000`

### Step 2: Open the Application

1. Open your web browser
2. Go to `http://localhost:3000`

## Default Admin Credentials

The system automatically creates a default admin account:
- **Email**: admin@admin.com
- **Password**: admin123

**Important**: Change these credentials after first login!

## API Endpoints

### Authentication
- `POST /api/auth/login/student` - Student login
- `POST /api/auth/login/admin` - Admin login
- `POST /api/auth/signup/student` - Student registration
- `POST /api/auth/signup/admin` - Admin registration

### Attendance
- `POST /api/attendance/submit` - Submit attendance record
- `GET /api/attendance/all` - Get all records

### Admin Dashboard
- `GET /api/admin/stats` - Get dashboard statistics
- `GET /api/admin/recent` - Get recent 10 records
- `GET /api/admin/filter` - Filter records by course/status/name
- `GET /api/admin/students` - Get list of all students
- `GET /api/admin/student-activity/:studentName` - Get specific student's records

## Database Schema

### Students Table
```sql
id (INTEGER, Primary Key)
name (TEXT)
email (TEXT, UNIQUE)
password (TEXT, encrypted)
created_at (DATETIME)
```

### Admins Table
```sql
id (INTEGER, Primary Key)
name (TEXT)
email (TEXT, UNIQUE)
password (TEXT, encrypted)
created_at (DATETIME)
```

### Attendance Records Table
```sql
id (INTEGER, Primary Key)
student_id (INTEGER, Foreign Key)
student_name (TEXT)
email (TEXT)
index_number (TEXT)
course_offering (TEXT)
attendance_status (TEXT)
class_time (TEXT)
submitted_at (DATETIME)
date (DATE)
```

## Usage

### For Students
1. Click "Student" role (default)
2. Sign up with your name, email, and password
3. Log in with your credentials
4. Select an index number, course, attendance status, and class time
5. Submit attendance

### For Admin
1. Click "Admin" role
2. Sign up as admin or use default admin account
3. Log in with admin credentials
4. View dashboard statistics
5. Check all records
6. View individual student activities
7. Apply filters to search records

## Features Highlights

✅ **Persistent Database Storage** - All data saved permanently in SQLite
✅ **Secure Authentication** - Passwords encrypted with bcryptjs
✅ **Separate Student & Admin Roles** - Different interfaces for each role
✅ **Advanced Filtering** - Search by course, status, and student name
✅ **Real-time Statistics** - Live dashboard with attendance counts
✅ **Responsive Design** - Works on desktop and mobile devices
✅ **REST API** - Clean API structure for future expansion

## Troubleshooting

### Server won't start
- Make sure Node.js is installed: `node --version`
- Make sure the port 3000 is not in use
- Check for error messages in the console

### Can't access the application
- Make sure the server is running
- Use `http://localhost:3000` (not HTTPS)
- Check browser console for errors (F12)

### Database errors
- The `attendance.db` file should be auto-created
- If deleted, restart the server to recreate it
- Make sure you have write permissions in the project folder

## Security Notes

⚠️ **Production Deployment**: 
- Change default admin credentials
- Use environment variables for sensitive data
- Implement rate limiting
- Use HTTPS in production
- Add input validation
- Implement JWT tokens for better security

## Future Enhancements

- User profile management
- Export reports to CSV/PDF
- Email notifications
- SMS alerts for absences
- Mobile app integration
- Multi-factor authentication
- Role-based access control (RBAC)
- Database backup automation

## Support

For issues or questions, please check the browser console (F12) and server logs for error messages.

---

**Version**: 1.0.0
**Created**: April 2026
