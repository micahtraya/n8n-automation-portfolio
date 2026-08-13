# Project 8 — AI Customer Support Assistant

An **n8n workflow** that uses AI to assist with customer support requests and automatically send a response to the customer through email.

The workflow receives a customer's support request through a **Webhook**, prepares the information, sends it to an AI model to generate a suitable response, and then uses **Gmail** to send the generated message to the customer.

## Workflow

```text id="6o9wqv"
Webhook
   │
   ▼
Edit Fields
   │
   ▼
Message a Model
   │
   ▼
Send a Message
   │
   ▼
Respond to Webhook
```
<img width="867" height="534" alt="8" src="https://github.com/user-attachments/assets/0cee59c4-053d-43f9-b6af-958cd9ef673b" />

<img width="1072" height="498" alt="8a" src="https://github.com/user-attachments/assets/a72b96e3-c2d2-42aa-a214-b3e00eb442db" />


## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the customer's support request.

The incoming request contains:

* Customer name
* Customer email
* Support subject
* Customer message

### 2. Edit Fields

The **Edit Fields** node prepares the customer information and support request before passing it to the AI model.

### 3. Message a Model

The **Message a Model** node processes the customer's request using an AI model.

The AI analyzes the issue and generates an appropriate customer support response.

### 4. Send a Message

The generated response is sent to the customer using the **Gmail** node.

This allows the workflow to automatically communicate with the customer without requiring a support agent to manually write the initial response.

### 5. Respond to Webhook

After the email is sent, the workflow returns the execution result through the **Respond to Webhook** node.

---

## Input

The workflow receives the following input through the Webhook:

```json id="g6d3q8"
{
  "body": {
    "customer": "Micah",
    "email": "micahtraya16@gmail.com",
    "subject": "Wrong item received",
    "message": "Hi, I ordered a wireless mouse but received a keyboard. Can you help me?"
  }
}
```

## AI Processing

For the provided input:

```text id="0q6z3n"
Customer = Micah
Email    = micahtraya16@gmail.com
Subject  = Wrong item received
Issue    = Customer received a keyboard instead of a wireless mouse
```

The customer message is passed to the AI model.

The AI is responsible for understanding the customer's issue and generating an appropriate support response.

The generated response is then passed to the Gmail node for delivery.

## Output

The provided workflow execution produced the following output:

```json id="v4m7x2"
[
  {
    "id": "19fe1ea3c117bfbe",
    "threadId": "19fe1ea3c117bfbe",
    "labelIds": [
      "SENT"
    ]
  }
]
```

The returned Gmail data confirms that the generated customer support message was sent successfully.

## Example

### Request

```json id="8j2p6r"
{
  "body": {
    "customer": "Micah",
    "email": "micahtraya16@gmail.com",
    "subject": "Wrong item received",
    "message": "Hi, I ordered a wireless mouse but received a keyboard. Can you help me?"
  }
}
```

### Result

The AI model processes the customer's complaint about receiving the wrong product and generates a customer support response.

The response is then sent to the customer's email address using Gmail.

### Response

```json id="w5n1cs"
[
  {
    "id": "19fe1ea3c117bfbe",
    "threadId": "19fe1ea3c117bfbe",
    "labelIds": [
      "SENT"
    ]
  }
]
```

## Workflow Summary

| Step | Node               | Purpose                                      |
| ---- | ------------------ | -------------------------------------------- |
| 1    | Webhook            | Receives the customer support request        |
| 2    | Edit Fields        | Prepares the customer and issue information  |
| 3    | Message a Model    | Generates an AI-powered support response     |
| 4    | Send a Message     | Sends the response to the customer via Gmail |
| 5    | Respond to Webhook | Returns the email execution result           |

## Technologies Used

* **n8n**
* **Webhook**
* **Edit Fields**
* **AI Model**
* **Gmail**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **AI and workflow automation can be combined to handle customer support requests**.

Instead of requiring a support agent to manually review every initial inquiry and compose a response, the workflow uses an AI model to understand the customer's issue and generate a response automatically.

The workflow can be extended with additional steps such as **ticket classification, order verification, escalation to human agents, FAQ lookup, or customer database integration**.
