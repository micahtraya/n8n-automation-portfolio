# Project 5 — TikTok Affiliate Content Generator

An **n8n workflow** that generates TikTok affiliate marketing content based on a product's category, price, and discount.

The workflow receives product information through a **Webhook**, identifies the product category, routes the request to the appropriate content template, and returns a ready-to-use TikTok affiliate caption, hashtags, and call-to-action.

## Workflow

```text id="t8g7fk"
Webhook
   │
   ▼
Edit Fields
   │
   ▼
IF: Electronics?
   ├── True  ──► Electronics Template ──────┐
   │                                        │
   └── False ─► IF: Beauty?                 │
                  ├── True  ─► Beauty Template
                  │                         │
                  └── False ► Others Template
                                            │
                                            ▼
                                   Respond to Webhook
```
<img width="872" height="533" alt="5" src="https://github.com/user-attachments/assets/a885db3e-be7e-4433-afec-684c68ef35b9" />

## n8n Workflow Nodes

### 1. Webhook

The workflow starts with a **Webhook** node that receives the product information.

The incoming request contains:

* Product name
* Product category
* Price
* Discount

### 2. Edit Fields

The **Edit Fields** node prepares the incoming product data for the category-based routing logic.

### 3. IF: Electronics?

The first conditional node checks whether the product belongs to the **electronics** category.

* **True** → `Electronics Template`
* **False** → Continue to the next category check

### 4. Electronics Template

Electronics products are routed to the **Electronics Template**, which generates promotional content focused on technology and electronics deals.

### 5. IF: Beauty?

Products that are not categorized as electronics are evaluated by a second condition.

* **True** → `Beauty Template`
* **False** → `Others Template`

### 6. Beauty Template

Beauty products are routed to the **Beauty Template** for category-specific promotional content.

### 7. Others Template

Products that do not match the electronics or beauty categories are routed to the **Others Template**.

### 8. Respond to Webhook

All three content-generation branches connect to the **Respond to Webhook** node, which returns the generated TikTok affiliate content.

---

## Input

The workflow receives the following input through the Webhook:

```json id="8yq9l2"
{
  "body": {
    "product_name": "Wireless Earbuds",
    "category": "electronics",
    "price": 1299,
    "discount": 50
  }
}
```

## Category Logic

For the provided input:

```text id="d8ecp5"
Product  = Wireless Earbuds
Category = electronics
Price    = 1299
Discount = 50
```

The workflow checks:

```text id="1j5x9n"
Category = electronics
```

The condition is **true**, so the workflow routes the product to:

```text id="5p8m3r"
Electronics Template
```

The template then generates TikTok affiliate promotional content using the product information and discount.

## Output

The generated TikTok affiliate content is:

```json id="y4j0s6"
[
  {
    "body": {
      "product_name": "Wireless Earbuds"
    },
    "caption": "🎧 Upgrade your music experience with Wireless Earbuds! Now 50% OFF for a limited time!",
    "hashtags": "#TikTokFinds #TechDeals #Electronics #Sale",
    "call_to_action": "🛒 Check the product in my TikTok Shop before the promo ends!"
  }
]
```

## Workflow Summary

| Step | Node                 | Purpose                                   |
| ---- | -------------------- | ----------------------------------------- |
| 1    | Webhook              | Receives product information              |
| 2    | Edit Fields          | Prepares the product data                 |
| 3    | IF: Electronics?     | Checks whether the product is electronics |
| 4    | Electronics Template | Generates electronics-focused content     |
| 5    | IF: Beauty?          | Checks whether the product is beauty      |
| 6    | Beauty Template      | Generates beauty-focused content          |
| 7    | Others Template      | Handles other product categories          |
| 8    | Respond to Webhook   | Returns the generated TikTok content      |

## Content Routing Rules

| Product Category     | Content Template     |
| -------------------- | -------------------- |
| **Electronics**      | Electronics Template |
| **Beauty**           | Beauty Template      |
| **Other categories** | Others Template      |

## Example

### Request

```json id="l9l1j4"
{
  "body": {
    "product_name": "Wireless Earbuds",
    "category": "electronics",
    "price": 1299,
    "discount": 50
  }
}
```

### Result

Because the product category is **electronics**, the workflow routes the request to the **Electronics Template**.

The workflow generates promotional content emphasizing the product, its **50% discount**, relevant TikTok hashtags, and a call-to-action directing customers to the TikTok Shop.

### Response

```json id="2n4s8k"
[
  {
    "body": {
      "product_name": "Wireless Earbuds"
    },
    "caption": "🎧 Upgrade your music experience with Wireless Earbuds! Now 50% OFF for a limited time!",
    "hashtags": "#TikTokFinds #TechDeals #Electronics #Sale",
    "call_to_action": "🛒 Check the product in my TikTok Shop before the promo ends!"
  }
]
```

## Technologies Used

* **n8n**
* **Webhook**
* **Edit Fields**
* **IF Node**
* **Conditional Routing**
* **Content Templates**
* **Respond to Webhook**

## Project Purpose

This project demonstrates how **n8n conditional routing** can be used to automate the creation of **TikTok affiliate marketing content**.

Instead of manually creating promotional captions for every product, the workflow identifies the product category and selects an appropriate content template. This creates a simple, reusable automation for generating product captions, hashtags, and calls-to-action for affiliate marketing.
