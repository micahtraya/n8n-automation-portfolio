# Project 6 - Smart Inventory Alert System

## Overview

A webhook-based n8n automation that receives inventory information and automatically processes low-stock items to trigger an inventory alert.

The workflow can help businesses monitor stock levels and notify the appropriate person when a product needs to be reordered.

## Workflow

**Webhook → Inventory Check → Gmail Notification**

## How It Works

1. The Webhook receives product inventory information.
2. The automation processes the product name, current stock, and supplier.
3. The inventory level is evaluated using the configured stock condition.
4. When the product requires attention, an automated email notification is sent.
5. Gmail processes the notification and returns the email message information.

## Input

```json id="fxe1tb"
{
  "Product": "Keyboard",
  "Stock": 10,
  "Supplier": "Razer"
}
```

## Output

```json id="7f1p6h"
{
  "id": "19fd7dc16c22c9b6",
  "threadId": "19fd7dc16c22c9b6",
  "labelIds": [
    "UNREAD",
    "SENT",
    "INBOX"
  ]
}
```

## Example

**Product:** Keyboard
**Stock Remaining:** 10
**Supplier:** Razer

The automation processes the inventory information and sends an automated Gmail notification when the configured stock condition is met.

## Use Case

This automation can be useful for:

* Warehouses
* Retail businesses
* E-commerce stores
* Inventory management teams
* Purchasing departments

It can reduce the need for manually checking inventory and help businesses respond more quickly when stock levels require attention.

## Tools

* n8n
* Webhook
* Inventory Logic
* Gmail
* JSON

## What I Learned

* Receiving inventory data through a webhook
* Processing structured JSON data
* Building automated inventory checks
* Creating conditional notification workflows
* Connecting n8n with Gmail
* Sending automated email alerts
* Working with Gmail message responses

## 📸 Workflow Screenshot

<img width="852" height="530" alt="image" src="https://github.com/user-attachments/assets/f840e90d-22df-4451-b62d-1fcf65c014ec" />


## Project Status

✅ Completed and tested
