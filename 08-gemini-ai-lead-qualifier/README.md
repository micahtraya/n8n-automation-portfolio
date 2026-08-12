# Project 8 — Gemini AI Lead Qualifier  ⭐⭐⭐⭐⭐⭐

An n8n automation workflow that uses **Google Gemini AI** to automatically analyze customer inquiries and send an AI-generated response through Gmail.

This project demonstrates how to connect a webhook to Google Gemini and Gmail to create an automated customer support workflow.

---

##  Workflow

```text
Webhook
   │
   ▼
Edit Fields
   │
   ▼
Google Gemini
   │
   ▼
Gmail
   │
   ▼
Respond to Webhook
```

###  Workflow Screenshot

<img width="853" height="529" alt="image" src="https://github.com/user-attachments/assets/d0f83640-f4d6-4e89-8bee-209cce40eef3" />

---

##  Objective

The goal of this project is to automate customer inquiry handling using AI.

Instead of manually reviewing and responding to every customer message, the workflow sends the inquiry to Google Gemini, generates an appropriate response, and automatically sends it to the customer through Gmail.

---

##  Input

The workflow receives customer information through a **Webhook** using a `POST` request.

### Example Input

```json
{
  "customer": "Micah",
  "email": "micahtraya16@gmail.com",
  "subject": "Wrong item received",
  "message": "Hi, I ordered a wireless mouse but received a keyboard. Can you help me?"
}
```

---

##  AI Processing

The Google Gemini node receives the customer information and generates a professional response.

The AI prompt instructs Gemini to:

* Analyze the customer's message
* Understand the customer's issue
* Determine the appropriate response
* Provide a professional and helpful reply

---

##  Output

After Gemini generates the response, the Gmail node automatically sends it to the customer.

### Gmail Output

```json
[
  {
    "id": "19fe1ea3c117bfbe",
    "threadId": "19fe1ea3c117bfbe",
    "labelIds": [
      "SENT"
    ]
  }
]
```

The `SENT` label confirms that the email was successfully sent.

---

##  Technologies Used

* **n8n** — Workflow automation
* **Google Gemini** — AI analysis and response generation
* **Gmail** — Automated email delivery
* **Webhook** — Receives customer information
* **Edit Fields** — Data preparation and mapping
* **Postman** — API testing
* **JSON** — Data format

---

##  How It Works

### 1. Webhook

The Webhook receives the customer's information.

```json
{
  "customer": "Micah",
  "email": "micahtraya16@gmail.com",
  "subject": "Wrong item received",
  "message": "Hi, I ordered a wireless mouse but received a keyboard. Can you help me?"
}
```

### 2. Edit Fields

The customer information is organized and prepared before being sent to Google Gemini.

### 3. Google Gemini

Gemini analyzes the customer inquiry and generates a professional response.

### 4. Gmail

The AI-generated response is automatically sent to the customer's email address.

### 5. Respond to Webhook

The workflow returns the result after the automation is completed.

---

##  Testing

The workflow can be tested using **Postman**.

### Request

**Method:**

```text
POST
```

### Example Body

```json
{
  "customer": "Micah",
  "email": "micahtraya16@gmail.com",
  "subject": "Wrong item received",
  "message": "Hi, I ordered a wireless mouse but received a keyboard. Can you help me?"
}
```

### Expected Result

The customer receives an AI-generated email response.

The Gmail node returns:

```json
{
  "labelIds": [
    "SENT"
  ]
}
```

---

##  Example Use Cases

This automation can be used for:

* Customer support
* Lead qualification
* E-commerce support
* Automated email responses
* Order issue handling
* Customer inquiry management
* Sales inquiries
* AI-powered help desks

---

##  Skills Demonstrated

This project demonstrates experience with:

* n8n workflow automation
* Google Gemini integration
* Gmail automation
* Webhook integration
* JSON data handling
* Dynamic data mapping
* AI prompt engineering
* API testing with Postman
* Automated customer communication
* Multi-step AI workflow design

---

##  Future Improvements

Possible improvements for future versions:

* Save customer inquiries to Google Sheets
* Store leads in Airtable
* Add automatic lead scoring
* Send high-priority notifications to Slack or Discord
* Add human approval before sending emails
* Create different AI response templates
* Add CRM integration
* Track customer support conversations

---

##  Project Status

**Status:** ✅ Completed

**Project:** #8

**Difficulty:** ⭐⭐⭐⭐⭐⭐

**Category:** AI Automation / Customer Support / Lead Qualification

**AI Provider:** Google Gemini

**Email Automation:** Gmail

---

##  Portfolio

This project is part of my **n8n Automation Portfolio**, demonstrating practical experience building AI-powered automation workflows using Google Gemini, Gmail, webhooks, and automated customer communication.
