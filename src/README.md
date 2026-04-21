# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teacher login/logout (admin mode)
- Teachers can sign up students for activities
- Teachers can unregister students from activities
- Students can still view activities and participants in read-only mode

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| GET    | `/auth/status`                                                    | Get current authentication status                                   |
| POST   | `/auth/login`                                                     | Log in as teacher                                                   |
| POST   | `/auth/logout`                                                    | Log out current teacher session                                     |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Register a student (teacher-only)                                   |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student (teacher-only)                                 |

## Teacher Credentials

Teacher usernames and passwords are stored in `teachers.json`.

Default demo accounts:

- Username: `mrs.johnson` / Password: `teach123`
- Username: `mr.lee` / Password: `classroom456`

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
