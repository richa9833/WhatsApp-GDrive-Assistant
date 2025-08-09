# 📱 WhatsApp-Driven Google Drive Assistant (n8n Workflow)

##  Overview
This project automates **file management in Google Drive** using **WhatsApp messages** via **Twilio** and **n8n**.  
Users send specific commands through WhatsApp, and the workflow responds by **listing**, **deleting**, **moving**, or **summarizing** files in Google Drive.  

The workflow uses:
- **Twilio WhatsApp Sandbox** for message input/output
- **Google Drive API** for file operations
- **OpenAI GPT-4o** for summarization
- **Switch Node** for command routing

##  Features
-  WhatsApp-based file management
-  Automatic command parsing
-  Secure Twilio signature verification *(optional)*
-  Multi-command routing with Switch Node
-  Summarization of text, PDF, and DOCX files


## Tech Stack
- **n8n**
- **Twilio WhatsApp API**
- **Google Drive API**
- **OpenAI API (GPT-4o)**


##  Workflow Architecture
```plaintext

[Webhook]
   ↓
[Function: Parse Command]
   ↓
[Switch Node: Command Router]
   ├── LIST    → Google Drive: List Files → Twilio Send
   ├── DELETE  → Confirm & Delete File
   ├── MOVE    → Move File to Target Folder
   └── SUMMARY → Download & Summarize via GPT-4o → Twilio Send
