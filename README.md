 WhatsApp-Driven Google Drive Assistant (n8n Workflow)
 
 Overview
This project automates file management in Google Drive using WhatsApp messages via Twilio and n8n.
Users send specific commands through WhatsApp, and the workflow responds by listing, deleting, or moving files in Google Drive.
The flow uses:

Twilio WhatsApp Sandbox for message input/output

Google Drive API for file operations

OpenAI GPT-4o for summarization

Switch Node for command routing

⚙️ Features
WhatsApp-based file management

Automatic command parsing

Secure Twilio signature verification (optional)

Multi-command routing with Switch Node

Summarization of text, PDF, and DOCX files

🛠 Tech Stack
n8n

Twilio WhatsApp API

Google Drive API

OpenAI API (GPT-4o)

📂 Workflow Architecture
plaintext
Copy
Edit
[Webhook]
    ↓
[Function: Parse Command]
    ↓
[Switch Node: Command Router]
 ├── LIST → Google Drive: List Files → Twilio Send
 ├── DELETE → Confirm & Delete File
 ├── MOVE → Move File to Target Folder
 └── SUMMARY → Download & Summarize via GPT-4o → Twilio Send
  Setup Instructions
1️⃣ Twilio WhatsApp Sandbox
Visit: https://www.twilio.com/console/sms/whatsapp/sandbox

Join the sandbox by sending the join keyword to the Twilio number.

Save Account SID and Auth Token.

2️⃣ Google Drive API
Go to: https://console.cloud.google.com/apis/credentials

Create an OAuth 2.0 Client ID.

Enable Google Drive API.

Set redirect URI:

bash
Copy
Edit
https://n8n.io/oauth2-credential/callback
Save Client ID and Client Secret.

