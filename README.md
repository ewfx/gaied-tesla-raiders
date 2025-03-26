# 🚀 Mail Intelligence Agency (MIA) with AI & n8n

## 📌 Table of Contents
- [Introduction](#introduction)
- [Demo](#demo)
- [Inspiration](#inspiration)
- [What It Does](#what-it-does)
- [How We Built It](#how-we-built-it)
- [Challenges We Faced](#challenges-we-faced)
- [How to Run](#how-to-run)
- [Tech Stack](#tech-stack)
- [Team](#team)

---

## 🎯 Introduction
This project automates the classification of incoming banking domain emails using n8n and an AI language model. It eliminates manual triaging by reading the email content and attachments (if any) and classifying them into allowed request types like "Fee Payment", "Commitment Change", or "AU Transfer".

The automation not only classifies emails but also checks for duplicates, logs the requests into Airtable, and enables future auditing or operational reporting.

## 🎥 Demo
🔗 [Live Demo](#) (if applicable)  
📹 [Video Demo](#) (if applicable)  
🖼️ Screenshots:

![Screenshot 1](link-to-image)

## 💡 Inspiration
In a high-volume operational banking setup, shared mailboxes receive hundreds of emails daily, including instructions, queries, and compliance updates. Manual routing causes SLA delays and audit gaps.

This project solves that problem by:

✅ Automatically understanding email + attachment content.
✅ Categorizing the message using AI.
✅ Logging classification in Airtable.
✅ Detecting repeated request types (for the same sender).

## ⚙️ What It Does
- 🔹 Polls Gmail for new emails (every minute).
- 🔹 Detects if the email has attachments.
- 🔹 Extracts PDF/Text content from attachments.
- 🔹 Uses OpenRouter’s Mistral AI model for classification.
- 🔹 Returns:
```
      {
        "request_type": "Commitment Change",
        "sub_request_type": "Increase"
      }
```      
✅ Logs to Airtable with status: new or duplicate.      

## 🛠️ How We Built It
We used n8n as the orchestration engine and built the following modular nodes:

✅ Gmail Trigger – Listens for incoming mail.
✅ Parser – Gets email content and metadata.
✅ IF Node – Checks for attachments.
✅ Extractor – Converts PDF/text to string.
✅ Merger – Combines email + attachment content.
✅ LLM Prompt (HTTP) – Sends combined text to AI for classification.
✅ Airtable Search – Checks for duplicate request type by sender.
✅ Airtable Create – Inserts classified result with status.

## 🚧 Challenges We Faced
- 🔹 Prompt engineering to guide the LLM to strictly return only allowed request/sub-request types.
- 🔹 Handling dynamic attachments (PDFs and other formats).
- 🔹 Airtable integration + duplicate filtering logic.
- 🔹 Ensuring the output JSON is AI-friendly and Airtable-compatible.

## 🏃 How to Run
1. Clone the repository  
   ```sh
   https://github.com/ewfx/gaied-tesla-raiders.git
   ```
2. Install dependencies  
   ```sh
   npm install -g n8n
   n8n start
   ```
3. Configure environment variables/API keys:
   ✅ Gmail credentials
   ✅ OpenRouter API token
   ✅ Airtable Base ID and API Key

4. Import workflow JSON and run Test Workflow.

## 🏗️ Tech Stack
- 🔹 n8n – Low-code automation engine
- 🔹 OpenRouter AI – Mistral-7B-Instruct LLM
- 🔹 Airtable – Relational table to store output + rules
- 🔹 Gmail – Email trigger source
- 🔹 JavaScript (Code Nodes) – Data transformation

## 👥 Team
- **Vigneshkumar G** - [LinkedIn](https://www.linkedin.com/in/vkumarg31990/)
- **Karthik S** - [LinkedIn](https://www.linkedin.com/in/karthik-sankaran-bigdata/)
- **Devendra B** - [LinkedIn](https://www.linkedin.com/in/devendra-bhumarapu/)