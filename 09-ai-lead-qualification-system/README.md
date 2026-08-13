# Project 9 — AI Lead Qualification System

An **n8n workflow** that uses AI to process and qualify potential business leads, record the lead information, and send an automated email response.

The workflow receives lead information through a **Webhook**, prepares the data, uses an AI model to evaluate the lead, records the result in **Google Sheets**, and sends a message through **Gmail**.

## Workflow

```text
Webhook
   │
   ▼
Edit Fields
   │
   ▼
Message a Model
   │
   ▼
Append row in sheet
   │
   ▼
Send a message
   │
   ▼
Respond to Webhook
```
<img width="862" height="526" alt="9" src="https://github.com/user-attachments/assets/d54d6f42-1cbf-4bd1-91c1-43aabec83729" />
<img width="1099" height="351" alt="9a" src="https://github.com/user-attachments/assets/7c35db44-fa5e-4cb5-a8a0-bdeabf3ed4db" />
<img width="1363" height="300" alt="9b" src="https://github.com/user-attachments/assets/2b8c7a20-f26d-4970-8c31-582cd8d152ed" />

## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives information about a potential lead.

The incoming request contains:

* Lead name
* Email address
* Company name
* Message or inquiry

### 2. Edit Fields

The **Edit Fields** node prepares the incoming lead information before it is passed to the AI model.

### 3. Message a Model

The **Message a Model** node uses AI to analyze the lead's inquiry.

The AI can evaluate the intent of the potential customer and determine whether the inquiry represents a potential business opportunity.

### 4. Append row in sheet

After the AI processes the lead, the workflow uses **Google Sheets** to append the lead information to a spreadsheet.

This creates a centralized record of incoming leads and their qualification results.

### 5. Send a Message

The workflow uses **Gmail** to send an automated message based on the processed lead information.

This allows potential customers to receive a response without requiring the lead to be handled manually.

### 6. Respond to Webhook

The workflow finishes by returning the execution result through the **Respond to Webhook** node.

---

## Input

The workflow receives the following input through the Webhook:

```json
{
  "body": {
    "name": "John",
    "email": "baceromicah@gmail.com",
    "company": "John's Store",
    "message": "Hello, I was just curious about what kind of website services your company offers. Maybe I'll need one someday."
  }
}
```

## Lead Processing

For the provided input:

```text
Name    = John
Email   = baceromicah@gmail.com
Company = John's Store
Message = Hello, I was just curious about what kind of website services your company offers. Maybe I'll need one someday.
```

The lead information is passed to the AI model for analysis.

The inquiry shows that the potential customer is **asking about website services** and may require a website in the future.

The workflow then continues by recording the lead information in Google Sheets and sending a message through Gmail.

## Output

The provided workflow execution produced the following output:

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

The output confirms that the Gmail message was successfully sent.

## Example

### Request

```json
{
  "body": {
    "name": "John",
    "email": "baceromicah@gmail.com",
    "company": "John's Store",
    "message": "Hello, I was just curious about what kind of website services your company offers. Maybe I'll need one someday."
  }
}
```

### Result

The workflow receives John's inquiry and sends the information to the AI model for processing.

The lead is then recorded in Google Sheets, followed by an automated email response.

### Response

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

## Workflow Summary

| Step | Node                | Purpose                               |
| ---- | ------------------- | ------------------------------------- |
| 1    | Webhook             | Receives potential lead information   |
| 2    | Edit Fields         | Prepares the lead data                |
| 3    | Message a Model     | Uses AI to analyze the lead           |
| 4    | Append row in sheet | Records the lead in Google Sheets     |
| 5    | Send a message      | Sends an automated email              |
| 6    | Respond to Webhook  | Returns the workflow execution result |

## Technologies Used

* **n8n**
* **Webhook**
* **Edit Fields**
* **AI Model**
* **Google Sheets**
* **Gmail**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **AI can be integrated into a lead qualification and follow-up workflow**.

Instead of manually reviewing every incoming inquiry, the workflow can use AI to understand the potential customer's intent, store the lead information in **Google Sheets**, and automatically send a follow-up message through **Gmail**.

This creates a simple automated pipeline for capturing, analyzing, recording, and responding to potential business leads.
