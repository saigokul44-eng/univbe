# 🎯 UniVibe — Find Your People

A university social matching web app. Answer 15 questions about your sports, projects, music, goals, and personality — get matched with 5 people who share your vibe!

## ✨ Features
- 🔐 User Registration & Login (session-based)
- 🎯 15-question quiz (sports, tech, music, movies, goals, personality + more)
- 🤝 Top 5 vibe matches using answer similarity algorithm
- 📊 Match score with shared interests display
- 👤 Profile page showing full quiz answers
- 🎨 Dark mode, animated UI with Bootstrap 5

## 🛠️ Tech Stack
- **Backend:** Python Flask + SQLite
- **Frontend:** Bootstrap 5, HTML5, CSS3, Vanilla JS
- **Fonts:** Syne (headers) + DM Sans (body) via Google Fonts
- **No AI, No paid APIs required**

## 🚀 Setup & Run

```bash
# 1. Clone or extract the project folder
cd univibe

# 2. Create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the app
python app.py
```

Visit **http://localhost:5000** in your browser.

## � Production Deployment on Render

### ⚠️ Important Notes
- **Database Limitation**: This app uses SQLite which works fine on Render's persistent disk. Data persists between deployments.
- For high-traffic production, consider switching to PostgreSQL.

### Deployment Steps

1. **Create a Render Account**:
   - Go to [render.com](https://render.com) and sign up
   - Connect your GitHub account

2. **Deploy from GitHub**:
   - Push this project to a GitHub repository
   - In Render dashboard, click "New +" → "Web Service"
   - Connect your GitHub repo
   - Configure the service:
     - **Runtime**: Python 3
     - **Build Command**: `pip install -r requirements.txt`
     - **Start Command**: `python app.py`
   - Add environment variable: `FLASK_ENV=production`
   - Click "Create Web Service"

3. **Alternative: Manual Deploy**:
   - Use the `render.yaml` file in this repo
   - Run: `render deploy` (if you have Render CLI installed)

Your app will be live at a `.onrender.com` URL!

### For Production Database (Optional)
- Sign up for a free PostgreSQL database (e.g., Neon.tech, Supabase)
- Update `app.py` to use PostgreSQL instead of SQLite
- Add `psycopg2-binary` to requirements.txt

## �📁 Project Structure
```
univibe/
├── app.py                  # Flask app, routes, matching algorithm
├── requirements.txt├── render.yaml             # Render deployment configuration├── univibe.db              # SQLite DB (auto-created on first run)
├── templates/
│   ├── base.html           # Navbar + layout
│   ├── index.html          # Landing page
│   ├── login.html
│   ├── register.html
│   ├── dashboard.html
│   ├── quiz.html           # 15-question quiz form
│   ├── results.html        # Top 5 matches display
│   └── profile.html        # User profile with answers
└── static/
    └── css/
        └── style.css       # Full dark theme stylesheet
```

## 🎯 How Matching Works
1. Each user's 15 answers are stored as a JSON object in SQLite.
2. When you view results, your answers are compared against all other users.
3. For each pair of answers to the same question, a match counts if both answers are identical.
4. Score = (matched answers / total answered questions) × 100.
5. Top 5 highest-scoring users are returned as your matches.

## 📋 Quiz Questions Cover
1. Favourite sport to watch (dropdown with 15 options)
2. Favourite sport to play (dropdown)
3. Type of projects (Web Dev, ML, Cybersecurity, etc.)
4. Preferred tech stack / language
5. Music genre
6. Movies / Series preference
7. Study style
8. Free time activities
9. Campus club preference
10. Career goals (5-year vision)
11. Personality type
12. Food preferences
13. Travel destination type
14. Social style
15. What matters most in life

## 💡 Tips
- Register at least 2-3 test accounts and complete the quiz with each to see matches.
- The more users take the quiz, the better the matches get.
- Retake the quiz anytime — it updates your answers.
