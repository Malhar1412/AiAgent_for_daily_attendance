# AiAgent_for_daily_attendance 
📌 AI Attendance Analyzer Agent
1️⃣ What does this project do?
This project automates daily attendance analysis using n8n, Google Sheets, and optional AI (LLM) logic. It fetches check-in times, analyzes them, and determines whether each person is Present, Late, or Absent — without any manual work.

The final status is written to a structured attendance summary sheet, and notifications (e.g., via email or Telegram) can also be sent.

2️⃣ Why is this project useful?
⏱️ Saves Time: Fully automates daily attendance tracking.

✅ Eliminates Human Error: Status is determined based on consistent rules or AI logic.

📊 Easy Integration: Works with Google Sheets — no extra tools needed.

🔔 Notifies Automatically: Optionally sends reports to users or admins.

🧠 AI Logic Ready: You can plug in an LLM to analyze messy or incomplete data if needed.

📈 Scalable: Works for teams of any size — from classrooms to large companies.

3️⃣ How can users get started?
🔧 Requirements:
A working n8n instance (cloud or local)

A Google Sheet for raw check-in data

A Google Sheets API credential

(Optional) OpenAI/Hugging Face key for LLM-based logic

🚀 Setup Steps:
Clone or download this repository.

Import the provided .json n8n workflow into your n8n instance.

Configure your Google Sheets credentials inside n8n.

Customize the logic in the Function Node or use AI for analysis.

Set up the Cron Trigger to run daily.

Test with sample data to ensure accuracy.



