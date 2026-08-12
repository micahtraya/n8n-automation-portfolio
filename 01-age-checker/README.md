# 🔞 Age Checker Automation

## Overview

A simple webhook-based automation that receives a user's information and checks whether they meet a specified age requirement.

## Workflow

Webhook → IF → Allowed / Not Allowed → Respond to Webhook

## How It Works

1. The Webhook receives the user's information.
2. The IF node checks whether the user's age is 18 or older.
3. If the condition is true, the request goes to the Allowed path.
4. If the condition is false, the request goes to the Not Allowed path.
5. Respond to Webhook returns the result.

## Input

```json
{
  "name": "John",
  "age": 15
}
```

## Output

```json
[
  {
    "status": "Not Allowed",
    "message": "You are not eligible."
  }
]
```

## 📸 Workflow Screenshot

<img width="1166" height="606" alt="1" src="https://github.com/user-attachments/assets/23efbf8d-1298-45b7-9dc6-02bca2a13055" />


## Tools

* n8n
* Webhook
* IF Node
* JSON
* Postman

## What I Learned

* Creating webhook endpoints
* Receiving JSON data
* Using expressions in n8n
* Building conditional logic
* Testing workflows with Postman
* Returning webhook responses
