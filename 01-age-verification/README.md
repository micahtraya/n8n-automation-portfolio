# Project 1 — Age Verification

An **n8n workflow** that performs a simple age verification check using data received through a Webhook.

The workflow checks whether the submitted age is **18 or older** and routes the request through either an **Allowed** or **Not Allowed** branch before returning a response through the Webhook.

## Workflow

```text
Webhook
   │
   ▼
IF: Age >= 18?
   ├── True  ──► Allowed ────────┐
   │                             │
   └── False ─► Not Allowed ────┤
                                 ▼
                         Respond to Webhook
```

<img width="1166" height="606" alt="1" src="https://github.com/user-attachments/assets/0cc6d312-901e-468a-a1f1-d042bca609b0" />


## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the incoming request.

### 2. IF: Age >= 18

The submitted age is evaluated using the condition:

```text
Age >= 18
```

The workflow has two possible paths:

* **True** → `Allowed`
* **False** → `Not Allowed`

### 3. Allowed

If the submitted age is **18 or older**, the request follows the **Allowed** branch.

### 4. Not Allowed

If the submitted age is **below 18**, the request follows the **Not Allowed** branch.

### 5. Respond to Webhook

Both branches connect to the **Respond to Webhook** node, which returns the workflow response.

---

## Input

The workflow receives the following input through the Webhook:

```json
{
  "body": {
    "name": "John",
    "age": 15
  }
}
```

## Age Verification Logic

For the provided input:

```text
Age = 15
```

The condition is:

```text
15 >= 18
```

This evaluates to:

```text
false
```

Therefore, the workflow follows the:

```text
Not Allowed
```

branch.

## Output

The output for the provided example is:

```json
[
  {
    "name": "John",
    "age": 15
  }
]
```

## Workflow Summary

| Step | Node               | Purpose                                       |
| ---- | ------------------ | --------------------------------------------- |
| 1    | Webhook            | Receives the user's name and age              |
| 2    | IF: Age >= 18      | Checks whether the age is at least 18         |
| 3    | Allowed            | Handles requests where the condition is true  |
| 4    | Not Allowed        | Handles requests where the condition is false |
| 5    | Respond to Webhook | Returns the workflow response                 |

## Example

### Request

```json
{
  "body": {
    "name": "John",
    "age": 15
  }
}
```

### Result

Since John's age is **15**, the condition `Age >= 18` is false, so the workflow follows the **Not Allowed** path.

### Response

```json
[
  {
    "name": "John",
    "age": 15
  }
]
```

## Technologies Used

* **n8n**
* **Webhook**
* **IF Node**
* **Respond to Webhook**

## Project Purpose

This project demonstrates a basic **conditional workflow in n8n**, using webhook input and an age-based decision to route data through different workflow branches.

It is a simple example of how n8n can be used to build **automation workflows, conditional logic, and webhook-based processes**.
