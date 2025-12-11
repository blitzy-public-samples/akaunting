# Validation Rules

<!-- Source: app/Http/Requests/** -->

## Overview

Akaunting validates user input to ensure data integrity and proper business operations. The following sections document the validation rules for each entity type, organized by functional area.

---

## Invoice/Bill Validation Rules

<!-- Source: app/Http/Requests/Document/Document.php -->

### Document Fields

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Document Number | Yes | String | Unique per company; cannot duplicate within same company and document type |
| Type | Yes | String | Valid document type (invoice, bill, etc.) |
| Status | Yes | String | Valid status value (draft, sent, viewed, partial, paid, cancelled) |
| Issue Date | Yes | Date (YYYY-MM-DD HH:MM:SS) | Must be on or before due date |
| Due Date | Yes | Date (YYYY-MM-DD HH:MM:SS) | Must be on or after issue date |
| Amount | Yes | Numeric | Total amount of document |
| Currency Code | Yes | String | Valid currency code from system currencies |
| Currency Rate | Yes | Numeric | Greater than 0 |
| Contact | Yes | Reference | Must select existing customer (for invoices) or vendor (for bills) |
| Category | Yes | Reference | Must select existing category |

### Line Items

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Item Name | Yes | String | Required for each line item |
| Quantity | Yes | Numeric | Maximum 10 digits; 12 digits if decimals are used |
| Unit Price | Yes | Amount | Valid currency amount |

### Attachments

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| File Type | No | File | Allowed types: jpg, jpeg, png, gif, pdf, doc, docx, xls, xlsx, csv |
| File Size | No | File | Maximum size configured in system settings (typically 2MB) |
| Logo | No | Image | Maximum dimensions: 1000x1000 pixels |

---

## Contact Validation Rules

<!-- Source: app/Http/Requests/Common/Contact.php -->

### Customers & Vendors

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Type | Yes | String | Must be "customer" or "vendor" |
| Name | Yes | String | Contact display name |
| Email | Conditional | Email (RFC format) | Unique per company and contact type; validated as proper email format |
| Currency | Yes | String | Valid currency code from system currencies |
| Enabled | No | Boolean | Active/inactive status; defaults to enabled |
| Logo | No | Image | Maximum dimensions configured in system settings |

### Contact Persons

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Name | No | String | Additional contact person name |
| Email | No | Email (RFC format) | Must be valid email format if provided |
| Phone | No | String | Contact phone number |

---

## Item Validation Rules

<!-- Source: app/Http/Requests/Common/Item.php -->

### Products & Services

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Type | Yes | String | Must be "product" or "service" |
| Name | Yes | String | Item display name |
| Sale Price | Conditional | Numeric | Required if sale information is enabled; maximum 14-16 digits; must contain valid numbers |
| Purchase Price | Conditional | Numeric | Required if purchase information is enabled; maximum 14-16 digits; must contain valid numbers |
| Tax IDs | No | Array | Valid tax rate references from system tax settings |
| Category | No | Reference | Valid category reference |
| Enabled | No | Boolean | Active/inactive status |
| Picture | No | Image | Allowed file types and maximum dimensions per system configuration |

**Note:** Either sale price or purchase price must be provided. If sale information is enabled, sale price becomes required. If purchase information is enabled, purchase price becomes required.

---

## Transaction Validation Rules

<!-- Source: app/Http/Requests/Banking/Transaction.php -->

### Income & Expense

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Type | Yes | String | Must be "income" or "expense" |
| Number | Yes | String | Unique per company; cannot duplicate transaction numbers |
| Account | Yes | Reference | Must select existing bank account |
| Date | Yes | Date (YYYY-MM-DD HH:MM:SS) | Transaction date |
| Amount | Yes | Amount | Must be greater than or equal to 0 |
| Currency Code | Yes | String | Valid currency code from system currencies |
| Currency Rate | Yes | Numeric | Greater than 0 |
| Category | Yes | Reference | Must select existing category |
| Payment Method | Yes | String | Valid payment method from system settings |
| Contact | No | Reference | Optional customer or vendor reference |
| Attachment | No | File | Allowed file types and maximum size per system configuration |

---

## Bank Account Validation Rules

<!-- Source: app/Http/Requests/Banking/Account.php -->

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Type | Yes | String | Account type (bank, cash, etc.) |
| Name | Yes | String | Account display name |
| Number | Yes | String | Account number or identifier |
| Currency | Yes | String | Valid currency code from system currencies |
| Opening Balance | Conditional | Amount | Required; must be a valid amount when account type is "bank" |
| Enabled | No | Boolean | Active/inactive status |

---

## Transfer Validation Rules

<!-- Source: app/Http/Requests/Banking/Transfer.php -->

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| From Account | Yes | Reference | Must be a valid bank account |
| To Account | Yes | Reference | Must be a valid bank account |
| Amount | Yes | Amount | Valid currency amount |
| Date | Yes | Date (YYYY-MM-DD) | Transfer date |
| Payment Method | Yes | String | Valid payment method from system settings |

---

## Reconciliation Validation Rules

<!-- Source: app/Http/Requests/Banking/Reconciliation.php -->

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Account | Yes | Reference | Must be a valid bank account |
| Start Date | Yes | Date (YYYY-MM-DD HH:MM:SS) | Must be before or equal to end date |
| End Date | Yes | Date (YYYY-MM-DD HH:MM:SS) | Must be after or equal to start date |
| Closing Balance | Yes | Numeric | Expected balance at end date |

---

## Tax Rate Validation Rules

<!-- Source: app/Http/Requests/Setting/Tax.php -->

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Name | Yes | String | Tax rate display name |
| Type | Yes | String | Must be one of: fixed, normal, inclusive, withholding, or compound |
| Rate | Yes | Numeric | Between 0 and 100 |
| Enabled | No | Boolean | Active/inactive status |

**Note:** Compound tax type has additional uniqueness constraints per company.

---

## Currency Validation Rules

<!-- Source: app/Http/Requests/Setting/Currency.php -->

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Name | Yes | String | Currency display name |
| Code | Yes | String | Valid currency code; unique per company |
| Rate | Yes | Numeric | Exchange rate; must be greater than 0 |
| Symbol First | No | Boolean | Determines if currency symbol appears before or after amount |
| Decimal Mark | No | String | Character for decimal separator; must differ from thousands separator |
| Thousands Separator | No | String | Character for thousands separator; must differ from decimal mark |
| Enabled | No | Boolean | Active/inactive status |
| Default Currency | No | Boolean | Whether this is the company's default currency |

---

## Category Validation Rules

<!-- Source: app/Http/Requests/Setting/Category.php -->

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Name | Yes | String | Category display name |
| Type | Yes | String | Must be a valid category type from system configuration |
| Color | Yes | String | Valid color code for visual identification |

---

## Recurring Schedule Validation

<!-- Source: app/Http/Requests/Document/Document.php, app/Http/Requests/Banking/Transaction.php -->

These rules apply when setting up recurring invoices, bills, or transactions.

| Field | Required | Format | Constraints |
|-------|----------|--------|-------------|
| Frequency | Conditional | String | Must be one of: daily, weekly, monthly, yearly, or custom |
| Interval | Conditional | Integer | Required when frequency is "custom"; must be 1 or greater |
| Custom Frequency | Conditional | String | Required when frequency is "custom"; must be daily, weekly, monthly, or yearly |
| Start Date | Conditional | Date (YYYY-MM-DD HH:MM:SS) | Required when recurring is enabled |
| Limit Date | Conditional | Date (YYYY-MM-DD HH:MM:SS) | Required if limit type is "date"; must be on or after start date |
| Limit Count | Conditional | Integer | Required if limit type is "count"; must be 0 or greater |

**Note:** Recurring schedules allow automatic generation of invoices, bills, or transactions at specified intervals. The limit can be set by date, count, or left unlimited.

---

## See Also

- [Error Handling](error-handling.md) - User-facing error messages and resolution guidance
- [Conditional Logic](conditional-logic.md) - Dynamic behaviors, calculations, and status transitions
