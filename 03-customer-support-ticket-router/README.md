# Project 3 — Customer Support Ticket Router

An **n8n workflow** that automatically routes customer support tickets to the appropriate team based on the customer's selected department.

The workflow receives a customer support request through a **Webhook**, checks the department, routes the ticket to the appropriate support team, and returns the ticket assignment and response information.

## Workflow

```text
Webhook
   │
   ▼
If
   ├── True ─────────► Technical Support ───────┐
   │                                            │
   └── False ─► Is Billing?                     │
                  ├── True ─► Billing Team ────┤
                  │                             │
                  └── False ► General Inquiry ─┤
                                                ▼
                                        Respond to Webhook
```
<img width="846" height="535" alt="3" src="https://github.com/user-attachments/assets/1798cc53-9714-49da-9d04-2f5f592f5427" />

## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the customer's support ticket.

The incoming request contains:

* Customer name
* Department
* Issue

### 2. If

The first conditional node evaluates the incoming department and determines whether the request should be routed to **Technical Support**.

* **True** → `technical support`
* **False** → Continue to the billing check

### 3. Is Billing?

If the ticket is not routed to Technical Support, the workflow checks whether the department is **billing**.

* **True** → `Billing Team`
* **False** → `General Inquiry`

### 4. Technical Support

Tickets that match the technical-support condition are routed to the **Technical Support** branch.

### 5. Billing Team

Tickets identified as billing requests are routed to the **Billing Team**.

### 6. General Inquiry

Tickets that do not match the previous conditions are routed to **General Inquiry**.

### 7. Respond to Webhook

All routing branches connect to the **Respond to Webhook** node, which returns the ticket assignment and status information.

---

## Input

The workflow receives the following input through the Webhook:

```json
{
  "body": {
    "customer_name": "badetha",
    "department": "billing",
    "issue": "Refund request"
  }
}
```

## Ticket Routing Logic

For the provided input:

```text
Customer  = badetha
Department = billing
Issue      = Refund request
```

The ticket is identified as a **billing** request.

Therefore, the workflow follows the:

```text
Billing Team
```

branch.

## Output

The resulting customer support ticket information is:

```json
[
  {
    "assigned_to": "Billing Department",
    "priority": "Medium",
    "estimated_response": "4 Hours",
    "status": "Open"
  }
]
```

## Workflow Summary

| Step | Node               | Purpose                                         |
| ---- | ------------------ | ----------------------------------------------- |
| 1    | Webhook            | Receives the customer support ticket            |
| 2    | If                 | Checks the first routing condition              |
| 3    | Technical Support  | Handles technical support requests              |
| 4    | Is Billing?        | Checks whether the ticket is related to billing |
| 5    | Billing Team       | Handles billing requests                        |
| 6    | General Inquiry    | Handles other requests                          |
| 7    | Respond to Webhook | Returns the ticket routing result               |

## Example

### Request

```json
{
  "body": {
    "customer_name": "badetha",
    "department": "billing",
    "issue": "Refund request"
  }
}
```

### Result

Because the department is **billing**, the workflow routes the ticket to the **Billing Team**.

### Response

```json
[
  {
    "assigned_to": "Billing Department",
    "priority": "Medium",
    "estimated_response": "4 Hours",
    "status": "Open"
  }
]
```

## Technologies Used

* **n8n**
* **Webhook**
* **IF Node**
* **Conditional Routing**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **n8n conditional routing** can automate customer support ticket assignment.

Instead of manually reviewing every ticket, the workflow evaluates the department and automatically directs the request to **Technical Support, Billing Team, or General Inquiry**, making the support process more organized and efficient.
