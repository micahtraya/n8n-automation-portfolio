# Project 10 — Client-Style Automation Challenge

A complete **n8n client-style automation workflow** that uses AI to analyze an incoming business inquiry, classify the lead, generate a personalized response, send an email, and record the lead information in a spreadsheet.

This workflow simulates a real-world automation project for a digital agency handling incoming website-service inquiries.

## Workflow

```text id="q8m2vx"
Webhook
   │
   ▼
Edit Fields
   │
   ▼
Message a Model
   │
   ▼
Edit Fields
   │
   ▼
Switch
   ├── Hot ──────►
   ├── Warm ─────► Merge ──► Send a message ──► Append row in sheet ──► Respond to Webhook
   └── Cold ─────►
```
<img width="853" height="522" alt="10" src="https://github.com/user-attachments/assets/8a4bdcb2-ccd2-4cf4-80c0-f5c6db8766e0" />

<img width="1086" height="377" alt="10a" src="https://github.com/user-attachments/assets/56c76d4b-aea9-4984-96af-871ee2935503" />

<img width="1355" height="262" alt="10b" src="https://github.com/user-attachments/assets/e3e2a004-ebb5-4efa-be41-07f26b83a3c7" />


## n8n Workflow Nodes

### 1. Webhook

The workflow begins with a **Webhook** that receives information from a potential client.

The incoming request contains:

* Client name
* Email address
* Company name
* Client message

### 2. Edit Fields

The first **Edit Fields** node prepares the incoming client information for AI processing.

### 3. Message a Model

The **Message a Model** node uses AI to analyze the client's inquiry.

The AI evaluates the client's message and generates relevant information, including:

* Lead type
* Priority
* Personalized AI response

### 4. Edit Fields

A second **Edit Fields** node prepares the AI-generated information for the routing and response stages.

### 5. Switch

The **Switch** node categorizes the lead based on the AI-generated lead type.

The workflow contains three routing paths:

* **Hot**
* **Warm**
* **Cold**

Each lead category is routed through the workflow before being combined again.

### 6. Merge

The **Merge** node combines the routed data back into a single workflow path.

This allows the different lead categories to continue through the same email and data-recording process.

### 7. Send a Message

The workflow uses **Gmail** to send the AI-generated response to the potential client.

This provides an automated and personalized follow-up based on the client's inquiry.

### 8. Append Row in Sheet

The processed lead information is recorded in **Google Sheets**.

This creates a structured record of the client, their company, inquiry, lead classification, priority, AI response, and email address.

### 9. Respond to Webhook

The workflow finishes by returning the processed client information through the **Respond to Webhook** node.

---

## Input

The workflow receives the following input through the Webhook:

```json id="3z0p7s"
{
  "body": {
    "name": "Sarah",
    "email": "baceromicah@gmail.com",
    "company": "Sarah's Boutique",
    "message": "Hi, I'm interested in your website design service. I'm comparing a few agencies right now and would like to know your pricing and what's included."
  }
}
```

## AI Lead Analysis

For the provided input:

```text id="7y1v9c"
Name    = Sarah
Company = Sarah's Boutique
Email   = baceromicah@gmail.com
```

The client is actively researching website design services and is comparing different agencies.

The AI classifies the inquiry as:

```text id="c5d8kn"
Lead Type = Warm
Priority  = Medium
```

The workflow therefore routes the lead through the **Warm** branch of the Switch node.

## AI-Generated Response

The AI generates a personalized response based on Sarah's inquiry:

```text id="6k2w1m"
Hi Sarah, thank you for reaching out to BrightWeb Digital Agency! We would love to help Sarah's Boutique stand out with a professional, high-converting website. Our design packages typically include custom UI/UX design, mobile responsiveness, basic SEO setup, and a user-friendly content management system. Since we tailor our services to each client's specific goals, I'd love to schedule a brief 15-minute discovery call to learn more about your vision so I can provide you with an accurate quote and a detailed breakdown of our deliverables. Are you available for a chat later this week?
```

The generated response is then sent to the client's email address.

## Output

The provided workflow execution produced:

```json id="1j7w5r"
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

## Lead Routing

The workflow uses the following lead categories:

| Lead Type | Switch Branch | Purpose                                                      |
| --------- | ------------- | ------------------------------------------------------------ |
| **Hot**   | Hot           | High-interest leads requiring strong follow-up               |
| **Warm**  | Warm          | Potential customers who are actively considering the service |
| **Cold**  | Cold          | Lower-interest leads requiring less immediate attention      |

The example inquiry is classified as **Warm** with **Medium** priority.

## Example

### Request

```json id="7x0n4q"
{
  "body": {
    "name": "Sarah",
    "email": "baceromicah@gmail.com",
    "company": "Sarah's Boutique",
    "message": "Hi, I'm interested in your website design service. I'm comparing a few agencies right now and would like to know your pricing and what's included."
  }
}
```

### Processing

```text id="2r5v9k"
Webhook
    ↓
Prepare Client Data
    ↓
AI Lead Analysis
    ↓
Lead Type: Warm
    ↓
Priority: Medium
    ↓
Warm Branch
    ↓
Merge
    ↓
Send Personalized Email
    ↓
Record Lead in Google Sheets
    ↓
Return Result
```

### Response

```json id="8h3p1z"
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

## Workflow Summary

| Step | Node                | Purpose                                  |
| ---- | ------------------- | ---------------------------------------- |
| 1    | Webhook             | Receives the client inquiry              |
| 2    | Edit Fields         | Prepares the incoming client data        |
| 3    | Message a Model     | Analyzes and qualifies the lead using AI |
| 4    | Edit Fields         | Prepares the AI-generated information    |
| 5    | Switch              | Routes the lead as Hot, Warm, or Cold    |
| 6    | Merge               | Combines the different lead paths        |
| 7    | Send a Message      | Sends the personalized AI response       |
| 8    | Append Row in Sheet | Records the lead information             |
| 9    | Respond to Webhook  | Returns the final processed lead         |

## Technologies Used

* **n8n**
* **Webhook**
* **Edit Fields**
* **AI Model**
* **Switch**
* **Merge**
* **Gmail**
* **Google Sheets**
* **Respond to Webhook**

## Project Purpose

This project demonstrates a **real-world, client-style business automation workflow** built with n8n.

It combines **AI lead qualification, conditional routing, automated email communication, and lead tracking** into one workflow.

The automation can help a digital agency process incoming inquiries by:

1. Capturing potential clients through a Webhook.
2. Using AI to understand and qualify each inquiry.
3. Assigning a **Hot, Warm, or Cold** lead type.
4. Determining the lead's priority.
5. Generating a personalized response.
6. Automatically emailing the potential client.
7. Recording the lead in Google Sheets.
8. Returning the complete processed lead information.

This project demonstrates how multiple automation services can be connected into a single **end-to-end AI-powered business workflow**.
