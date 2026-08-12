#  Customer Support Ticket Router ⭐⭐⭐⭐⭐⭐

## Overview

A webhook-based n8n automation that receives customer support requests and automatically routes each ticket based on the department and issue.

The workflow helps organize incoming customer inquiries by assigning the appropriate support team, determining ticket priority, estimating the response time, and setting the ticket status.

## Workflow

**Webhook → Ticket Routing → Respond to Webhook**

## How It Works

1. The Webhook receives the customer's support request.
2. The automation processes the customer's name, department, and issue.
3. The ticket is routed to the appropriate support team.
4. A priority level is assigned based on the issue.
5. An estimated response time is determined.
6. The ticket is marked with its current status.
7. Respond to Webhook returns the structured ticket information.

## Input

```json
{
  "customer_name": "Alex",
  "department": "general",
  "issue": "What are your business hours?"
}
```

## Output

```json
{
  "assigned_to": "Customer Service",
  "priority": "Low",
  "estimated_response": "24 Hours",
  "status": "Open"
}
```

## Example

**Customer:** Alex
**Department:** General
**Issue:** What are your business hours?

### Automated Result

* **Assigned To:** Customer Service
* **Priority:** Low
* **Estimated Response:** 24 Hours
* **Status:** Open

## Use Case

This automation can be useful for:

* Customer support teams
* Online businesses
* E-commerce stores
* Service-based businesses
* Help desk systems

Instead of manually reviewing every incoming request, the automation can immediately organize and route support tickets.

## Tools

* n8n
* Webhook
* JSON
* Ticket Routing Logic
* Respond to Webhook

## What I Learned

* Receiving customer support requests through a webhook
* Processing structured JSON data
* Building automated ticket-routing logic
* Assigning ticket priorities
* Generating estimated response times
* Returning structured webhook responses

## 📸 Workflow Screenshot

<img width="849" height="528" alt="image" src="https://github.com/user-attachments/assets/bfc79764-766e-434a-9cd5-7f20bf264d7f" />


## Project Status

✅ Completed and tested
