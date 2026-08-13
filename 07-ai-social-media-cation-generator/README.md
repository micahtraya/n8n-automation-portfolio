# Project 7 — AI Social Media Caption Generator

An **n8n workflow** that uses an AI model to automatically generate engaging social media captions based on product information.

The workflow receives product details through a **Webhook**, prepares the data, sends it to an AI model, and returns the generated caption through the Webhook response.

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
Respond to Webhook
```
<img width="862" height="527" alt="7" src="https://github.com/user-attachments/assets/021400ae-9c0b-4176-a8ad-382c127c607f" />

## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the product information.

The incoming request contains:

* Product name
* Product price

### 2. Edit Fields

The **Edit Fields** node prepares the incoming product data before it is passed to the AI model.

### 3. Message a Model

The **Message a Model** node sends the prepared product information to an AI model.

The AI generates an engaging social media caption based on the product and its price.

### 4. Respond to Webhook

The generated AI content is returned through the **Respond to Webhook** node.

---

## Input

The workflow receives the following input through the Webhook:

```json
{
  "body": {
    "product": "Gaming Mouse",
    "price": 50
  }
}
```

## AI Processing

For the provided input:

```text
Product = Gaming Mouse
Price   = $50
```

The product information is passed to the AI model, which generates a promotional social media caption.

## Output

The provided workflow execution produced the following AI-generated content:

```json
[
  {
    "content": {
      "parts": [
        {
          "text": "Stop missing your shots! 🎯 This pro Gaming Mouse is the ultimate setup upgrade for just $50. 🖱️"
        }
      ]
    }
  }
]
```

## Example

### Request

```json
{
  "body": {
    "product": "Gaming Mouse",
    "price": 50
  }
}
```

### Result

The product information is sent to the AI model, which generates a short, engaging promotional caption suitable for social media.

### Response

```json
[
  {
    "content": {
      "parts": [
        {
          "text": "Stop missing your shots! 🎯 This pro Gaming Mouse is the ultimate setup upgrade for just $50. 🖱️"
        }
      ]
    }
  }
]
```

## Workflow Summary

| Step | Node               | Purpose                                     |
| ---- | ------------------ | ------------------------------------------- |
| 1    | Webhook            | Receives product information                |
| 2    | Edit Fields        | Prepares the product data                   |
| 3    | Message a Model    | Generates the social media caption using AI |
| 4    | Respond to Webhook | Returns the AI-generated content            |

## Technologies Used

* **n8n**
* **Webhook**
* **Edit Fields**
* **AI Model**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **n8n can integrate AI into an automated content-generation workflow**.

Instead of manually writing social media captions for individual products, product information can be submitted through a Webhook and automatically transformed into an engaging promotional caption by an AI model.

This workflow can be extended to generate different types of marketing content, such as product descriptions, promotional posts, advertising copy, and social media captions.
