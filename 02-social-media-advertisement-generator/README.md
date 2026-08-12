# Project 2 - Social Media Advertisement Generator ⭐⭐⭐⭐⭐⭐

## Overview

A webhook-based n8n automation that receives product information and generates a short, engaging social media caption based on the product details.

This automation is designed to help businesses quickly create promotional copy for their products without manually writing a caption for every item.

## Workflow

**Webhook → Caption Generation → Respond to Webhook**

## How It Works

1. The Webhook receives product information.
2. The automation processes the product details, including the product name, category, price, and discount.
3. A promotional caption is generated based on the provided product information.
4. Respond to Webhook returns the original product data together with the generated caption.

## Input

```json
{
  "product": "socks",
  "category": "general",
  "price": 100.99,
  "discount": 20
}
```

## Output

```json
{
  "product": "socks",
  "category": "general",
  "price": 100.99,
  "discount": 20,
  "caption": "✨ Everyday essentials at prices you'll love."
}
```

## Example Generated Caption

> ✨ Everyday essentials at prices you'll love.

## Use Case

This automation can be used by:

* Online stores
* E-commerce businesses
* Social media marketers
* Affiliate marketers
* Small businesses

Instead of manually creating promotional captions, product information can be sent to the webhook and the automation generates a ready-to-use social media caption.

## Tools

* n8n
* Webhook
* AI Caption Generation
* JSON
* Respond to Webhook

## What I Learned

* Receiving product data through a webhook
* Working with JSON data in n8n
* Using product information as input for AI-generated content
* Creating automated marketing content
* Returning structured data through a webhook response
* Building reusable automation workflows

## 📸 Workflow Screenshot

<img width="852" height="529" alt="image" src="https://github.com/user-attachments/assets/a7512019-aa40-47d1-afe7-dbfdf71cb3d6" />

## Project Status

✅ Completed and tested
