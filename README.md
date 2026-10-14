# Smart Lead Management System

## Overview

The Smart Lead Management System is a workflow automation solution built using n8n to streamline customer lead processing. It captures customer inquiries through webhooks, classifies leads based on their budget, stores lead information in Google Sheets, and notifies the sales team through Telegram or Slack.

## Features

- **Automated Lead Capture:** Receives customer information through HTTP POST requests.
- **Data Processing:** Organizes and transforms incoming lead data.
- **Lead Classification:** Assigns priority levels based on predefined budget thresholds.
- **Centralized Lead Storage:** Stores customer information in Google Sheets.
- **Sales Notifications:** Sends lead details to the sales team through Telegram.
- **API Integration:** Supports testing and data submission using Postman.

## Technology Stack

- **Workflow Automation:** n8n
- **API Testing:** Postman
- **Data Exchange:** JSON, HTTP Webhooks
- **Data Storage:** Google Sheets
- **Notifications:** Telegram Bot API

## Workflow Architecture

```text
Customer Inquiry
       |
       v
    Webhook
       |
       v
   Edit Fields
       |
       v
       IF
      /  \
   True  False
     |      |
     v      v
 Set High  Set Standard
 Priority  Priority
     |      |
     v      v
 Google Sheets
       |
       v
 Telegram Notification
```

## Lead Classification

Leads are classified according to their specified budget.

| Condition | Priority |
|---|---|
| Budget ≥ ₹50,000 | High |
| Budget < ₹50,000 | Standard |

The classification threshold can be adjusted to meet business requirements.

## Sample Input

The workflow accepts customer information in JSON format.

```json
{
  "name": "Rahul Sharma",
  "email": "rahul@example.com",
  "budget": 75000,
  "requirement": "Website development"
}
```

## Data Storage

Lead information is stored in Google Sheets using the following fields:

- Name
- Email
- Budget
- Requirement
- Priority

## Sales Notification

The Telegram integration sends a structured message containing the customer's contact information, budget, requirement, and assigned priority, enabling the sales team to respond promptly.

## Setup and Configuration

1. Install and configure n8n.
2. Import or create the workflow.
3. Configure the Webhook node and obtain its URL.
4. Use Postman to submit customer data through an HTTP POST request with a JSON body.
5. Connect Google Sheets and configure the required credentials and field mappings.
6. Create a Telegram bot and configure the bot credentials and destination chat ID.
7. Execute the workflow and verify lead storage and notifications.

## Security Considerations

- Store API tokens and credentials securely using n8n's credential management.
- Avoid exposing unauthenticated production webhooks.
- Do not commit secrets or confidential customer information to version control.
- Use appropriate access controls for connected services.

## Future Enhancements

- AI-based lead scoring and categorization.
- Duplicate lead detection.
- Automated email confirmations.
- Follow-up reminders and sales tracking.
- Integration with CRM platforms.
- Lead analytics and reporting dashboards.
