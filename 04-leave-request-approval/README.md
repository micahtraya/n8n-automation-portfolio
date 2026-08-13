# Project 4 — Leave Request Approval

An **n8n workflow** that automates the approval process for employee leave requests based on the number of requested leave days.

The workflow receives an employee's leave request through a **Webhook**, extracts the request data, evaluates the number of leave days, and routes the request to the appropriate approval status.

## Workflow

```text
Webhook
   │
   ▼
Extract Request Data
   │
   ▼
IF: Days <= 3?
   ├── True  ──► Auto Approved ────────┐
   │                                   │
   └── False ─► Review Request         │
                  │                    │
                  ▼                    │
              IF: Days <= 7?           │
                  ├── True ─► Manager Approval
                  │                         │
                  └── False ─► Rejected ───┤
                                            ▼
                                   Respond to Webhook
```
<img width="855" height="533" alt="4" src="https://github.com/user-attachments/assets/a4204ca8-eb86-45df-88d6-282a68cae11f" />

## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the employee's leave request.

The incoming request contains:

* Employee name
* Department
* Leave type
* Number of leave days

### 2. Extract Request Data

The **Extract Request Data** node processes the information received from the Webhook and prepares it for the approval conditions.

### 3. IF: Days <= 3?

The first conditional node checks whether the requested leave is **3 days or fewer**.

* **True** → `Auto Approved`
* **False** → `Review Request`

### 4. Auto Approved

Requests for **3 days or fewer** are automatically approved.

### 5. Review Request

Requests exceeding 3 days continue to the next stage of the approval process.

### 6. IF: Days <= 7?

The workflow then checks whether the requested leave is **7 days or fewer**.

* **True** → `Manager Approval`
* **False** → `Rejected`

### 7. Manager Approval

Requests between **4 and 7 days** are sent for manager approval.

### 8. Rejected

Requests exceeding **7 days** are routed to the **Rejected** branch.

### 9. Respond to Webhook

All approval paths connect to the **Respond to Webhook** node, which returns the final leave request status.

---

## Input

The workflow receives the following input through the Webhook:

```json
{
  "body": {
    "employee": "popoy",
    "department": "HR",
    "leave_type": "Vacation",
    "days": 5
  }
}
```

## Approval Logic

For the provided input:

```text
Employee   = popoy
Department = HR
Leave Type = Vacation
Days       = 5
```

The first condition checks:

```text
5 <= 3
```

This evaluates to **false**, so the request continues to the review stage.

The second condition checks:

```text
5 <= 7
```

This evaluates to **true**, so the workflow routes the request to:

```text
Manager Approval
```

The request therefore receives a **Pending** status while waiting for manager approval.

## Output

The resulting leave request information is:

```json
[
  {
    "employee": "popoy",
    "status": "Pending",
    "approver": "Manager",
    "message": "Waiting for manager approval"
  }
]
```

## Workflow Summary

| Step | Node                 | Purpose                                       |
| ---- | -------------------- | --------------------------------------------- |
| 1    | Webhook              | Receives the employee's leave request         |
| 2    | Extract Request Data | Processes the request information             |
| 3    | IF: Days <= 3?       | Checks for automatic approval                 |
| 4    | Auto Approved        | Automatically approves short leave requests   |
| 5    | Review Request       | Handles requests requiring further evaluation |
| 6    | IF: Days <= 7?       | Determines manager approval or rejection      |
| 7    | Manager Approval     | Routes eligible requests to the manager       |
| 8    | Rejected             | Handles requests exceeding 7 days             |
| 9    | Respond to Webhook   | Returns the final request status              |

## Approval Rules

| Requested Leave      | Workflow Result  |
| -------------------- | ---------------- |
| **3 days or fewer**  | Auto Approved    |
| **4–7 days**         | Manager Approval |
| **More than 7 days** | Rejected         |

## Example

### Request

```json
{
  "body": {
    "employee": "popoy",
    "department": "HR",
    "leave_type": "Vacation",
    "days": 5
  }
}
```

### Result

The employee requested **5 days** of vacation leave.

Since 5 days is greater than 3 but less than or equal to 7, the workflow routes the request to **Manager Approval**.

### Response

```json
[
  {
    "employee": "popoy",
    "status": "Pending",
    "approver": "Manager",
    "message": "Waiting for manager approval"
  }
]
```

## Technologies Used

* **n8n**
* **Webhook**
* **Edit/Extract Fields**
* **IF Node**
* **Conditional Routing**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **n8n conditional logic** can automate an employee leave approval workflow.

By defining approval thresholds, the workflow can automatically handle short leave requests, send medium-length requests to a manager, and reject requests that exceed the defined limit.

This reduces manual processing and creates a consistent, rule-based leave approval process.
