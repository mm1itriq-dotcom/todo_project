# Calendar To-Do Application

## Description
The Calendar To-Do Application is a web-based task management system that allows users to organize their daily tasks based on specific dates (Months and Days). Unlike a traditional endless list of to-dos, this application groups tasks chronologically. It features a secure user authentication system and ensures that every user's tasks are kept private and isolated.

## Key Features
- **User Authentication:** Secure user registration and login system. Uses `Werkzeug` for strong password hashing and enforces strict password requirements (minimum length, uppercase, lowercase, and symbols).
- **Date-Based Task Management:** Users can view, add, edit, and delete tasks for specific days of any given month.
- **Task Toggling:** Easily toggle tasks between "To-Do" and "Completed" states.
- **Data Isolation:** Uses session-based authentication to ensure users can only access and modify their own tasks.
- **Database Initialization:** The application can automatically create the required database tables (`users` and `todos`) on startup.

## Technologies Used
- **Backend:** Python 3, Flask
- **Database:** PostgreSQL
- **ORM & Migrations:** SQLAlchemy Core, Alembic
- **Frontend:** HTML, CSS, JavaScript (rendered via Jinja2 templates)
- **Security:** Werkzeug Security (password hashing), Flask Sessions

## Project Structure
- `app.py`: The main Flask application containing all routes for authentication and task management.
- `models.py`: SQLAlchemy Core definitions for the `users` and `todos` tables.
- `db.py`: Database connection settings and the `init_db()` initialization script.
- `requirements.txt`: Python dependencies required to run the project.
- `templates/` & `static/`: Frontend HTML templates and static assets (CSS/JS).
- `alembic/` & `alembic.ini`: Database migration configurations.

## Setup Instructions

### Prerequisites
- Python 3.8+
- PostgreSQL installed and running locally

### 1. Database Configuration
Ensure PostgreSQL is running and create a database named `training_db`:
```sql
CREATE DATABASE training_db;
```
*(If your Postgres credentials differ from the defaults, update the `DATABASE_URL` in `db.py` or export it as an environment variable).*

### 2. Environment Setup
Navigate to the root directory and set up a Python virtual environment:
```bash
# Navigate to the project directory
cd todo_project

# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install required dependencies
pip install -r requirements.txt
```

### 3. Initialize the Database
You can initialize the database tables either by running the `db.py` script directly or by using Alembic migrations:
```bash
# Initialize directly via SQLAlchemy Core
python db.py

# OR use Alembic (if migrations are configured)
alembic upgrade head
```

### 4. Run the Application
Start the Flask development server:
```bash
python app.py
```
The application will be accessible at `http://127.0.0.1:5000`.

## How It Works
1. Navigate to the local URL. If you aren't logged in, you will be redirected to the **Login** screen.
2. Create a new account using the **Register** page. Make sure your password meets the required security standards.
3. Once logged in, you will be directed to the **Dashboard**. 
4. The dashboard defaults to the current month and day. Use the date selectors to navigate to a different date.
5. You can now add new tasks, edit existing task titles, check them off as completed, or delete them entirely for the selected day.