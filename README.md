# 🎯 Job Shikari — AI-Powered Automated Job Hunting System

![n8n](https://img.shields.io/badge/n8n-workflow-orange)
![Gemini](https://img.shields.io/badge/Google-Gemini_AI-blue)
![Docker](https://img.shields.io/badge/Docker-deployed-blue)
![Telegram](https://img.shields.io/badge/Telegram-notifications-blue)

## 📌 Overview
Job Shikari is a fully automated AI-powered job hunting pipeline 
that scrapes LinkedIn every 24 hours, scores jobs against your 
resume using Google Gemini AI, generates personalized cover 
letters, and sends Telegram notifications for best matches.

## ✨ Features
- 🔍 Scrapes 20 LinkedIn jobs every 24 hours (4 pages)
- 🤖 AI-powered resume-job matching (score 0-100)
- ✍️ Auto-generates personalized cover letters
- 📊 Saves all results to Google Sheets
- 📱 Telegram notifications for jobs scoring ≥ 50
- 🔄 Duplicate job detection
- 🐳 Docker deployment with ngrok

## 🛠️ Tech Stack
| Technology | Purpose |
|---|---|
| n8n | Workflow automation |
| Google Gemini 2.5 Flash | AI scoring + cover letters |
| Google Drive API | Resume storage |
| Google Sheets API | Preferences + results |
| Telegram Bot API | Notifications |
| Docker | Deployment |
| JavaScript | URL builder + JSON parser |

## 🏗️ System Architecture
```
Schedule Trigger (24hrs)
    ↓
Google Drive → Resume PDF
Google Sheets → Job Preferences
    ↓
LinkedIn URL Builder (JavaScript)
    ↓
HTTP Request → Scrape 20 Jobs (4 pages)
    ↓
Loop Over Each Job
    ↓
Duplicate Check → Skip if exists
    ↓
Gemini AI → Score (0-100) + Cover Letter
    ↓
Google Sheets → Save Results
    ↓
If Score ≥ 50 → Telegram Notification
```

## 🚀 Setup Instructions

### Prerequisites
- Docker Desktop
- n8n (self-hosted)
- Google Cloud Account
- Telegram Bot Token
- Google Gemini API Key

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/job-shikari-ai
cd job-shikari-ai
```

### 2. Start n8n with Docker
```bash
docker-compose up -d
```

### 3. Import Workflow
- Open n8n at `http://localhost:5678`
- Import `workflow.json`
- Configure all credentials

### 4. Configure Google Sheets
Add these columns to your preferences sheet:
- Keyword, Location, Experience Level
- Remote, Job Type, Easy Apply

### 5. Start ngrok
```bash
ngrok http 5***
```

## ⚙️ Environment Variables
```env
N8N_BASIC_AUTH_USER=admin(use yours)
N8N_BASIC_AUTH_PASSWORD=yourpassword(what are you looking at)
GEMINI_API_KEY=your_key(again...)
TELEGRAM_BOT_TOKEN=your_token(tch.. tch... ok take this "3Bx9WWD6umbNd1rD8frwO_842p_ChU4ti7ya_3Hok7ya")
```

## 📸 Screenshots
<img width="859" height="355" alt="image" src="https://github.com/user-attachments/assets/e43ae6fa-b6e9-4d0e-85c0-b1c63f8ce947" />


## 🔮 Future Scope
- Multi-platform scraping (Naukri, Indeed)
- Resume auto-optimization
- Interview scheduler
- Analytics dashboard


## 📄 License
MIT License
