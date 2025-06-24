# -Flask-Code-Challenge-Late-Show-API
🌙 Late Show API

A Flask RESTful API for managing guests, episodes, and appearances on a late-night TV show.

PROJECT STRUCTURE:

.
├── server/
│   ├── app.py
│   ├── config.py
│   ├── seed.py
│   ├── models/
│   │   ├── __init__.py
│   │   ├── guest.py
│   │   ├── episode.py
│   │   ├── appearance.py
│   │   └── user.py
│   ├── controllers/
│   │   ├── __init__.py
│   │   ├── guest_controller.py
│   │   ├── episode_controller.py
│   │   ├── appearance_controller.py
│   │   └── auth_controller.py
├── migrations/
├── challenge-4-lateshow.postman_collection.json
└── README.md

FEATURES:

- MVC Architecture
- PostgreSQL Database
- JWT Authentication
- RESTful Endpoints
- Cascade Deletes on Relationships
- Fully tested with Postman
- Seed script included

SETUP INSTRUCTIONS:

1. Clone the repository

git clone https://github.com/<your-username>/late-show-api-challenge.git
cd late-show-api-challenge

2. Install dependencies

pipenv install flask flask_sqlalchemy flask_migrate flask-jwt-extended psycopg2-binary
pipenv shell

3. Set up PostgreSQL

Create the database in psql:

CREATE DATABASE late_show_db;

Then in server/config.py:

SQLALCHEMY_DATABASE_URI = "postgresql://<user>:<password>@localhost:5432/late_show_db"

Replace <user> and <password> with your actual credentials.

4. Database Migration & Seeding

export FLASK_APP=server/app.py
flask db init
flask db migrate -m "Initial migration"
flask db upgrade
python server/seed.py

AUTHENTICATION FLOW:

- POST /register → create a new user
- POST /login → receive a JWT token
- Include the token in the header for protected routes:
  Authorization: Bearer <your_token>

RUNNING THE APP:

flask run
App runs at: http://127.0.0.1:5000/

API ROUTES:

/register (POST)         → Register a new user [No Auth]
/login (POST)            → Login and get JWT token [No Auth]
/episodes (GET)          → List all episodes [No Auth]
/episodes/<id> (GET)     → Get episode + appearances [No Auth]
/episodes/<id> (DELETE)  → Delete an episode and appearances [Auth]
/guests (GET)            → List all guests [No Auth]
/appearances (POST)      → Create new appearance [Auth]

POSTMAN TESTING:

1. Import challenge-4-lateshow.postman_collection.json into Postman
2. Register and login to get JWT token
3. Add token to Authorization header:
   Authorization: Bearer <token>

TECH STACK:

- Python 3.8
- Flask
- Flask-SQLAlchemy
- Flask-Migrate
- Flask-JWT-Extended
- PostgreSQL
- Postman
- Git + GitHub

.gitignore CONTENTS:

__pycache__/
*.pyc
*.db
.env
*.sqlite3
migrations/
Pipfile.lock

LIVE DEPLOYMENT (OPTIONAL):

Live API: https://your-api-url.com (replace with actual URL if deployed)

AUTHOR:

Vincent Murithi — Junior Full-Stack Developer  
Email: vincent4431murithi@gmail.com  
GitHub: https://github.com/<your-username>

SUBMISSION CHECKLIST:

[x] MVC Folder structure
[x] PostgreSQL used (No SQLite)
[x] Models and validations complete
[x] JWT Auth implemented
[x] Seed data working
[x] Routes tested in Postman
[x] Complete README
[x] GitHub repo pushed

