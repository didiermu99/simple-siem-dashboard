# 🛡️ Simple SIEM Dashboard

A beginner-friendly Python web app to display and monitor suspicious activity (like failed logins) from log files.

## 🚀 Features
- Parses log files (e.g., `auth.log`) for suspicious events
- Displays failed login attempts by IP on a web dashboard
- Easy to expand for more events

## 🛠️ Requirements
- Python 3.x
- Flask

## ⏳ Usage

1. Install Flask if not already:
   ```bash
   pip install flask
   ```
2. Place your log file in the `sample_logs` folder (or use the provided sample).
3. Run:
   ```bash
   python app.py
   ```
4. Open your browser and go to [http://127.0.0.1:5000/](http://127.0.0.1:5000/) to view the dashboard.

---

**For educational demonstration only.**
