# 🏖️ Leave Request Approval Automation

## Overview

A webhook-based n8n automation that receives employee leave requests and automatically determines whether the request should be approved or rejected based on the number of requested leave days.

This automation helps organizations process leave requests consistently and reduce manual approval work.

## Workflow

**Webhook → Leave Validation → Approval/Rejection → Respond to Webhook**

## How It Works

1. The Webhook receives the employee's leave request.
2. The automation processes the employee, department, leave type, and requested number of days.
3. The leave request is evaluated against the allowed leave limit.
4. If the requested leave exceeds the maximum allowed days, the request is rejected.
5. The automation provides a reason for the rejection.
6. Respond to Webhook returns the final leave request status.

## Input

```json
{
  "employee": "popoy",
  "department": "HR",
  "leave_type": "Vacation",
  "days": 15
}
```

## Output

```json
{
  "employee": "popoy",
  "status": "Rejected",
  "reason": "Maximum leave exceeded."
}
```

## Example

**Employee:** Popoy
**Department:** HR
**Leave Type:** Vacation
**Requested Days:** 15

### Automated Result

* **Status:** Rejected
* **Reason:** Maximum leave exceeded.

## Use Case

This automation can be useful for:

* Human Resources departments
* Employee leave management
* Small and medium-sized businesses
* Internal approval systems
* Automated HR workflows

It can help HR teams automatically evaluate leave requests and provide consistent decisions based on predefined business rules.

## Tools

* n8n
* Webhook
* Conditional Logic
* JSON
* Respond to Webhook

## What I Learned

* Receiving employee requests through a webhook
* Processing structured JSON data
* Building rule-based approval logic
* Using conditional logic in n8n
* Handling approved and rejected requests
* Returning structured webhook responses

## 📸 Workflow Screenshot

<img width="840" height="537" alt="image" src="https://github.com/user-attachments/assets/f896f5a2-2584-4eb7-b417-6fa8cc87095b" />

## Project Status

✅ Completed and tested
