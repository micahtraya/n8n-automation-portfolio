#  Project 2 - Social Media Advertisement Generator ⭐⭐⭐⭐⭐⭐

A webhook-based n8n automation that receives product information and generates a short, engaging social media caption based on the product category and details.

This automation is designed to help businesses quickly create promotional copy for different types of products by automatically routing them to the appropriate advertisement style.

---

##  Workflow

Webhook → Edit Fields → IF - Electronics → Tech-focused / IF → Beauty-focused / Others → General Promotion → Respond to Webhook

---

##  Objective

The goal of this project is to create an automated social media advertisement generator that can adjust promotional content based on the product category.

The workflow receives product information through a webhook, prepares the data using Edit Fields, checks the product category using conditional logic, and routes the product to the appropriate promotional path.

Electronics products receive a **Tech-focused advertisement**, beauty products receive a **Beauty-focused advertisement**, while other product categories receive a **General promotional advertisement**.

---

##  How It Works

1. The Webhook receives product information.
2. The Edit Fields node prepares and organizes the incoming product data.
3. The first IF node checks whether the product belongs to the **Electronics** category.
4. If the product is Electronics, it follows the **Tech-focused ad** path.
5. If it is not Electronics, the second IF node checks the product category.
6. Beauty products follow the **Beauty-focused ad** path.
7. Other product categories follow the **Others → General promotion** path.
8. The selected advertisement is sent to the Respond to Webhook node.
9. Respond to Webhook returns the generated promotional content.

---

##  Category Routing

### 💻 Electronics

Electronics products are routed to a technology-focused advertisement.

    Electronics
        ↓
    IF - Electronics
        ↓
    Tech-focused ad

### 💄 Beauty

Beauty products are routed to a beauty-focused advertisement.

    Beauty
       ↓
    IF
       ↓
    Beauty-focused ad

### 🛍️ Other Products

Products that are neither Electronics nor Beauty are routed to a general promotional advertisement.

    Other Category
         ↓
       IF
         ↓
    Others → General promotion

---

##  Input

The workflow receives product information through a **Webhook**.

### Example Input

    {
      "product": "socks",
      "category": "general",
      "price": 100.99,
      "discount": 20
    }

---

##  Output

The selected promotional path generates a caption based on the product information and returns the result through the Respond to Webhook node.

### Example Output

    {
      "product": "socks",
      "category": "general",
      "price": 100.99,
      "discount": 20,
      "caption": "✨ Everyday essentials at prices you'll love."
    }

---

##  Example Generated Caption

> ✨ Everyday essentials at prices you'll love.

---

##  Testing

The workflow can be tested by sending product information to the Webhook.

### Request

**Method:**

    POST

### Example Test Data

    {
      "product": "socks",
      "category": "general",
      "price": 100.99,
      "discount": 20
    }

### Expected Process

    Postman
       ↓
    Webhook
       ↓
    Edit Fields
       ↓
    IF - Electronics
       ├── True
       │    ↓
       │  Tech-focused ad
       │
       └── False
              ↓
             IF
              ├── True
              │    ↓
              │  Beauty-focused ad
              │
              └── False
                   ↓
              Others → General promotion
                         ↓
                  Respond to Webhook

---

##  Workflow Screenshot

<img width="852" height="529" alt="2" src="https://github.com/user-attachments/assets/b826a3f9-fa32-4ffa-926c-4268758f4604" />


---

##  Technologies Used

- **n8n** — Workflow automation
- **Webhook** — Receives product information
- **Edit Fields** — Prepares and organizes product data
- **IF Node** — Routes products based on category
- **Tech-focused Ad** — Generates technology-related promotional content
- **Beauty-focused Ad** — Generates beauty-related promotional content
- **General Promotion** — Handles other product categories
- **JSON** — Data format
- **Respond to Webhook** — Returns the generated advertisement

---

##  Example Use Cases

This automation can be used by:

- Online stores
- E-commerce businesses
- Social media marketers
- Affiliate marketers
- Small businesses
- Product-based businesses

Instead of manually deciding how to promote each product, product information can be sent to the webhook and the automation automatically routes it to the appropriate advertisement style.

---

##  Skills Demonstrated

This project demonstrates experience with:

- Creating webhook endpoints
- Receiving product data through webhooks
- Working with JSON data in n8n
- Using Edit Fields for data preparation
- Building conditional logic with IF nodes
- Creating category-based workflow routing
- Generating different promotional content based on product type
- Working with multiple workflow branches
- Returning structured data through a webhook response
- Building reusable marketing automation workflows
- Testing workflows with Postman

---

##  Future Improvements

Possible improvements for future versions:

- Add more product categories
- Add separate advertisements for Fashion products
- Add separate advertisements for Food products
- Add automatic hashtag generation
- Add multiple caption variations
- Add platform-specific captions for TikTok, Instagram, and Facebook
- Add AI-generated promotional content
- Add product image processing
- Add automatic social media publishing
- Add scheduled advertisement posting

---

##  Project Status

**Status:** ✅ Completed and tested

**Project:** #2

**Difficulty:** ⭐⭐⭐⭐⭐⭐

**Category:** Marketing Automation / Conditional Logic

**Automation Type:** Social Media Advertisement Generation

---

##  Portfolio

This project is part of my **n8n Automation Portfolio**, demonstrating practical experience building category-based marketing automation workflows using webhooks, data preparation, conditional routing, promotional content generation, JSON processing, and automated webhook responses.
