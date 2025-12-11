# Outbound Interfaces

<!-- Source: app/Exports/**, app/Reports/**, app/Notifications/**, routes/api.php, config/excel.php -->

## Overview

Akaunting provides multiple ways to export data from the system, enabling you to share information with external parties, generate reports for analysis, and integrate with other business applications. This document describes all outbound data interfaces including file exports, report generation, automated notifications, and API data access.

Data can leave Akaunting through four primary channels:
- **Data Exports** - Download records as CSV or Excel files for external processing
- **Report Generation** - Generate PDF and Excel financial reports for analysis and compliance
- **Automated Notifications** - Email alerts sent automatically for invoices, payments, and system events
- **API Data Access** - Programmatic access for external systems to retrieve data

For a visual overview of how these outbound interfaces fit into the overall integration architecture, see the [Integration Map](integration-map.md).

---

## Data Exports

Akaunting allows you to export business data to CSV and Excel formats for use in spreadsheets, external accounting systems, or data analysis tools. Exports are available from list screens throughout the application.

### Supported Export Formats

| Format | File Extension | Best For |
|--------|---------------|----------|
| **CSV** | .csv | Simple data transfer, maximum compatibility with other systems |
| **Excel** | .xlsx | Formatted spreadsheets with multiple worksheets, data validation |

### Exportable Data Types

The following data types can be exported from Akaunting:

| Data Type | Access Location | Export Includes |
|-----------|----------------|-----------------|
| **Customers** | Sales > Customers | Contact details, addresses, currency preferences |
| **Vendors** | Purchases > Vendors | Contact details, addresses, currency preferences |
| **Invoices** | Sales > Invoices | Invoice details, line items, taxes, payment history, totals |
| **Bills** | Purchases > Bills | Bill details, line items, taxes, payment history, totals |
| **Transactions** | Banking > Transactions | Transaction details, account information, categorization |
| **Transfers** | Banking > Transfers | Transfer details between accounts |
| **Items** | Common > Items | Product/service details, pricing, tax assignments |
| **Categories** | Settings > Categories | Category names, types, hierarchy |
| **Taxes** | Settings > Taxes | Tax names, rates, types |

### Export Field Reference

#### Transaction Export Fields

When exporting transactions, the following fields are included:

| Field Name | Description |
|------------|-------------|
| type | Transaction type (income or expense) |
| number | Unique transaction number |
| paid_at | Date the transaction was recorded |
| amount | Transaction amount |
| currency_code | Currency code (e.g., USD, EUR) |
| currency_rate | Exchange rate at time of transaction |
| account_name | Bank or cash account name |
| invoice_bill_number | Related invoice or bill number (if applicable) |
| contact_email | Customer or vendor email address |
| category_name | Expense or income category |
| description | Transaction description or notes |
| payment_method | Method of payment used |
| reference | External reference number |
| reconciled | Whether the transaction has been reconciled |
| parent_number | Parent transaction number (for recurring transactions) |

#### Transfer Export Fields

When exporting bank transfers, the following fields are included:

| Field Name | Description |
|------------|-------------|
| transferred_at | Date of the transfer |
| amount | Transfer amount |
| from_currency_code | Source account currency |
| from_currency_rate | Source currency exchange rate |
| from_account_name | Source bank account name |
| to_currency_code | Destination account currency |
| to_currency_rate | Destination currency exchange rate |
| to_account_name | Destination bank account name |
| description | Transfer description |
| payment_method | Transfer method |
| reference | Reference number |

#### Customer Export Fields

When exporting customers, the following fields are included:

| Field Name | Description |
|------------|-------------|
| name | Customer name |
| email | Email address |
| tax_number | Tax identification number |
| phone | Phone number |
| address | Street address |
| country | Country name |
| state | State or province |
| zip_code | Postal code |
| city | City |
| website | Website URL |
| currency_code | Preferred currency |
| reference | Internal reference |
| enabled | Whether the customer is active |
| can_login | Whether the customer has portal access |

#### Vendor Export Fields

When exporting vendors, the following fields are included:

| Field Name | Description |
|------------|-------------|
| name | Vendor name |
| email | Email address |
| tax_number | Tax identification number |
| phone | Phone number |
| address | Street address |
| country | Country name |
| state | State or province |
| zip_code | Postal code |
| city | City |
| website | Website URL |
| currency_code | Preferred currency |
| reference | Internal reference |
| enabled | Whether the vendor is active |

### Multi-Sheet Excel Exports

When exporting invoices or bills to Excel format, Akaunting creates a multi-sheet workbook containing related data in separate worksheets:

**Invoice Export Worksheets:**
- Invoices (main document details)
- Invoice Items (line item details)
- Invoice Item Taxes (tax breakdown per item)
- Invoice Histories (status change history)
- Invoice Totals (subtotals, taxes, discounts, grand total)
- Invoice Transactions (payment records)

**Bill Export Worksheets:**
- Bills (main document details)
- Bill Items (line item details)
- Bill Item Taxes (tax breakdown per item)
- Bill Histories (status change history)
- Bill Totals (subtotals, taxes, discounts, grand total)
- Bill Transactions (payment records)

### How to Export Data

1. Navigate to the list screen for the data you want to export (e.g., Sales > Invoices)
2. Optionally apply filters to narrow down the records
3. Select specific records using checkboxes, or leave all unchecked to export all visible records
4. Click the **Export** button
5. Choose your preferred format (CSV or Excel)
6. The file downloads automatically, or you receive an email notification with a download link for large exports

---

## Report Generation

Akaunting generates financial reports that can be viewed on screen, printed, or exported to PDF and Excel formats. Reports help you analyze business performance, prepare for tax filing, and meet compliance requirements.

### Available Report Types

| Report | Description | Key Data |
|--------|-------------|----------|
| **Income Summary** | Overview of all income by category | Income amounts grouped by category and time period |
| **Expense Summary** | Overview of all expenses by category | Expense amounts grouped by category and time period |
| **Income vs Expense** | Comparison of income and expenses | Side-by-side income and expense totals by period |
| **Profit and Loss** | Net profit/loss statement | Income minus expenses with net profit calculation |
| **Tax Summary** | Taxes collected and paid | Tax amounts by tax rate and period |
| **Discount Summary** | Discounts applied to sales and purchases | Discount amounts and their impact on totals |

### Report Export Formats

| Format | Best For |
|--------|----------|
| **View on Screen** | Quick review and interactive filtering |
| **Print** | Physical copies for filing or distribution |
| **PDF** | Digital archiving, email attachments, professional presentation |
| **Excel** | Further analysis in spreadsheets, data manipulation |

### Report Features

**Filtering Options:**
- Date range selection (custom dates or presets like This Month, This Year)
- Accounting basis (Cash basis or Accrual basis)
- Grouping period (Daily, Monthly, Quarterly, Yearly)

**Cash vs Accrual Basis:**
- **Cash Basis** - Reports income when payment is received and expenses when payment is made
- **Accrual Basis** - Reports income when invoiced and expenses when billed, regardless of payment timing

### How to Generate Reports

1. Navigate to Reports from the main menu
2. Select the report type you want to generate
3. Set your filter options (date range, basis, grouping)
4. Click **Show** to view the report on screen
5. Use the export buttons to download as PDF or Excel

---

## Automated Notifications

Akaunting automatically sends email notifications to keep customers, vendors, and team members informed about important events. These notifications use customizable email templates.

### Invoice Notifications

Notifications sent to customers regarding invoices:

| Notification Type | Trigger | Recipient | Attachments |
|-------------------|---------|-----------|-------------|
| **New Invoice** | Invoice is marked as sent | Customer | PDF invoice (optional) |
| **Payment Reminder** | Scheduled reminder before due date | Customer | PDF invoice (optional) |
| **Overdue Notice** | Invoice becomes overdue | Customer | PDF invoice (optional) |

**Invoice Email Content Includes:**
- Invoice number and amount due
- Invoice date and due date
- Link to view invoice online
- Link to pay through the Customer Portal
- Company contact information

### Bill Notifications

Notifications related to vendor bills:

| Notification Type | Trigger | Recipient | Content |
|-------------------|---------|-----------|---------|
| **Bill Receipt** | Bill is created | Internal users/Vendor | Bill details, amounts, due date |

**Bill Email Content Includes:**
- Bill number and total amount
- Bill date and due date
- Vendor name
- Link to view bill in the system

### Payment Notifications

Notifications sent when payments are recorded:

| Notification Type | Trigger | Recipient | Attachments |
|-------------------|---------|-----------|-------------|
| **Payment Receipt** | Payment is recorded for an invoice | Customer | PDF receipt (optional) |

**Payment Email Content Includes:**
- Payment amount and date
- Link to view payment confirmation
- Link to view in Customer Portal
- Company contact information

### System Notifications

Notifications for system events:

| Notification Type | Trigger | Recipient |
|-------------------|---------|-----------|
| **Export Completed** | Large data export finishes processing | User who initiated export |

**Export Completed Email Content:**
- Notification that export is ready
- Download link for the exported file

### Email Template Customization

Notification emails support customizable templates with dynamic placeholders:

**Invoice Placeholders:**
| Placeholder | Replaced With |
|-------------|---------------|
| `{invoice_number}` | Invoice document number |
| `{invoice_total}` | Total invoice amount |
| `{invoice_amount_due}` | Remaining balance due |
| `{invoiced_date}` | Invoice issue date |
| `{invoice_due_date}` | Payment due date |
| `{customer_name}` | Customer's name |
| `{company_name}` | Your company name |
| `{company_email}` | Your company email |

**Bill Placeholders:**
| Placeholder | Replaced With |
|-------------|---------------|
| `{bill_number}` | Bill document number |
| `{bill_total}` | Total bill amount |
| `{bill_amount_due}` | Remaining balance due |
| `{billed_date}` | Bill issue date |
| `{bill_due_date}` | Payment due date |
| `{vendor_name}` | Vendor's name |

**Payment Placeholders:**
| Placeholder | Replaced With |
|-------------|---------------|
| `{payment_amount}` | Amount paid |
| `{payment_date}` | Date of payment |
| `{contact_name}` | Customer or vendor name |

---

## API Data Access

External applications can retrieve data from Akaunting through the REST API. This enables integration with CRM systems, e-commerce platforms, custom dashboards, and other business tools.

### API Overview

| Aspect | Details |
|--------|---------|
| **API Version** | v3 |
| **Base URL** | `{your-domain}/api` |
| **Content Type** | `application/vnd.akaunting.v3+json` |
| **Authentication** | API key or OAuth 2.0 |

### Available Data Endpoints

The following data can be retrieved through the API:

| Endpoint | Data Available | Operations |
|----------|---------------|------------|
| `/api/users` | User accounts and profiles | List, Read |
| `/api/companies` | Company configurations | List, Read |
| `/api/items` | Products and services | List, Read |
| `/api/contacts` | Customers and vendors | List, Read |
| `/api/documents` | Invoices, bills, and other documents | List, Read |
| `/api/documents/{id}/transactions` | Payments on specific documents | List, Read |
| `/api/accounts` | Bank and cash accounts | List, Read |
| `/api/transactions` | Income and expense transactions | List, Read |
| `/api/transfers` | Account-to-account transfers | List, Read |
| `/api/reconciliations` | Bank reconciliation records | List, Read |
| `/api/categories` | Income and expense categories | List, Read |
| `/api/currencies` | Configured currencies | List, Read |
| `/api/taxes` | Tax rates and rules | List, Read |
| `/api/settings` | Application settings | List, Read |
| `/api/reports` | Financial report data | List, Read |
| `/api/dashboards` | Dashboard configurations | List, Read |

### API Use Cases for Data Retrieval

| Use Case | Endpoints Used |
|----------|---------------|
| Sync customer data to CRM | `/api/contacts` |
| Display outstanding invoices in external dashboard | `/api/documents` |
| Export transaction history to reporting tool | `/api/transactions` |
| Retrieve product catalog for e-commerce sync | `/api/items` |
| Get tax configuration for compliance reporting | `/api/taxes`, `/api/reports` |
| Access financial summaries for executive dashboard | `/api/reports` |

### Utility Endpoint

| Endpoint | Purpose |
|----------|---------|
| `/api/ping` | Test API connectivity and authentication |

---

## See Also

- [Integration Map](integration-map.md) - Visual diagram of all integration touchpoints
- [Inbound Interfaces](inbound-interfaces.md) - Import capabilities and file format requirements
- [Validation Rules](../04-business-rules/validation-rules.md) - Data validation applied to exports
