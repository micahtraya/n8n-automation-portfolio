# 📦 Warehouse Inventory Management

## Overview

A webhook-based n8n automation that receives warehouse inventory information and evaluates the current stock level to determine the inventory status.

The automation helps businesses monitor product stock and identify inventory conditions that may require attention.

## Workflow

**Webhook → Inventory Check → Respond to Webhook**

## How It Works

1. The Webhook receives product and inventory information.
2. The automation processes the product, category, stock quantity, and supplier.
3. The stock level is evaluated against the defined inventory rules.
4. The automation determines the inventory status.
5. Respond to Webhook returns the product information together with its inventory status.

## Input

```json
{
  "product": "Gaming Mouse",
  "category": "Electronics",
  "stock": 500,
  "supplier": "Logitech"
}
```

## Output

```json
{
  "body": {
    "product": "Gaming Mouse",
    "category": "Electronics",
    "supplier": "Logitech"
  },
  "status": "normal"
}
```

## Example

**Product:** Gaming Mouse
**Category:** Electronics
**Stock:** 500
**Supplier:** Logitech

### Automated Result

* **Status:** Normal

The automation identifies the current inventory level as **normal** based on the configured stock rules.

## Use Case

This automation can be useful for:

* Warehouses
* E-commerce businesses
* Retail businesses
* Inventory management systems
* Supply chain operations

It can help businesses automatically evaluate inventory levels and prepare the data for further actions, such as alerts, database updates, or supplier notifications.

## Tools

* n8n
* Webhook
* Conditional Logic
* JSON
* Respond to Webhook

## What I Learned

* Receiving inventory data through a webhook
* Processing structured JSON data
* Building inventory evaluation logic
* Using conditional logic to determine stock status
* Handling inventory information
* Returning structured webhook responses

## 📸 Workflow Screenshot

<img width="846" height="534" alt="image" src="https://github.com/user-attachments/assets/5c2aae30-1cb1-4397-946a-46e1d833b3c9" />


## Project Status

✅ Completed and tested
