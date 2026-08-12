# 🔞 Project 1 — Age Checker Automation

A simple n8n webhook automation that receives a user's information and checks whether they meet a specified age requirement.

This project demonstrates a foundational real-world automation scenario involving webhook integration, conditional logic, data routing, and automated webhook responses.

---

## 🚀 Workflow

Webhook → IF → Allowed / Not Allowed → Respond to Webhook

---

## 🎯 Objective

The goal of this project is to build a simple age verification automation.

The workflow receives a user's information through a webhook, checks whether the user's age is **18 or older** using an IF node, routes the request to either the **Allowed** or **Not Allowed** path, and then returns the appropriate result through the Respond to Webhook node.

This demonstrates how conditional logic can be used to make decisions inside an n8n automation workflow.

---

## 📥 Input

The workflow receives the user's information through a **Webhook** using a `POST` request.

### Example Input

    {
      "name": "John",
      "age": 15
    }

---

## 🔀 Age Verification Logic

The **IF** node checks whether the user's age meets the required age of 18.

### ✅ Allowed

Users who are **18 or older** follow the Allowed path.

    Age ≥ 18
       ↓
    Allowed

### ❌ Not Allowed

Users who are **under 18** follow the Not Allowed path.

    Age < 18
       ↓
    Not Allowed

---

## 📤 Output

For this test, the user's age was **15**, so the workflow followed the **Not Allowed** path.

### Example Output

    [
      {
        "status": "Not Allowed",
        "message": "You are not eligible."
      }
    ]

### Verification Result

    Age: 15
    Status: ❌ Not Allowed
    Message: You are not eligible.

---

## 🔄 How It Works

### 1. Webhook

Receives the user's information.

    {
      "name": "John",
      "age": 15
    }

### 2. IF Node

Checks whether the user's age is **18 or older**.

### 3. Allowed Path

If the condition is true, the request is sent to the Allowed path.

    Age ≥ 18
       ↓
    Allowed

### 4. Not Allowed Path

If the condition is false, the request is sent to the Not Allowed path.

    Age < 18
       ↓
    Not Allowed

### 5. Respond to Webhook

Returns the appropriate result after the age verification is completed.

---

## 🧪 Testing

The workflow can be tested using **Postman**.

### Request

**Method:**

    POST

### Example Body

    {
      "name": "John",
      "age": 15
    }

### Expected Process

    Postman
       ↓
    Webhook
       ↓
    IF
       ├── ✅ Allowed
       │
       └── ❌ Not Allowed
              ↓
       Respond to Webhook

### Test Result

    Age: 15
       ↓
    IF Node
       ↓
    ❌ Not Allowed
       ↓
    "You are not eligible."

---

## 📸 Workflow Screenshot

<img width="1166" height="606" alt="1" src="https://github.com/user-attachments/assets/35f063a7-572e-4fc3-80e5-2c1d6e267e79" />


---

## 🧩 Technologies Used

- **n8n** — Workflow automation
- **Webhook** — Receives user information
- **IF Node** — Conditional age verification
- **Respond to Webhook** — Returns the result
- **Postman** — API testing
- **JSON** — Data format

---

## 💡 Example Use Cases

This automation can be used for:

- Age verification
- Registration systems
- Eligibility checking
- Access control
- User validation
- Webhook-based validation
- API request validation
- Membership eligibility

---

## 📈 Skills Demonstrated

This project demonstrates experience with:

- n8n workflow automation
- Creating webhook endpoints
- Receiving JSON data
- Using expressions in n8n
- Building conditional logic
- IF node configuration
- Routing data based on conditions
- Webhook response handling
- API testing with Postman
- Building simple API-based automations

---

## ⭐ Future Improvements

Possible improvements for future versions:

- Add date-of-birth validation
- Add customizable age requirements
- Add validation for missing age values
- Add validation for invalid age values
- Add custom responses for allowed users
- Connect the workflow to a database
- Add logging for verification attempts
- Add error handling

---

## 📌 Project Status

**Status:** ✅ Completed

**Project:** #1

**Difficulty:** ⭐

**Category:** Webhook Automation / Conditional Logic

**Automation Type:** Age Verification

---

## 👨‍💻 Portfolio

This project is part of my **n8n Automation Portfolio**, demonstrating practical experience building webhook-based automation workflows using conditional logic, JSON data processing, API testing, and automated webhook responses.
