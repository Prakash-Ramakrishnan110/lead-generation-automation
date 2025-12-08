# 🚀 AI-Powered Lead Generation & Qualification Workflow
A fully automated lead capture and AI-based qualification system built with **n8n**, **OpenAI GPT-4o-mini**, **Gmail API**, and **n8n Data Tables**. This workflow captures leads from a web form, stores them in a database, scores their quality using AI, and notifies you instantly when high-value prospects submit their information.

---

## ⭐ Features

### ✅ Lead Capture Form
- Clean, embeddable web form (no n8n branding)
- Responsive layout for desktop & mobile
- Collects:
  - Full Name  
  - Email  
  - Company Name  
  - Company Size  
  - Project Description  
  - Budget Range  
  - Timeline  
- Shows a “Thank You” confirmation after submission

---

### ✅ Central Workflow Configuration
Easily update all workflow settings from one place:

| Setting | Example |
|--------|---------|
| **High Score Threshold** | `70` |
| **Notification Email** | `prakash7418r@gmail.com` |
| **Calendar Booking Link** | `https://cal.com/prakash-r-j6e1vx/prakash` |

---

### ✅ Data Formatting Layer
Automatically:
- Converts form fields to database-friendly names  
- Ensures clean, consistent formatting  
- Adds `submitted_at` timestamp  
Full Name → full_name
Budget Range → budget_range
Project Description → project_description


---

### ✅ Persistent Database Storage
All leads are stored in an n8n Data Table named **mytable**.

#### Required Columns


full_name
email
company_name
company_size
project_description
budget_range
timeline
submitted_at


#### Optional Columns (for AI Scoring)


qualification_score
qualification_priority
qualification_reasoning


---

## 🤖 AI Lead Qualification (GPT-4o-mini)

Each lead is scored using a weighted model:

| Factor | Weight |
|--------|--------|
| Budget Range | 30% |
| Timeline Urgency | 25% |
| Company Size | 20% |
| Project Description Quality | 25% |

Example AI output:

```json
{
  "score": 85,
  "priority": "high",
  "reasoning": "Strong budget, urgent timeline, and clear requirements."
}

🔀 Smart Routing Logic
If score ≥ 70

Lead marked as high priority

Sends detailed email alert to your inbox

Auto-includes your calendar booking link

If score < 70

Lead is still stored in the database

No email sent

Helps you archive all leads for future review

📧 Email Notifications

High-priority leads trigger a real-time Gmail alert containing:

Lead contact details

Company information

Budget & timeline

AI score + reasoning

Direct reply-to email

Your calendar booking link

Email sending uses Gmail OAuth2 API.

🗂️ Workflow Structure

Lead Generation Form (Web Form Trigger)

Workflow Configuration (central settings)

Format Data for Table

Store Lead in mytable

AI Lead Qualifier (GPT-4o-mini)

Check Lead Score

Branching:

High score → Send Email

Low score → End

Completed Execution Summary

🚀 Usage
Embed the Form on Your Website

Open the Lead Generation Form node

Copy the Production URL

Paste into your website as:

<iframe src="YOUR_FORM_URL_HERE" width="100%" height="650px"></iframe>

Test the Workflow

Submit a lead through the form

Check mytable for stored data

If score ≥70 → check your email inbox

Modify the Workflow

Change threshold → edit highScoreThreshold

Change notification email → edit yourEmail

Modify AI scoring → edit system prompt in AI Lead Qualifier

Add/remove form fields → edit Lead Generation Form node

📈 Benefits

24/7 automated lead handling

AI scoring removes guesswork

Focus only on high-quality leads

Clean, structured database for all submissions

Fast response times → higher conversions

Highly customizable & scalable

🧰 Technologies Used

n8n Automation Platform

OpenAI GPT-4o-mini

Gmail API (OAuth2)

n8n Data Tables

HTML Embeddable Form

Example:

