from flask import Flask, render_template_string
import re

app = Flask(__name__)

# Path to the sample log file
LOG_FILE = "sample_logs/auth.log"

def parse_failed_logins(log_path):
    """
    Parses log file for failed login attempts and returns a summary.
    """
    try:
        with open(log_path, "r") as f:
            lines = f.readlines()
    except FileNotFoundError:
        return {}

    pattern = re.compile(r"Failed password for (invalid user )?(\w+) from ([\d\.]+)")
    summary = {}

    for line in lines:
        match = pattern.search(line)
        if match:
            ip = match.group(3)
            summary[ip] = summary.get(ip, 0) + 1
    return summary

@app.route("/")
def dashboard():
    failed_logins = parse_failed_logins(LOG_FILE)
    # Render dashboard with results
    template = """
    <h1>Simple SIEM Dashboard</h1>
    <h2>Failed Login Attempts by IP</h2>
    <table border="1">
        <tr><th>IP Address</th><th>Number of Attempts</th></tr>
        {% for ip, count in data.items() %}
        <tr><td>{{ ip }}</td><td>{{ count }}</td></tr>
        {% endfor %}
    </table>
    """
    return render_template_string(template, data=failed_logins)

if __name__ == "__main__":
    app.run(debug=True)
