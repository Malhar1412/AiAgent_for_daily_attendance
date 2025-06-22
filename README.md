 # AiAgent_for_daily_attendance 
📌 AI Attendance Analyzer Agent

project demo:-

https://github.com/user-attachments/assets/d56e468c-8558-4668-8653-9bda24258eff



1) What does this project do?


This project automates daily attendance analysis  It fetches 1check-in times, 2analyzes them, and 3determines whether each person is "Present", "Late", or "Absent" — without any manual work.

The final status is written to a structured attendance "summary sheet", and notifications (e.g., via email or Telegram) can also be sent.


2) Why is this project useful?


 Saves Time: Fully automates daily attendance tracking.

1 Eliminates Human Error: Status is determined based on consistent rules or AI logic.

2 Easy Integration: Works with Google Sheets — no extra tools needed.

3 Notifies Automatically: Optionally sends reports to users or admins.

4 AI Logic Ready: You can plug in an LLM to analyze messy or incomplete data if needed.

5 Scalable: Works for teams of any size — from classrooms to large companies.


3) How can users get started?


###Requirements:

A working n8n instance (cloud or local)

A Google Sheet for raw check-in data

A Google Sheets API credential



# AI-Powered Attendance Analyzer 

d automatically classify each person as **Present**, **Late**, or **Absent**.

No manual work needed — the bot runs every morning on its own!



##  What This Project Does

- Reads attendance entries (Name, Date, Clock-in Time)
- Classifies attendance using simple rules:
  
  - Present: Clocked in by 9:30 AM
  - Late: Clocked in after 9:30 AM
  - Absent: No clock-in time
  - 
- Saves the result into a clean summary sheet
- Runs automatically every day via cron schedule





##  n8n Workflow Breakdown

This project uses the following nodes:

### 1. **Cron Node (Trigger)**  
**Purpose:** Runs the workflow every morning.  
**Setup:**  

- Mode: Every Day  
- Time: 9:00 AM  



### 2. **Google Sheets (Get Rows)**  

**Purpose:** Reads attendance from `RawData` tab  

**Config:**  

- Operation: Get All  
- Sheet: Your spreadsheet  
- Tab: RawData  



### 3. **Function Node (Classify Attendance)**  
**Purpose:** Classifies each row into Present / Late / Absent  
**Code:**

```javascript
return items.map(item => {
  const name = item.json.name;
  const date = item.json.date;
  const time = item.json["clock in time"];
  let status = "";

  if (!time) {
    status = "Absent";
  } else {
    const hour = parseInt(time.split(":")[0]);
    const min = parseInt(time.split(":")[1]);
    const isPM = time.toLowerCase().includes("pm");
    const totalMinutes = (isPM && hour < 12 ? hour + 12 : hour) * 60 + min;

    if (totalMinutes <= 570) { // 9:30 AM = 570 mins
      status = "Present";
    } else {
      status = "Late";
    }
  }

  return {
    json: { name, date, status }
  };
});


 OpenAI/Hugging Face key for LLM-based logic





