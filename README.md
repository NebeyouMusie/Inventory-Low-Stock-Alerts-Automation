# Inventory Low Stock Alerts Automation with n8n

Automate your inventory monitoring with n8n! This project continuously checks product stock levels in Google Sheets and sends alert emails when items fall below a defined threshold.

![Inventory Low Stock Alerts Cover](./images/Inventory%20Low%20Stock%20Alerts%20Automation%20Cover.png)

---

## Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
  - [Workflow Steps](#workflow-steps)
- [Benefits](#benefits)
- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
  - [1. Clone or Import Workflow](#1-clone-or-import-workflow)
  - [2. Connect Google Sheets](#2-connect-google-sheets)
  - [3. Connect Gmail](#3-connect-gmail)
  - [4. Customize Email Template](#4-customize-email-template)
  - [5. Schedule the Trigger](#5-schedule-the-trigger)
  - [6. Test the Workflow](#6-test-the-workflow)
- [Customization](#customization)
  - [Inventory Data Sheet Structure](#inventory-data-sheet-structure)
  - [Threshold Logic](#threshold-logic)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

**Inventory Low Stock Alerts** is an n8n workflow that:

- Reads inventory records from Google Sheets
- Filters items where current stock is at or below the low-stock threshold
- Sends alert emails via Gmail with product details for low-stock items
- Runs on a schedule to proactively prevent stockouts

---

## How It Works

![Inventory Low Stock Alerts Workflow](./images/Inventory%20Low%20Stock%20Alerts%20workflow.png)

### Workflow Steps

1. **Schedule Trigger**
   - Initiates the workflow on a periodic schedule (e.g., daily at 06:00).

2. **Get Row(s) in Sheet**
   - Retrieves all inventory rows from a specified Google Sheets document.

3. **Filter Low Stock**
   - Compares `Current Stock` against `Low Stock Threshold` and keeps only items at or below the threshold.

4. **Send Email via Gmail**
   - Sends a low-stock alert email including product details to the specified recipient(s).

---

## Benefits

- **Prevents stockouts and lost sales** with proactive alerts
- **Automates inventory monitoring** to reduce manual checks
- **Provides clear, actionable alerts** including product and stock details
- **Easily extensible** to other data sources and notification channels

---

## Requirements

- [n8n](https://n8n.io/) installation or cloud account
- Google account with:
  - Access to Google Sheets (your inventory sheet)
  - Access to Gmail (for sending alert emails)
- Inventory data stored in Google Sheets

---

## Setup Instructions

### 1. Clone or Import Workflow

- Download or import the attached `Inventory Low Stock Alerts.json` workflow into your n8n instance (Cloud, Desktop, or self-hosted).

### 2. Connect Google Sheets

- Add your Google Sheets credentials in n8n.
- Set the Spreadsheet ID and Worksheet (Sheet) name to your inventory sheet.
- Ensure the sheet includes columns for `Product ID`, `Product Name`, `Variant`, `Current Stock`, and `Low Stock Threshold`.

### 3. Connect Gmail

- Add your Gmail credentials to the email node(s) in n8n.
- Confirm the sender account and recipient email address(es) for alerts.

### 4. Customize Email Template

- Edit the "Send a message" (Gmail) node to tailor subject and body content.
- Use n8n expressions to personalize details, e.g. `{{ $json["Product Name"] }}`, `{{ $json["Variant"] }}`, `{{ $json["Current Stock"] }}`.

### 5. Schedule the Trigger

- Adjust the Schedule Trigger node to your preferred run frequency/time (e.g., daily at 06:00).

### 6. Test the Workflow

- Run the workflow manually for the first time.
- Verify alerts are sent for items at or below the threshold.
- Confirm Gmail "Sent" items and validate results against your Google Sheet.

---

## Customization

### Inventory Data Sheet Structure

Your sheet should look similar to the `Inventory Data.csv` file in the `data` folder.

![Inventory Spreadsheet Example](./images/Inventory%20Spreadsheet.png)

Recommended columns:
- **Product ID**: Unique identifier
- **Product Name**: Item name
- **Variant**: Size/Color or other variant information (optional)
- **Current Stock**: Current quantity on hand (number)
- **Low Stock Threshold**: Minimum acceptable stock before alert (number)

### Threshold Logic

The default logic triggers an alert when:

- `Current Stock` is less than `Low Stock Threshold`

You can adjust this logic in the IF node (e.g., use less-than-or-equal). You can also enhance the workflow to:
- Include supplier contacts and auto-email the supplier
- Post alerts to Slack or Microsoft Teams
- Write flagged items to another sheet or database

---

## Troubleshooting

- **Google Sheets node fails**: Check API permissions, spreadsheet ID, and sheet name.
- **Gmail node errors**: Verify authentication and that your account allows API sending.
- **No emails sent**: Ensure the IF condition correctly matches low-stock rows; test with known low values.
- **Workflow not triggering**: Review Schedule Trigger configuration and n8n instance status.

---

## Contributing

Contributions and suggestions are welcome!  
Fork the repo, submit issues, or create pull requests for workflow improvements.

---

## License

This project is licensed under the MIT License.

---

## Contact

- **Email:** nebeyoumusie@gmail.com
- **LinkedIn:** [LinkedIn](https://www.linkedin.com/in/nebeyou-musie)
- **X(Twitter):** [X](https://x.com/NebeyouMusie)
- **Upwork:** [Upwork](https://www.upwork.com/freelancers/~017ff01729e3cd26e0?mp_source=share)
- **My Agency:** [Fuzion Tech Website](https://fuzion-tech.com/) or [Fuzion Tech on Upwork](https://www.upwork.com/agencies/1948388369189366041/)

---

**Skills & Technologies:**  
`n8n`, `Automation`, `Inventory Management`, `Google Sheets Automation`, `Gmail`

---

**Enjoy automated inventory monitoring and proactive low-stock alerts!**

---

> _For any issues, please contact the project maintainer or open an issue on your workflow repository._
