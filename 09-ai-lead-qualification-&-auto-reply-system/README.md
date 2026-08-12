# 🚀 Project 9 — AI Lead Qualification & Auto-Reply System ⭐⭐⭐⭐⭐⭐

An n8n automation workflow that uses **Google Gemini AI** to analyze potential customer inquiries, determine the lead type and priority, store the lead information in **Google Sheets**, and automatically send a response through **Gmail**.

This project demonstrates how AI can be combined with data storage and email automation to create an automated lead qualification system.

---

## 🚀 Workflow

```text
Customer submits inquiry
        │
        ▼
     Webhook
        │
        ▼
   Edit Fields
        │
        ▼
    Gemini AI
        │
        ▼
 AI analyzes lead
 • Lead Type
 • Priority
 • Recommended Response
        │
        ▼
  Google Sheets
        │
        ▼
     Gmail
        │
        ▼
Respond to customer
```

### 📸 Workflow Screenshot

<img width="829" height="523" alt="image" src="https://github.com/user-attachments/assets/73d0d792-ad4f-4dbf-9c68-8ed59cbad56f" />

---

## 🎯 Objective

The goal of this project is to automatically qualify potential customers and respond to their inquiries using AI.

Instead of manually reviewing every incoming lead, the workflow uses Google Gemini to analyze the customer's message, determine the lead type and priority, save the lead information to Google Sheets, and automatically send a personalized response through Gmail.

---

## 📥 Input

The workflow receives customer information through a **Webhook** using a `POST` request.

### Example Input

```json
{
  "name": "John",
  "email": "baceromicah@gmail.com",
  "company": "John's Store",
  "message": "Hello, I was just curious about what kind of website services your company offers. Maybe I'll need one someday."
}
```

---

## 🤖 AI Processing

The Google Gemini node analyzes the customer's inquiry and determines:

* Lead Type
* Priority
* Recommended Response

The AI evaluates the customer's message to determine how valuable or urgent the lead may be and generates an appropriate response.

---

## 📊 Google Sheets

After Gemini processes the inquiry, the lead information is stored in **Google Sheets**.

The spreadsheet can be used as a simple lead database for tracking potential customers.

Example information stored:

```text
Name
Email
Company
Message
Lead Type
Priority
AI Response
```

---

## 📤 Output

After the lead is analyzed and stored, Gmail automatically sends the AI-generated response to the customer.

### Gmail Output

```json
[
  {
    "id": "19fec01fcd2f2d6f",
    "threadId": "19fec01fcd2f2d6f",
    "labelIds": [
      "SENT"
    ]
  }
]
```

The `SENT` label confirms that Gmail successfully sent the automated response.

---

## 🧩 Technologies Used

* **n8n** — Workflow automation
* **Google Gemini** — AI lead analysis and response generation
* **Google Sheets** — Lead database
* **Gmail** — Automated customer communication
* **Webhook** — Receives customer inquiries
* **Edit Fields** — Data preparation and mapping
* **Postman** — API testing
* **JSON** — Data format

---

## 🔄 How It Works

### 1. Webhook

The Webhook receives the potential customer's information.

```json
{
  "name": "John",
  "email": "baceromicah@gmail.com",
  "company": "John's Store",
  "message": "Hello, I was just curious about what kind of website services your company offers. Maybe I'll need one someday."
}
```

### 2. Edit Fields

The customer information is organized and prepared for Gemini.

### 3. Gemini AI

Gemini analyzes the customer's inquiry and determines the lead type, priority, and recommended response.

### 4. Google Sheets

The lead information and AI-generated analysis are saved to Google Sheets.

### 5. Gmail

The AI-generated response is automatically sent to the customer's email address.

### 6. Respond to Webhook

The workflow completes the automation and returns the result of the request.

---

## 🧪 Testing

The workflow can be tested using **Postman**.

### Request

**Method:**

```text
POST
```

### Example Body

```json
{
  "name": "John",
  "email": "baceromicah@gmail.com",
  "company": "John's Store",
  "message": "Hello, I was just curious about what kind of website services your company offers. Maybe I'll need one someday."
}
```

### Expected Process

```text
Postman
   ↓
Webhook
   ↓
Edit Fields
   ↓
Gemini AI
   ↓
Google Sheets
   ↓
Gmail
   ↓
Email Sent ✅
```

### Gmail Result

```json
{
  "labelIds": [
    "SENT"
  ]
}
```

---

## 💡 Example Use Cases

This automation can be used for:

* Lead qualification
* Website service inquiries
* Sales automation
* Customer inquiry management
* Automated email responses
* CRM lead management
* E-commerce businesses
* Service-based businesses
* AI-powered sales assistants
* Customer follow-up automation

---

## 📈 Skills Demonstrated

This project demonstrates experience with:

* n8n workflow automation
* Google Gemini integration
* Google Sheets integration
* Gmail automation
* Webhook integration
* AI lead qualification
* AI prompt engineering
* Dynamic data mapping
* JSON data handling
* Automated email communication
* Lead database management
* API testing with Postman
* Multi-step AI workflow design

---

## ⭐ Future Improvements

Possible improvements for future versions:

* Add lead scoring from 1–100
* Send hot leads to Slack or Discord
* Add automatic follow-up emails
* Create a CRM integration
* Add different email templates based on lead priority
* Notify sales teams about high-priority leads
* Add lead status tracking
* Generate personalized sales proposals
* Add calendar booking automation
* Create automated lead nurturing sequences

---

## 📌 Project Status

**Status:** ✅ Completed

**Project:** #9

**Difficulty:** ⭐⭐⭐⭐⭐⭐

**Category:** AI Automation / Lead Qualification / Sales Automation

**AI Provider:** Google Gemini

**Database:** Google Sheets

**Email Automation:** Gmail

---

## 👨‍💻 Portfolio

This project is part of my **n8n Automation Portfolio**, demonstrating practical experience building AI-powered lead qualification and customer communication systems using Google Gemini, Google Sheets, Gmail, and webhooks.
