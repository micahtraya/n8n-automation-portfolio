# Project 7 — AI Social Media Caption Generator ⭐⭐⭐⭐⭐⭐

An n8n automation workflow that uses **OpenAI** to automatically generate engaging social media captions from simple product information.

This project demonstrates how to connect a webhook to an AI model and transform structured product data into ready-to-use social media content.

---

## 🚀 Workflow

```text
Webhook
   │
   ▼
OpenAI
   │
   ▼
Generate Caption
   │
   ▼
Respond to Webhook
```

### 📸 Workflow Screenshot

<img width="859" height="520" alt="image" src="https://github.com/user-attachments/assets/f366f474-0d34-42b2-9770-563df7c7930c" />

---

## 🎯 Objective

The goal of this project is to automate the creation of short, engaging product captions for social media platforms such as:

* TikTok
* Instagram
* Facebook
* Other social media platforms

Instead of manually writing a caption for every product, the workflow sends the product information to OpenAI and generates a promotional caption automatically.

---

## 📥 Input

The workflow receives product information through a **Webhook** using a `POST` request.

### Example Input

```json
{
  "product": "Gaming Mouse",
  "price": 50
}
```

---

## 🤖 AI Processing

The OpenAI node receives the product information and generates a short promotional caption.

The AI prompt instructs the model to:

* Create an attention-grabbing hook
* Mention the product
* Include the product price
* Make the caption suitable for social media
* Keep the caption short
* Use engaging language
* Include emojis

---

## 📤 Output

### Example Output

```json
{
  "text": "Stop missing your shots! 🎯 This pro Gaming Mouse is the ultimate setup upgrade for just $50. 🖱️"
}
```

---

## 🧩 Technologies Used

* **n8n** — Workflow automation
* **Webhook** — Receives product information
* **OpenAI** — Generates the social media caption
* **Postman** — Used for API testing
* **JSON** — Data format

---

## 🔄 How It Works

### 1. Webhook

The Webhook receives the product and price.

```json
{
  "product": "Gaming Mouse",
  "price": 50
}
```

### 2. OpenAI

The product information is passed to OpenAI.

The AI analyzes the information and creates an engaging promotional caption.

### 3. Generate Caption

The generated AI response becomes the final social media caption.

### 4. Respond to Webhook

The workflow returns the generated caption as a response.

---

## 🧪 Testing

The workflow can be tested using **Postman**.

### Request

**Method:**

```text
POST
```

**Example Body:**

```json
{
  "product": "Gaming Mouse",
  "price": 50
}
```

### Expected Response

```json
{
  "text": "Stop missing your shots! 🎯 This pro Gaming Mouse is the ultimate setup upgrade for just $50. 🖱️"
}
```

---

## 💡 Example Use Cases

This automation can be used for:

* TikTok affiliate marketing
* E-commerce product promotion
* Social media content automation
* Product listing automation
* Marketing workflows
* Automated promotional campaigns

---

## 📈 Skills Demonstrated

This project demonstrates experience with:

* n8n workflow automation
* Webhook integration
* REST API concepts
* JSON data handling
* Dynamic data mapping
* AI prompt engineering
* OpenAI integration
* API testing with Postman
* Automated content generation

---

## ⭐ Future Improvements

Possible improvements for future versions:

* Add automatic hashtag generation
* Generate multiple caption variations
* Add different tones such as funny, professional, or persuasive
* Automatically post to TikTok or Instagram
* Store generated captions in Google Sheets
* Add product images
* Generate captions for multiple products at once
* Add an approval step before publishing

---

## 📌 Project Status

**Status:** ✅ Completed

**Project:** #7

**Difficulty:** ⭐⭐⭐⭐⭐⭐

**Category:** AI Automation / Social Media Automation

---

## 👨‍💻 Portfolio

This project is part of my **n8n Automation Portfolio**, demonstrating practical experience building AI-powered automation workflows.
