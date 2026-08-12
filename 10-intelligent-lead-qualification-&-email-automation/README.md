#  Project 10 — Intelligent Lead Qualification & Email Automation ⭐⭐⭐⭐⭐⭐⭐

A client-style n8n automation workflow that uses **Google Gemini AI** to analyze incoming leads, classify them as **Hot, Warm, or Cold**, route them through different workflow paths, merge the results, and automatically send a personalized email response.

This project demonstrates a more advanced real-world business automation scenario involving AI decision-making, conditional routing, data transformation, merging, and automated customer communication.

---

## 🚀 Workflow

```text id="h1w6j3"
Webhook
   │
   ▼
Edit Fields
   │
   ▼
Gemini AI
   │
   ▼
Edit Fields
   │
   ▼
Switch
   │
   ├── 🔥 Hot ──────┐
   │                │
   ├── 🟡 Warm ─────┤
   │                │
   └── ❄️ Cold ─────┘
                    │
                    ▼
                  Merge
                    │
                    ▼
                  Gmail
                    │
                    ▼
            Respond to Webhook
```

### 📸 Workflow Screenshot

<img width="844" height="529" alt="image" src="https://github.com/user-attachments/assets/0f7688f8-5afb-4a81-80ae-e1feb42b2bd1" />


---

## 🎯 Objective

The goal of this project is to simulate a real-world client automation system for handling potential customers.

The workflow receives a customer inquiry, uses Google Gemini to analyze the lead, determines whether the lead is **Hot, Warm, or Cold**, routes the lead through the appropriate path using a Switch node, and then sends a personalized response through Gmail.

This demonstrates how AI can make business decisions inside an automated workflow.

---

## 📥 Input

The workflow receives customer information through a **Webhook** using a `POST` request.

### Example Input

```json id="cx0s80"
{
  "name": "Sarah",
  "email": "baceromicah@gmail.com",
  "company": "Sarah's Boutique",
  "message": "Hi, I'm interested in your website design service. I'm comparing a few agencies right now and would like to know your pricing and what's included."
}
```

---

## 🤖 AI Processing

The Google Gemini node analyzes the customer's inquiry and determines:

* Lead Type
* Priority
* Recommended Response

The lead is classified into one of three categories:

```text id="w0u0dg"
🔥 Hot
🟡 Warm
❄️ Cold
```

The AI also generates a personalized response that can be sent directly to the customer.

---

## 🔀 Lead Routing

After Gemini analyzes the lead, the **Switch** node determines which path the lead should follow.

### 🔥 Hot Lead

High-potential customers who show strong buying intent.

```text id="xujw3c"
Hot
 ↓
Hot Lead Path
```

### 🟡 Warm Lead

Potential customers who are interested but may still be comparing options or gathering information.

```text id="2v1j4n"
Warm
 ↓
Warm Lead Path
```

### ❄️ Cold Lead

Customers who show little immediate buying intent.

```text id="x9r4c5"
Cold
 ↓
Cold Lead Path
```

---

## 🔗 Merge

After the different lead paths are processed, the **Merge** node combines the results back into a single workflow path.

```text id="j5k6u1"
🔥 Hot ──────┐
             │
🟡 Warm ─────┼──→ Merge
             │
❄️ Cold ─────┘
```

This allows all lead types to continue to the same Gmail automation step.

---

## 📧 Gmail Automation

After the lead has been classified and processed, Gmail automatically sends the AI-generated response to the customer.

This allows the business to respond to potential customers without manually writing every email.

---

## 📤 Output

For this test, Gemini classified the lead as a **Warm** lead with **Medium** priority.

### Example Output

```json id="ukv3ur"
[
  {
    "Name": "Sarah",
    "Company": "Sarah's Boutique",
    "Message": "Hi, I'm interested in your website design service. I'm comparing a few agencies right now and would like to know your pricing and what's included.",
    "Lead Type": "Warm",
    "Priority": "Medium",
    "AI Response": "Hi Sarah, thank you for reaching out to BrightWeb Digital Agency! We would love to help Sarah's Boutique stand out with a professional, high-converting website. Our design packages typically include custom UI/UX design, mobile responsiveness, basic SEO setup, and a user-friendly content management system. Since we tailor our services to each client's specific goals, I'd love to schedule a brief 15-minute discovery call to learn more about your vision so I can provide you with an accurate quote and a detailed breakdown of our deliverables. Are you available for a chat later this week?",
    "Email": "baceromicah@gmail.com"
  }
]
```

### Lead Result

```text id="8r9v6t"
Lead Type: 🟡 Warm
Priority: Medium
Email: Sent ✅
```

---

## 🔄 How It Works

### 1. Webhook

Receives the customer's information.

```json id="5z5g3p"
{
  "name": "Sarah",
  "email": "baceromicah@gmail.com",
  "company": "Sarah's Boutique",
  "message": "Hi, I'm interested in your website design service. I'm comparing a few agencies right now and would like to know your pricing and what's included."
}
```

### 2. Edit Fields

Prepares and organizes the incoming customer information.

### 3. Gemini AI

Analyzes the customer's message and determines:

* Lead type
* Priority
* AI-generated response

### 4. Edit Fields

Formats the AI output into a consistent structure that can be used by the routing and email steps.

### 5. Switch

Routes the lead based on the AI-generated lead type:

```text id="n8v3tq"
🔥 Hot
🟡 Warm
❄️ Cold
```

### 6. Merge

Combines the different lead paths back into one workflow.

### 7. Gmail

Sends the personalized AI-generated response to the customer.

### 8. Respond to Webhook

Returns the processed result after the automation is completed.

---

## 🧪 Testing

The workflow can be tested using **Postman**.

### Request

**Method:**

```text id="o9rjcs"
POST
```

### Example Body

```json id="fyx2m2"
{
  "name": "Sarah",
  "email": "baceromicah@gmail.com",
  "company": "Sarah's Boutique",
  "message": "Hi, I'm interested in your website design service. I'm comparing a few agencies right now and would like to know your pricing and what's included."
}
```

### Expected Process

```text id="c6z2u7"
Postman
   ↓
Webhook
   ↓
Edit Fields
   ↓
Gemini AI
   ↓
Edit Fields
   ↓
Switch
   ├── 🔥 Hot
   ├── 🟡 Warm
   └── ❄️ Cold
          ↓
        Merge
          ↓
        Gmail
          ↓
    Email Sent ✅
          ↓
 Respond to Webhook
```

---

## 🧩 Technologies Used

* **n8n** — Workflow automation
* **Google Gemini** — AI lead analysis
* **Switch** — Conditional lead routing
* **Merge** — Combines workflow branches
* **Gmail** — Automated email communication
* **Webhook** — Receives customer inquiries
* **Edit Fields** — Data preparation and formatting
* **Postman** — API testing
* **JSON** — Data format

---

## 💡 Example Use Cases

This automation can be used for:

* Sales lead qualification
* Website agency inquiries
* Service-based businesses
* Customer support
* Automated sales responses
* Lead nurturing
* CRM automation
* E-commerce businesses
* Digital marketing agencies
* AI-powered sales assistants

---

## 📈 Skills Demonstrated

This project demonstrates experience with:

* n8n workflow automation
* Google Gemini integration
* AI lead qualification
* AI prompt engineering
* Conditional workflow routing
* Switch node logic
* Merge node logic
* Gmail automation
* Webhook integration
* Dynamic data mapping
* JSON data handling
* Automated customer communication
* API testing with Postman
* Multi-branch workflow design
* Client-style automation architecture

---

## ⭐ Future Improvements

Possible improvements for future versions:

* Add different email templates for Hot, Warm, and Cold leads
* Send Hot leads directly to a sales representative
* Add Slack or Discord notifications for Hot leads
* Store all leads in Google Sheets or Airtable
* Add automatic lead scoring from 1–100
* Add CRM integration
* Schedule automatic follow-up emails
* Add a human approval step for high-value leads
* Add calendar booking links for Hot leads
* Create an automated lead nurturing sequence

---

## 📌 Project Status

**Status:** ✅ Completed

**Project:** #10

**Difficulty:** ⭐⭐⭐⭐⭐⭐⭐

**Category:** AI Automation / Lead Qualification / Sales Automation

**AI Provider:** Google Gemini

**Email Automation:** Gmail

**Workflow Type:** Multi-Branch Client-Style Automation

---

## 👨‍💻 Portfolio

This project is part of my **n8n Automation Portfolio**, demonstrating practical experience building client-style AI automation systems using Google Gemini, conditional routing, data processing, Gmail, webhooks, and multi-branch workflows.
