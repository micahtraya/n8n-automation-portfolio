# Project 2 — Social Media Advertisement Generator

An **n8n workflow** that generates a social media advertisement based on a product's **category, price, and discount**.

The workflow receives product information through a **Webhook**, processes the product details, determines the appropriate advertising path based on the product category, and returns a formatted social media advertisement.

## Workflow

```text
Webhook
   │
   ▼
Edit Fields
   │
   ▼
If - Electronics
   ├── True  ─────────► Tech-focused ad ──────┐
   │                                          │
   └── False ─► If ──────────────────────────┤
                  ├── True ─► Beauty-focused ad
                  │                         │
                  └── False ► Others → General promotion
                                            │
                                            ▼
                                   Respond to Webhook
```
<img width="847" height="538" alt="2" src="https://github.com/user-attachments/assets/ee820da9-84d5-4b0e-af5b-f6759ad5e9e2" />

## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the product information.

### 2. Edit Fields

The incoming product data is prepared for the following workflow logic.

### 3. If - Electronics

The workflow first checks whether the product belongs to the **electronics** category.

* **True** → `Tech-focused ad`
* **False** → Continue to the next category check

### 4. If

Products that are not categorized as electronics are evaluated by another conditional node.

The workflow determines whether the product belongs to the **beauty** category.

* **True** → `Beauty-focused ad`
* **False** → `Others → General promotion`

### 5. Advertisement Generation

Depending on the product category, the workflow routes the data to an appropriate advertisement format:

* **Electronics** → Tech-focused ad
* **Beauty** → Beauty-focused ad
* **Other categories** → General promotion

### 6. Respond to Webhook

The selected advertisement is returned through the **Respond to Webhook** node.

---

## Input

The workflow receives the following input through the Webhook:

```json
{
  "body": {
    "product": "cojic",
    "category": "beauty",
    "price": 100.99,
    "discount": 20
  }
}
```

## Category Logic

For the provided input:

```text
Product  = cojic
Category = beauty
Price    = 100.99
Discount = 20
```

The first condition checks whether the category is **electronics**.

Since:

```text
beauty ≠ electronics
```

the workflow continues to the next condition.

The second condition identifies the product as **beauty**, so the workflow follows:

```text
Beauty-focused ad
```

## Output

The generated advertisement for the provided example is:

```json
[
  {
    "title": "✨ Look Amazing Every Day!",
    "description": "Don't miss today's beauty essentials at an incredible discount!",
    "price": "100.99",
    "discount": "20",
    "hashtag": "#BeautyFinds #TikTokMadeMeBuyIt",
    "call_to_action": "Order Yours Today!"
  }
]
```

## Workflow Summary

| Step | Node                       | Purpose                                   |
| ---- | -------------------------- | ----------------------------------------- |
| 1    | Webhook                    | Receives product information              |
| 2    | Edit Fields                | Prepares the incoming product data        |
| 3    | If - Electronics           | Checks whether the product is electronics |
| 4    | If                         | Checks whether the product is beauty      |
| 5    | Tech-focused ad            | Handles electronics advertisements        |
| 6    | Beauty-focused ad          | Handles beauty advertisements             |
| 7    | Others → General promotion | Handles other product categories          |
| 8    | Respond to Webhook         | Returns the generated advertisement       |

## Example

### Request

```json
{
  "body": {
    "product": "cojic",
    "category": "beauty",
    "price": 100.99,
    "discount": 20
  }
}
```

### Result

Because the product category is **beauty**, the workflow follows the **Beauty-focused ad** branch.

### Response

```json
[
  {
    "title": "✨ Look Amazing Every Day!",
    "description": "Don't miss today's beauty essentials at an incredible discount!",
    "price": "100.99",
    "discount": "20",
    "hashtag": "#BeautyFinds #TikTokMadeMeBuyIt",
    "call_to_action": "Order Yours Today!"
  }
]
```

## Technologies Used

* **n8n**
* **Webhook**
* **Edit Fields**
* **IF Node**
* **Conditional Routing**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **n8n conditional routing** can be used to create category-specific social media advertisements.

It shows how a single webhook request can be evaluated against multiple conditions and routed to different advertisement-generation paths based on the product category.
