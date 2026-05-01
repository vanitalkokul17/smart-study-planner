# 📚 Smart Study Planner — AI-Powered

A full-stack AI-powered study planner that helps students manage subjects, generate personalized study plans, track progress, and receive email reminders — all running locally with Docker.

---

## ✨ Features

- 🔐 **User Authentication** — Register and login with JWT-secured sessions
- 📚 **Subject Management** — Add, view and delete subjects with priority, chapters, exam date and daily hours
- 🤖 **AI Study Plan Generator** — Automatically generates a weekly timetable based on your subjects and exam dates
- 📈 **Progress Tracker** — Log study sessions with hours, chapters completed and notes
- 📊 **Dashboard Analytics** — See total sessions, hours studied, exam readiness score and grade
- 💡 **AI Recommendations** — Get personalized tips based on your study history
- 🍅 **Pomodoro Timer** — Built-in focus timer with customizable work and break durations
- 📧 **Email Notifications** — Send study reminder emails listing your real subjects and exam countdown alerts

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Gateway | Nginx (reverse proxy) |
| Services | Python (Flask) — 7 microservices |
| Database | MySQL 8 |
| Container | Docker & Docker Compose |
| Email | SMTP (Gmail) |

---

## 📁 Project Structure

```
smart-study-planner/
├── docker-compose.yml
├── .env.example
├── nginx/
│   └── nginx.conf
├── frontend/
│   └── index.html
├── mysql-init/
│   └── init.sql
└── services/
    ├── user-service/          → Register, login, JWT auth
    ├── study-plan-service/    → Subjects + AI plan generation
    ├── ai-planner-service/    → AI logic for timetable
    ├── progress-service/      → Log and view study sessions
    ├── analytics-service/     → Dashboard stats and grade
    ├── recommendation-service/→ Personalized study tips
    └── notification-service/  → Email reminders and countdowns
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have these installed:

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) — must be running before you start
- That's it! Everything else runs inside Docker.

---

### Step 1 — Clone the repository

```bash
git clone https://github.com/vanitalkokul17/smart-study-planner.git
cd smart-study-planner
```

---

### Step 2 — Create your `.env` file

Copy the example file:

```bash
cp .env.example .env
```

Then open `.env` and fill in your values:

```env
MYSQL_ROOT_PASSWORD=StudyPlanner123
JWT_SECRET=mysupersecretkey_changethis_2024

SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-gmail@gmail.com
SMTP_PASSWORD=your-16-char-app-password
FROM_EMAIL=your-gmail@gmail.com
```

#### 📧 Getting a Gmail App Password (for email features)

1. Go to your Google Account → **Security**
2. Enable **2-Step Verification** if not already on
3. Search **"App Passwords"** → Create one → Select **"Mail"**
4. Google gives you a 16-character password → paste it as `SMTP_PASSWORD`

> Email features are optional — the app works fine without them.

---

### Step 3 — Build and run

```bash
docker-compose up --build
```

The first run takes **3–5 minutes** to download and build everything.

When you see logs like:
```
ssp-nginx | ready
ssp-user-service | started successfully
```

The app is ready.

---

### Step 4 — Open the app

Open your browser and go to:

```
http://localhost
```

---

## 📖 How to Use

1. **Register** a new account with your name, email and password
2. **Login** with your credentials
3. Go to **📚 Subjects** → Add your subjects with exam dates and priority
4. Click **🤖 Generate AI Study Plan** → view your personalized weekly timetable
5. Go to **📈 Log Progress** → log your study sessions daily
6. Check **📊 Dashboard** for your stats and readiness score
7. Go to **💡 Tips** for AI recommendations based on your progress
8. Go to **🍅 Pomodoro** to use the focus timer during study sessions
9. Go to **🔔 Notifications** to send email reminders with your real subjects

---

## 🐳 Docker Commands

| Command | What it does |
|---|---|
| `docker-compose up --build` | First time build and start |
| `docker-compose up` | Start without rebuilding |
| `docker-compose up -d` | Start in background |
| `docker-compose down` | Stop all containers |
| `docker-compose down -v` | Stop and wipe the database |
| `docker-compose logs -f` | See live logs |
| `docker-compose logs user-service` | Logs for a specific service |

---

## 🔌 API Services & Ports

| Service | Internal Port | Route |
|---|---|---|
| Nginx Gateway | 80 | `http://localhost` |
| User Service | 5001 | `/api/users/` |
| Study Plan Service | 5002 | `/api/study/` |
| AI Planner Service | 5003 | `/api/ai/` |
| Progress Service | 5004 | `/api/progress/` |
| Recommendation Service | 5005 | `/api/recommendations/` |
| Notification Service | 5006 | `/api/notifications/` |
| Analytics Service | 5007 | `/api/analytics/` |

---

## 🐛 Troubleshooting

**App not opening at `http://localhost`**
→ Make sure Docker Desktop is running (whale icon in taskbar)

**A service crashes on startup**
→ MySQL takes a few seconds to be ready. Just run `docker-compose up` again.

**Email not sending**
→ Check your `SMTP_PASSWORD` is the Gmail App Password (16 chars), not your regular Gmail password.

**"Cannot connect to server" on login**
→ Run `docker-compose logs user-service` to see the error details.

**Port 80 already in use**
→ Another app is using port 80. Stop it or change the port in `docker-compose.yml`.

---

## 🔒 Security Notes

- Never commit your `.env` file — it contains passwords
- `.gitignore` already excludes `.env`
- JWT tokens expire and require re-login
- All passwords are hashed before storing in the database

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙋‍♀️ Author

Made by **vanitalkokul17**

GitHub: [https://github.com/vanitalkokul17](https://github.com/vanitalkokul17)

Here are Output Images

<img width="1920" height="1461" alt="screencapture-localhost-2026-05-02-00_19_24" src="https://github.com/user-attachments/assets/5d80d8b2-1b89-4e23-8a5e-4b8a2cd92f72" /><br/>


<img width="1920" height="2388" alt="screencapture-localhost-2026-05-02-00_19_49" src="https://github.com/user-attachments/assets/9bac1ba2-b0a0-4fb4-af5c-576cd7d618db" /><br/>


<img width="1920" height="1428" alt="screencapture-localhost-2026-05-02-00_20_41" src="https://github.com/user-attachments/assets/bc856627-6322-415f-bbeb-6cb94631dcd4" /><br/>


<img width="1920" height="1118" alt="screencapture-localhost-2026-05-02-00_21_16" src="https://github.com/user-attachments/assets/f33954a1-a99d-4853-807c-92f90e312427" /><br/>


<img width="1920" height="1632" alt="screencapture-localhost-2026-05-02-00_22_21" src="https://github.com/user-attachments/assets/36343ee5-a127-4d23-bc4a-211075cb0319" /><br/>


<img width="1920" height="1632" alt="screencapture-localhost-2026-05-02-00_23_12" src="https://github.com/user-attachments/assets/e6f51f52-f541-4525-a53c-a7a3878b0108" />



