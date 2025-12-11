# Inbound Interfaces

<!-- Source: app/Imports/**, config/excel.php, config/import.php -->

## Overview

Akaunting allows users to import data from external sources to quickly populate their accounting records. Instead of manually entering contacts, items, transactions, and documents one by one, users can prepare their data in spreadsheet files and import them in bulk.

The import functionality supports:
- **Contacts** - Import customer and vendor information
- **Items** - Import products and services with associated tax rates
- **Transactions** - Import income and expense records
- **Transfers** - Import transfers between bank accounts
- **Invoices** - Import sales invoices with line items and payment history
- **Bills** - Import purchase bills with line items and payment history
- **Categories** - Import income and expense categories
- **Taxes** - Import tax rate configurations

---

## Supported File Formats

Akaunting accepts the following file formats for data import:

| Format | Extension | Description |
|--------|-----------|-------------|
| **Excel 97-2003** | .xls | Legacy Microsoft Excel format |
| **Excel 2007+** | .xlsx | Modern Microsoft Excel format (recommended) |

### File Requirements

| Requirement | Value | Notes |
|-------------|-------|-------|
| **Maximum rows per file** | 1,000 | Larger datasets should be split into multiple files |
| **File structure** | Heading row required | First row must contain column names |
| **Character encoding** | UTF-8 | Ensures proper handling of international characters |
| **Empty rows** | Skipped automatically | Empty rows are ignored during processing |

### CSV Import Settings

When CSV format is used within Excel files, the following settings apply:

| Setting | Value |
|---------|-------|
| **Delimiter** | Comma (,) |
| **Text enclosure** | Double quote (") |
| **Escape character** | Backslash (\\) |
| **Input encoding** | UTF-8 |

---

## Import Types and Column Requirements

Each import type requires specific columns to be present in your file. Required columns must contain valid data for every row, while optional columns can be left empty.

### Customers Import

Import customer records to quickly populate your customer database.

| Column Name | Required | Description |
|-------------|----------|-------------|
| `name` | Yes | Customer name (individual or company) |
| `email` | Yes | Primary contact email address |
| `country` | No | Country name (must match system country list) |
| `currency_code` | No | Preferred currency (e.g., USD, EUR) - defaults to company currency |
| `phone` | No | Phone number |
| `address` | No | Street address |
| `city` | No | City name |
| `state` | No | State or province |
| `zip_code` | No | Postal or ZIP code |
| `website` | No | Website URL |
| `tax_number` | No | Tax identification number |
| `reference` | No | Custom reference or ID |
| `enabled` | No | Active status (1 = enabled, 0 = disabled) - defaults to 1 |
| `can_login` | No | Portal access (1 = yes, 0 = no) - requires matching email in user accounts |

**Duplicate Detection:** Customers are identified by the combination of type, name, and email. Existing records with matching values are skipped during import.

### Vendors Import

Import vendor records to build your supplier database.

| Column Name | Required | Description |
|-------------|----------|-------------|
| `name` | Yes | Vendor or supplier name |
| `email` | Yes | Primary contact email address |
| `country` | No | Country name (must match system country list) |
| `currency_code` | No | Preferred currency - defaults to company currency |
| `phone` | No | Phone number |
| `address` | No | Street address |
| `city` | No | City name |
| `state` | No | State or province |
| `zip_code` | No | Postal or ZIP code |
| `website` | No | Website URL |
| `tax_number` | No | Tax identification number |
| `reference` | No | Custom reference or ID |
| `enabled` | No | Active status (1 = enabled, 0 = disabled) - defaults to 1 |

**Duplicate Detection:** Vendors are identified by the combination of type, name, and email. Existing records with matching values are skipped during import.

---

### Items Import

Import products and services with optional tax assignments. This import uses two sheets within the Excel file.

#### Sheet 1: Items

| Column Name | Required | Description |
|-------------|----------|-------------|
| `name` | Yes | Item name |
| `sale_price` | Yes | Price when selling to customers |
| `purchase_price` | Yes | Price when purchasing from vendors |
| `type` | Yes | Item type identifier |
| `description` | No | Item description |
| `category_id` | No | Category ID - can also use `category_name` |
| `category_name` | No | Category name (alternative to category_id) |
| `enabled` | No | Active status (1 = enabled, 0 = disabled) - defaults to 1 |

#### Sheet 2: Item Taxes

| Column Name | Required | Description |
|-------------|----------|-------------|
| `item_name` | Yes | Name of the item to associate with tax |
| `tax_id` | No | Tax rate ID - can also use `tax_name` |
| `tax_name` | No | Tax rate name (alternative to tax_id) |

**Duplicate Detection:** Items are identified by type, name, sale_price, and purchase_price. Existing records with matching values are skipped during import.

---

### Transactions Import

Import income and expense transactions to your bank accounts.

| Column Name | Required | Description |
|-------------|----------|-------------|
| `number` | Yes | Unique transaction number or reference |
| `type` | Yes | Transaction type: "income" or "expense" |
| `paid_at` | Yes | Transaction date (YYYY-MM-DD format) |
| `amount` | Yes | Transaction amount (positive number) |
| `account_id` | No | Bank account ID - can also use `account_name` |
| `account_name` | No | Bank account name (alternative to account_id) |
| `currency_code` | No | Currency code - defaults to account currency |
| `currency_rate` | No | Exchange rate - required for foreign currency |
| `category_id` | No | Category ID - can also use `category_name` |
| `category_name` | No | Category name (alternative to category_id) |
| `contact_id` | No | Customer/Vendor ID - can also use `contact_name` |
| `contact_name` | No | Customer/Vendor name (alternative to contact_id) |
| `description` | No | Transaction description |
| `payment_method` | No | Payment method (cash, bank_transfer, etc.) |
| `reference` | No | Additional reference information |
| `reconciled` | No | Reconciliation status (1 = reconciled, 0 = not) |

**Duplicate Detection:** Transactions are identified by their number. Existing records with matching numbers are skipped during import.

---

### Transfers Import

Import transfers between bank accounts.

| Column Name | Required | Description |
|-------------|----------|-------------|
| `from_account_id` | Yes | Source account ID - can also use `from_account_name` |
| `from_account_name` | No | Source account name (alternative to from_account_id) |
| `from_currency_code` | Yes | Source account currency code |
| `from_currency_rate` | Yes | Source currency exchange rate (must be > 0) |
| `to_account_id` | Yes | Destination account ID - can also use `to_account_name` |
| `to_account_name` | No | Destination account name (alternative to to_account_id) |
| `to_currency_code` | Yes | Destination account currency code |
| `to_currency_rate` | Yes | Destination currency exchange rate (must be > 0) |
| `amount` | Yes | Transfer amount |
| `transferred_at` | Yes | Transfer date (YYYY-MM-DD format) |
| `payment_method` | Yes | Payment method used for transfer |
| `description` | No | Transfer description |
| `reference` | No | Reference number or notes |

**Duplicate Detection:** Transfers are identified by their expense and income transaction IDs. Existing records with matching values are skipped during import.

---

### Invoices Import

Import sales invoices with line items. This import uses multiple sheets within the Excel file.

#### Sheet 1: Invoices (Main Invoice Data)

| Column Name | Required | Description |
|-------------|----------|-------------|
| `invoice_number` | Yes | Unique invoice number |
| `invoiced_at` | Yes | Invoice date (YYYY-MM-DD format) |
| `due_at` | No | Payment due date |
| `currency_code` | Yes | Invoice currency code |
| `currency_rate` | Yes | Exchange rate (must be > 0) |
| `status` | No | Invoice status (draft, sent, paid, cancelled) |
| `contact_id` | No | Customer ID - can also use `contact_name` or `contact_email` |
| `contact_name` | No | Customer name |
| `contact_email` | No | Customer email |
| `contact_address` | No | Billing address |
| `contact_city` | No | City |
| `contact_state` | No | State or province |
| `contact_zip_code` | No | Postal code |
| `contact_country` | No | Country name |
| `contact_phone` | No | Phone number |
| `category_id` | No | Income category ID - can also use `category_name` |
| `category_name` | No | Category name |
| `notes` | No | Invoice notes (visible on invoice) |
| `footer` | No | Footer text |
| `title` | No | Invoice title - defaults to "Invoice" |
| `template` | No | Invoice template name |
| `color` | No | Accent color (hex code) |

#### Sheet 2: Invoice Items (Line Items)

| Column Name | Required | Description |
|-------------|----------|-------------|
| `invoice_number` | Yes | Reference to parent invoice |
| `item_name` | Yes | Product or service name |
| `item_description` | No | Item description |
| `quantity` | Yes | Quantity |
| `price` | Yes | Unit price |
| `tax` | No | Tax amount for this line |
| `discount_rate` | No | Discount percentage |
| `total` | No | Line total (calculated if not provided) |

#### Additional Invoice Sheets

- **Invoice Item Taxes** - Tax breakdowns for line items
- **Invoice Histories** - Status change history records
- **Invoice Totals** - Subtotals, taxes, and grand totals
- **Invoice Transactions** - Payment records against the invoice

**Duplicate Detection:** Invoices are identified by type and document_number. Existing invoices with matching numbers are skipped during import.

---

### Bills Import

Import purchase bills with line items. This import uses multiple sheets within the Excel file, similar to invoices.

#### Sheet 1: Bills (Main Bill Data)

| Column Name | Required | Description |
|-------------|----------|-------------|
| `bill_number` | Yes | Unique bill number |
| `billed_at` | Yes | Bill date (YYYY-MM-DD format) |
| `due_at` | No | Payment due date |
| `currency_code` | Yes | Bill currency code |
| `currency_rate` | Yes | Exchange rate (must be > 0) |
| `status` | No | Bill status (draft, received, paid, cancelled) |
| `contact_id` | No | Vendor ID - can also use `contact_name` or `contact_email` |
| `contact_name` | No | Vendor name |
| `contact_email` | No | Vendor email |
| `contact_address` | No | Vendor address |
| `contact_city` | No | City |
| `contact_state` | No | State or province |
| `contact_zip_code` | No | Postal code |
| `contact_country` | No | Country name |
| `contact_phone` | No | Phone number |
| `category_id` | No | Expense category ID - can also use `category_name` |
| `category_name` | No | Category name |
| `notes` | No | Bill notes |
| `footer` | No | Footer text |
| `title` | No | Bill title - defaults to "Bill" |
| `template` | No | Bill template name |
| `color` | No | Accent color (hex code) |

#### Sheet 2: Bill Items (Line Items)

| Column Name | Required | Description |
|-------------|----------|-------------|
| `bill_number` | Yes | Reference to parent bill |
| `item_name` | Yes | Product or service name |
| `item_description` | No | Item description |
| `quantity` | Yes | Quantity |
| `price` | Yes | Unit price |
| `tax` | No | Tax amount for this line |
| `discount_rate` | No | Discount percentage |
| `total` | No | Line total (calculated if not provided) |

#### Additional Bill Sheets

- **Bill Item Taxes** - Tax breakdowns for line items
- **Bill Histories** - Status change history records
- **Bill Totals** - Subtotals, taxes, and grand totals
- **Bill Transactions** - Payment records against the bill

**Duplicate Detection:** Bills are identified by type and document_number. Existing bills with matching numbers are skipped during import.

---

### Categories Import

Import income and expense categories for organizing transactions.

| Column Name | Required | Description |
|-------------|----------|-------------|
| `name` | Yes | Category name |
| `type` | Yes | Category type: "income", "expense", or "item" |
| `color` | No | Display color (hex code) |
| `parent_id` | No | Parent category ID for subcategories |
| `enabled` | No | Active status (1 = enabled, 0 = disabled) |

**Duplicate Detection:** Categories are identified by the combination of name and type. Existing records with matching values are skipped during import.

---

### Taxes Import

Import tax rate configurations.

| Column Name | Required | Description |
|-------------|----------|-------------|
| `name` | Yes | Tax name (e.g., "VAT", "Sales Tax") |
| `type` | Yes | Tax type: "normal", "inclusive", "compound", "fixed", or "withholding" |
| `rate` | Yes | Tax rate percentage |
| `enabled` | No | Active status (1 = enabled, 0 = disabled) |

**Special Rule:** Only one compound tax can exist in the system. If a compound tax already exists, any rows with type "compound" are skipped.

**Duplicate Detection:** Taxes are identified by the combination of name and type. Existing records with matching values are skipped during import.

---

## Validation During Import

Akaunting validates each row of data during import to ensure data integrity. Understanding the validation process helps you prepare files that import successfully.

### Validation Process

1. **File Format Validation** - The system verifies the file format and structure
2. **Header Row Validation** - Column names are matched to expected fields
3. **Row-by-Row Validation** - Each data row is validated against field requirements
4. **Business Rule Validation** - Cross-field and business logic rules are applied
5. **Duplicate Detection** - Existing records are checked to prevent duplicates

### Common Validation Rules

| Validation | Description | Affected Fields |
|------------|-------------|-----------------|
| **Required** | Field must contain a value | Marked as "Yes" in column tables |
| **Email format** | Must be a valid email address | `email` fields |
| **Currency code** | Must match a configured currency | `currency_code` fields |
| **Date format** | Must be in YYYY-MM-DD format | Date fields |
| **Numeric** | Must be a valid number | Amount and price fields |
| **Greater than zero** | Must be a positive number | `currency_rate` fields |
| **Unique** | Value cannot already exist | Document numbers |
| **Exists** | Referenced ID must exist in system | ID reference fields |

### Duplicate Handling

When the import process encounters a row that matches an existing record, the duplicate row is automatically skipped. This behavior:

- Prevents accidental duplication of records
- Allows you to re-import files without creating duplicates
- Uses the columns specified in each import type's "Duplicate Detection" section

### Error Handling

When validation errors occur:

1. **The problematic rows are not imported**
2. **You receive a notification with error details**
3. **Error messages indicate the row number and field causing the issue**
4. **Successfully validated rows before the error are imported**

---

## Import Notifications

Akaunting notifies users when import processes complete, whether successful or failed.

### Import Completed Notification

When an import completes successfully, you receive:

- **Email notification** - Sent to your registered email address with completion confirmation
- **In-app notification** - Displayed in the notification bell icon showing:
  - The type of records imported (e.g., "Customers", "Invoices")
  - The total number of rows successfully imported

### Import Failed Notification

When an import fails due to validation errors, you receive:

- **Email notification** - Contains a list of all errors encountered during import
- **In-app notification** - Alerts you that the import failed with error details including:
  - The specific validation errors for each problematic row
  - Guidance on which rows and fields need correction

---

## Bank Feed Integrations

Akaunting supports automatic bank transaction imports through module-based bank feed integrations. These modules connect directly to financial institutions to retrieve transaction data.

### How Bank Feeds Work

1. **Install a bank feed module** from the Akaunting App Store
2. **Connect your bank account** using your banking credentials
3. **Transactions are automatically imported** on a scheduled basis
4. **Review and categorize** imported transactions in Akaunting

### Bank Feed Features

| Feature | Description |
|---------|-------------|
| **Automatic Import** | Transactions are fetched automatically without manual file uploads |
| **Duplicate Prevention** | Already-imported transactions are not re-imported |
| **Transaction Matching** | System suggests matches with existing invoices and bills |
| **Categorization** | Suggest categories based on transaction patterns |
| **Reconciliation Support** | Imported transactions can be reconciled with bank statements |

### Supported Bank Feed Modules

Bank feed availability varies by region and financial institution. Visit the Akaunting App Store to see available bank feed modules for your location.

> **Note:** Bank feed integrations require purchasing and installing separate modules from the Akaunting App Store. These modules are not included in the core Akaunting application.

---

## Best Practices for Successful Imports

Follow these guidelines to ensure smooth data imports:

### File Preparation

- **Use the correct file format** - Excel (.xlsx) is recommended for best compatibility
- **Include all required columns** - Even if a column is optional, include it in your header row
- **Keep files under 1,000 rows** - Split larger datasets into multiple files
- **Use consistent date formatting** - YYYY-MM-DD format works best
- **Verify currency codes** - Ensure currency codes match those configured in Akaunting

### Data Quality

- **Remove duplicate rows** before importing to avoid processing overhead
- **Validate email addresses** - Invalid emails will cause row failures
- **Check reference IDs** - If using ID columns, verify the IDs exist in Akaunting
- **Use name alternatives** - If you don't know IDs, use the name-based columns instead

### Testing Imports

- **Import a small test file first** - Verify your column mapping with a few rows
- **Review notifications** - Check for any errors in the import completion notification
- **Verify imported data** - Spot-check several imported records for accuracy

---

## See Also

- [Integration Map](integration-map.md) - Overview of all Akaunting integration points
- [Outbound Interfaces](outbound-interfaces.md) - Export capabilities and data output options
- [Validation Rules](../04-business-rules/validation-rules.md) - Detailed validation rules for all entities
