# Vangari Mama  — Trash Collection Marketplace

A Flask-based web application that connects waste generators with local collectors. Users can post trash for pickup, collectors can accept and complete jobs, and everyone can track progress through clean dashboards. The system includes role-based access, authentication, and a points-based rewards model.

## Features

- **User Registration**: Sign up as either a User (waste generator) or Collector
- **Trash Posting**: Users can post trash details with location for collection
- **Collection Management**: Collectors can browse, accept, and complete pickups
- **Reward System**: Earn points based on trash type and quantity
- **Real-time Dashboard**: Track posts, earnings, and collection status
- **Responsive Design**: Works on desktop and mobile devices

## Tech Stack

- **Backend**: Flask (Python)
- **Database**: PostgreSQL with SQLAlchemy
- **Frontend**: Bootstrap 5 with dark theme
- **Authentication**: Flask-Login
- **Icons**: Font Awesome 6

## Local Development Setup (VS Code)

### Prerequisites

- Python 3.11+
- PostgreSQL
- VS Code

## Quick Start

### 1) Clone and set up a virtual environment
```bash
git clone https://github.com/your-username/vangari-mama.git
cd vangari-mama
python -m venv venv
# Linux/Mac
source venv/bin/activate
# Windows
# venv\Scripts\activate
```

### 2) Install dependencies
```bash
pip install -r requirements_for_vscode.txt
```

### 3) Configure environment
Copy the sample and adjust values:
```bash
cp .env.example .env
```
Key variables you will see in `.env.example`:
```
DATABASE_URL=postgresql://username:password@localhost:5432/scrapmama
PGHOST=localhost
PGPORT=5432
PGUSER=username
PGPASSWORD=password
PGDATABASE=scrapmama

SESSION_SECRET=your-secret-key-here
FLASK_ENV=development
FLASK_DEBUG=True
```

> Note: If you prefer SQLite for local development, you can set `DATABASE_URL=sqlite:///instance/database.db` and ensure the `instance/` folder exists.

### 4) Initialize the database
```bash
flask db init        # only once for a new repo
flask db migrate -m "initial"
flask db upgrade
```

### 5) Run the application

Option A — via Flask CLI:
```bash
export FLASK_APP=main.py      # Windows (Powershell): $env:FLASK_APP="main.py"
export FLASK_ENV=development  # optional
flask run
```

Option B — run the entry script directly:
```bash
python main.py
```

The app serves on `http://127.0.0.1:5000/` by default.

## Project Structure

```
vangari-mama/
├─ app.py                 # Flask app factory and extensions
├─ main.py                # App entrypoint (runs the server)
├─ routes.py              # Routes, views, and controller logic
├─ models.py              # SQLAlchemy models
├─ forms.py               # Flask-WTF forms
├─ admin.py               # Admin utilities and views
├─ instance/
│  └─ database.db         # SQLite DB (if used locally)
├─ migrations/            # Alembic migration scripts
├─ templates/             # Jinja2 HTML templates
├─ static/
│  ├─ css/custom.css
│  └─ js/main.js
├─ requirements_for_vscode.txt
├─ pyproject.toml
├─ .env.example
└─ README.md
```

## Common Tasks

- Create a new migration after changing models:
  ```bash
  flask db migrate -m "describe your change"
  flask db upgrade
  ```

- Create an admin user (example snippet to run in a Python shell):
  ```python
  from app import app, db
  from models import User
  with app.app_context():
      u = User(username="admin", email="admin@example.com", role="admin")
      u.set_password("change-me")
      db.session.add(u)
      db.session.commit()
  ```

## Testing

You can use any Python test framework (pytest/unittest). A simple pattern:
```bash
pip install pytest
pytest -q
```

## Deployment Notes

- Set a strong `SESSION_SECRET` in production
- Use a managed PostgreSQL database and set `DATABASE_URL`
- Run migrations during deploy: `flask db upgrade`
- Use a production server such as Gunicorn:
  ```bash
  gunicorn -w 4 -b 0.0.0.0:8000 main:app
  ```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes with clear messages
4. Add/update tests where appropriate
5. Open a pull request

## License

This project is open source and available under the MIT License."# VangariMama"
