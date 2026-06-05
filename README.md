# 📄 Automated Hiring Email System (n8n Workflow)

## 📌 Overview

This project is an automated system built using **n8n** to streamline the hiring process.

It reads candidate data from Google Sheets, generates personalized acceptance emails using AI, sends them automatically, and updates the sheet to track delivery status.

The system ensures that each candidate receives a customized email based on their job title, without any manual work.

---

## ⚙️ How It Works

The workflow is fully automated and follows these steps:

### 1. Google Sheets Trigger
The workflow starts when new or updated candidate data is detected.

---

### 2. Fetch Candidates Data
It retrieves candidate information such as:
- Name
- Email
- Job Title
- Status

---

### 3. Filter by Job Title
Candidates are grouped or processed based on their job role.

---

### 4. AI Email Generation
An AI model generates a formal HTML acceptance email using:

- Candidate Name: `{{ $json.name }}`
- Job Title: `{{ $json["job Title"] }}`

---

### 5. Send Email
The generated HTML email is sent to the candidate via email service (SMTP / Gmail / SendGrid).

---

### 6. Update Google Sheets
After sending the email, the system updates the sheet:

- status = sent
- sent_at timestamp is added

---

### 7. Logging (Optional)
Stores records of sent emails for tracking and debugging purposes.

---

## 🧠 AI Email Template (Output Format)

```html
<p>Dear {{ $json.name }},</p>

<p>We are pleased to inform you that you have been accepted for the position of {{ $json["job Title"] }} at Zone Tech. Congratulations!</p>

<p>Our team will contact you via phone shortly to discuss the next steps in the onboarding process.</p>

<p>Thank you for your interest in joining Zone Tech. We look forward to working with you.</p>

<p>Zone Team.</p>

<p>Best regards</p>
