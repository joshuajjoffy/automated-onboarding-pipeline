Automated Customer Onboarding Pipeline

📋 Overview

This project is an end-to-end automated pipeline designed to streamline the customer onboarding process. By integrating Webhooks, Python logic, Google Sheets, and Gmail, this system eliminates manual data entry and ensures instant user engagement.

The pipeline listens for new user signups via an API endpoint, processes and sanitizes the data using Python, stores the records in a database (Google Sheets), and automatically sends a personalized welcome email.

🚀 Key Features

Real-time Trigger: Uses Webhooks to capture user data instantly upon signup.

Data Transformation (Python): - Capitalizes names (e.g., "sarah connor" -> "Sarah Connor").

Generates a unique, smart User ID (e.g., USR-SAR16).

Automated Database Entry: Appends clean data to Google Sheets with a precise timestamp.

Instant Notification: Sends a dynamic, personalized welcome email via Gmail.

🛠️ Tech Stack

Workflow Automation: n8n

Scripting: Python (Data cleaning & logic)

Database: Google Sheets

Communication: Gmail (SMTP)

API Testing: cURL / Postman / ReqBin

⚙️ Architecture Workflow

The data flows through the system in the following steps:

Webhook: Receives raw JSON payload (Name, Email).

Python Node: - Splits full name into First/Last.

Generates Custom ID (USR + First 3 letters + Email Length).

Google Sheets Node: Appends User ID, First Name, Last Name, Email, and Timestamp to the database.

Gmail Node: Sends a welcome email using the First Name and User ID.

(Note: Upload a screenshot of your n8n canvas here and name it workflow_diagram.png)

📥 Example JSON Payload

To test the pipeline, send a POST request to the webhook URL with the following body:

{
  "full_name": "bruce wayne",
  "email": "bruce@wayne-enterprises.com"
}


📊 Results

Database Output (Google Sheets):
| user_id | first_name | last_name | email | timestamp |
| :--- | :--- | :--- | :--- | :--- |
| USR-BRU25 | Bruce | Wayne | bruce@wayne... | 2025-11-26T14:30:00 |

Email Output:

Subject: Welcome to the Platform, Bruce!

Hi Bruce,
Your account has been successfully created!
Your User ID is: USR-BRU25

Welcome aboard!

🔧 How to Run

Import Workflow: Import the workflow.json file into your n8n instance.

Setup Credentials:

Connect your Google account for Sheets and Gmail.

Prepare Sheet: Create a Google Sheet with headers: user_id, first_name, last_name, email, timestamp.

Activate: specific the Webhook URL and toggle the workflow to "Active".

Created by
