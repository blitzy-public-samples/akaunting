# Capabilities Inventory

<!-- Source: app/Http/Controllers/**, routes/admin.php, routes/portal.php -->

## Overview

Akaunting is an open-source, online accounting application designed for small to medium businesses to manage their finances, track income and expenses, generate invoices, and produce financial reports—all from a web browser.

---

## Sales Capabilities

<!-- Source: app/Http/Controllers/Sales/Invoices.php, app/Http/Controllers/Sales/RecurringInvoices.php, app/Http/Controllers/Sales/Customers.php -->

The Sales module enables businesses to manage customer relationships and revenue generation through invoicing and payment tracking.

### Invoice Management

- **Invoice Creation** – Create professional invoices with customer details, line items, taxes, discounts, and due dates.
- **Invoice Editing** – Modify draft or existing invoices to update amounts, items, or customer information.
- **Invoice Viewing** – View complete invoice details including line items, totals, payment history, and document history.
- **Invoice Sending** – Send invoices directly to customers via email with PDF attachments.
- **Invoice PDF Generation** – Generate and download professional PDF versions of invoices for printing or manual delivery.
- **Invoice Printing** – Print invoices directly from the browser for physical distribution.
- **Invoice Duplication** – Clone existing invoices to quickly create similar invoices for repeat transactions.
- **Invoice Status Tracking** – Track invoice status through draft, sent, viewed, paid, and cancelled states.
- **Mark as Sent** – Manually mark an invoice as sent when delivered through alternative channels.
- **Mark as Cancelled** – Cancel invoices that are no longer valid or were created in error.
- **Invoice Restoration** – Restore previously cancelled invoices to active status.
- **Invoice Import** – Bulk import invoices from Excel or CSV files to quickly populate historical data.
- **Invoice Export** – Export invoice data to Excel format for external analysis or backup.
- **Invoice Deletion** – Remove invoices that are no longer needed from the system.

### Recurring Invoices

- **Recurring Invoice Setup** – Create recurring invoice templates that automatically generate invoices on a schedule.
- **Recurring Schedule Configuration** – Define frequency (daily, weekly, monthly, yearly) and duration for automatic invoicing.
- **End Recurring Schedule** – Stop a recurring invoice series when no longer needed.
- **Recurring Invoice Duplication** – Clone recurring invoice templates for similar customers.
- **Recurring Invoice Import/Export** – Bulk import or export recurring invoice configurations.

### Customer Management

- **Customer Creation** – Add new customer records with contact details, billing address, and tax information.
- **Customer Editing** – Update customer information including addresses, payment terms, and contact persons.
- **Customer Viewing** – View complete customer profiles including invoice history and outstanding balances.
- **Customer Enabling/Disabling** – Activate or deactivate customer accounts without deleting historical data.
- **Customer Duplication** – Clone customer records to quickly add similar customers.
- **Quick Invoice Creation** – Create a new invoice directly from a customer's profile.
- **Quick Income Recording** – Record a payment or income directly from a customer's profile.
- **Customer Import** – Bulk import customer data from Excel or CSV files.
- **Customer Export** – Export customer data to Excel format.

---

## Purchases Capabilities

<!-- Source: app/Http/Controllers/Purchases/Bills.php, app/Http/Controllers/Purchases/RecurringBills.php, app/Http/Controllers/Purchases/Vendors.php -->

The Purchases module enables businesses to track expenses, manage vendor relationships, and record payments for goods and services received.

### Bill Management

- **Bill Recording** – Enter vendor bills with line items, taxes, amounts, and due dates.
- **Bill Editing** – Modify bill details including amounts, items, or vendor information.
- **Bill Viewing** – View complete bill details including line items, payment status, and history.
- **Bill PDF Generation** – Generate and download PDF versions of bills for record-keeping.
- **Bill Printing** – Print bills directly from the browser.
- **Bill Duplication** – Clone existing bills to quickly record similar expenses.
- **Bill Status Tracking** – Track bill status through draft, received, paid, and cancelled states.
- **Mark as Received** – Confirm receipt of goods or services for a recorded bill.
- **Mark as Cancelled** – Cancel bills that are no longer valid.
- **Bill Restoration** – Restore previously cancelled bills to active status.
- **Bill Import** – Bulk import bills from Excel or CSV files.
- **Bill Export** – Export bill data to Excel format.
- **Bill Deletion** – Remove bills from the system.

### Recurring Bills

- **Recurring Bill Setup** – Create recurring bill templates for regular expenses like rent or subscriptions.
- **Recurring Schedule Configuration** – Define frequency and duration for automatic bill generation.
- **End Recurring Schedule** – Stop a recurring bill series when the expense ends.
- **Recurring Bill Duplication** – Clone recurring bill templates.
- **Recurring Bill Import/Export** – Bulk import or export recurring bill configurations.

### Vendor Management

- **Vendor Creation** – Add new vendor records with contact details, payment information, and tax identifiers.
- **Vendor Editing** – Update vendor information and payment preferences.
- **Vendor Viewing** – View complete vendor profiles including bill history and payment records.
- **Vendor Enabling/Disabling** – Activate or deactivate vendor accounts.
- **Vendor Duplication** – Clone vendor records.
- **Quick Bill Creation** – Create a new bill directly from a vendor's profile.
- **Quick Expense Recording** – Record a payment directly from a vendor's profile.
- **Vendor Import** – Bulk import vendor data from Excel or CSV files.
- **Vendor Export** – Export vendor data to Excel format.

---

## Banking Capabilities

<!-- Source: app/Http/Controllers/Banking/Accounts.php, app/Http/Controllers/Banking/Transactions.php, app/Http/Controllers/Banking/Transfers.php, app/Http/Controllers/Banking/Reconciliations.php -->

The Banking module provides tools to manage bank accounts, record financial transactions, and reconcile records with bank statements.

### Account Management

- **Bank Account Creation** – Add bank accounts, cash accounts, or credit card accounts to track balances.
- **Account Editing** – Update account details including name, currency, and starting balance.
- **Account Viewing** – View account details with transaction history and current balance.
- **Account Summary** – See incoming, outgoing, and current balance summaries for each account.
- **Account Enabling/Disabling** – Activate or deactivate accounts without losing transaction history.
- **Account Duplication** – Clone account configurations.
- **Quick Actions** – Create income, expense, or transfer transactions directly from an account view.
- **Performance View** – See account performance metrics and trends.

### Transaction Management

- **Income Recording** – Record payments received from customers or other income sources.
- **Expense Recording** – Record payments made for purchases, bills, or other expenses.
- **Transaction Editing** – Modify transaction details including amounts, categories, and dates.
- **Transaction Viewing** – View complete transaction details including linked documents.
- **Transaction Duplication** – Clone transactions for similar entries.
- **Transaction PDF** – Generate PDF receipts for transactions.
- **Transaction Email** – Send transaction confirmations via email.
- **Transaction Categorization** – Assign categories to transactions for reporting.
- **Transaction Import** – Bulk import transactions from Excel or CSV files (bank statement imports).
- **Transaction Export** – Export transaction data to Excel format.
- **Transaction Deletion** – Remove transactions from the system.
- **Document Connection** – Link transactions to related invoices or bills.

### Recurring Transactions

- **Recurring Transaction Setup** – Create templates for regular income or expense transactions.
- **Schedule Configuration** – Define frequency and duration for automatic transaction creation.
- **End Recurring Schedule** – Stop a recurring transaction series.
- **Recurring Transaction Duplication** – Clone recurring transaction templates.
- **Recurring Transaction Import/Export** – Bulk manage recurring transaction configurations.

### Bank Transfers

- **Transfer Recording** – Record transfers between bank accounts.
- **Transfer Viewing** – View transfer details including source and destination accounts.
- **Transfer PDF** – Generate PDF documentation for transfers.
- **Transfer Duplication** – Clone transfer records.
- **Transfer Import/Export** – Bulk manage transfer records.

### Bank Reconciliation

- **Reconciliation Creation** – Start a new reconciliation period for a bank account.
- **Transaction Matching** – Match recorded transactions with bank statement entries.
- **Opening Balance Calculation** – Automatically calculate opening balances for reconciliation periods.
- **Closing Balance Entry** – Enter the closing balance from bank statements.
- **Reconciliation Status** – Track reconciliation progress (in progress vs. completed).
- **Reconciliation History** – View historical reconciliation records.

---

## Items & Contacts

<!-- Source: app/Http/Controllers/Common/Items.php, app/Http/Controllers/Common/Contacts.php -->

These modules manage the products, services, and contacts used throughout the application.

### Item Management

- **Item Creation** – Create reusable products or services with names, prices, and tax settings.
- **Item Editing** – Update item details including pricing and descriptions.
- **Item Viewing** – View item details and usage history.
- **Item Enabling/Disabling** – Activate or deactivate items without deletion.
- **Item Duplication** – Clone item configurations.
- **Item Import** – Bulk import items from Excel or CSV files.
- **Item Export** – Export item data to Excel format.
- **Default Tax Assignment** – Assign default taxes to items for automatic calculation on invoices and bills.

### Contact Management

- **Unified Contact View** – View all customers and vendors in a single contact list.
- **Contact Search** – Search and filter contacts by name, type, or other attributes.

---

## Reports Capabilities

<!-- Source: app/Http/Controllers/Common/Reports.php, app/Reports/IncomeSummary.php, app/Reports/ExpenseSummary.php, app/Reports/ProfitLoss.php, app/Reports/TaxSummary.php -->

The Reports module provides financial insights through various summary and detailed reports.

### Standard Reports

- **Income Summary** – View total income by category and time period with chart visualizations.
- **Expense Summary** – View total expenses by category and time period with chart visualizations.
- **Income vs Expense** – Compare income against expenses over a selected period.
- **Profit & Loss Statement** – Generate comprehensive profit and loss reports showing net income.
- **Tax Summary** – View collected and paid taxes by tax type and period for compliance reporting.

### Report Operations

- **Report Generation** – Generate reports for selected date ranges and filters.
- **Report Printing** – Print reports directly from the browser.
- **Report PDF Export** – Download reports as PDF documents.
- **Report Data Export** – Export report data to Excel for further analysis.
- **Report Customization** – Create custom report configurations with specific filters.
- **Report Duplication** – Clone report configurations.
- **Basis Selection** – Choose between cash basis and accrual basis accounting for reports.
- **Period Comparison** – Compare financial data across different time periods.

---

## Settings Capabilities

<!-- Source: app/Http/Controllers/Settings/Company.php, app/Http/Controllers/Settings/Currencies.php, app/Http/Controllers/Settings/Taxes.php, app/Http/Controllers/Settings/Categories.php, routes/admin.php -->

The Settings module allows customization of application behavior, company information, and financial configurations.

### Company Settings

- **Company Profile** – Configure business name, address, logo, and contact information.
- **Company Logo Upload** – Upload and manage the company logo displayed on documents.

### Localization Settings

- **Date Format** – Configure preferred date display format.
- **Financial Year** – Set the fiscal year start date.
- **Timezone** – Configure the company's timezone.

### Currency Management

- **Currency Creation** – Add currencies with codes, symbols, and precision settings.
- **Currency Editing** – Update currency details and exchange rates.
- **Default Currency** – Set the primary currency for the business.
- **Currency Enabling/Disabling** – Activate or deactivate currencies.
- **Exchange Rate Management** – Set and update exchange rates for multi-currency transactions.

### Tax Configuration

- **Tax Rate Creation** – Define tax rates with names, percentages, and types.
- **Tax Types** – Configure normal, inclusive, compound, fixed, and withholding taxes.
- **Tax Editing** – Modify tax rate details.
- **Tax Enabling/Disabling** – Activate or deactivate tax rates.
- **Tax Import/Export** – Bulk manage tax rate configurations.
- **Default Tax Assignment** – Set default taxes for new documents.

### Category Management

- **Category Creation** – Create categories for income, expenses, and items.
- **Subcategory Support** – Organize categories with parent-child relationships.
- **Category Editing** – Modify category names and hierarchies.
- **Category Enabling/Disabling** – Activate or deactivate categories.
- **Category Import/Export** – Bulk manage category configurations.

### Invoice Settings

- **Invoice Numbering** – Configure invoice number prefix and sequence.
- **Payment Terms** – Set default payment terms for invoices.
- **Invoice Template** – Customize invoice appearance and layout.

### Email Settings

- **SMTP Configuration** – Configure email server settings for sending invoices.
- **Email Templates** – Customize email content for invoices and notifications.

### Default Settings

- **Default Account** – Set the default bank account for transactions.
- **Default Payment Method** – Configure preferred payment methods.
- **Default Categories** – Set default categories for income and expenses.

### Schedule Settings

- **Command Scheduling** – Configure automated tasks like recurring invoice generation.

---

## Dashboard Capabilities

<!-- Source: app/Http/Controllers/Common/Dashboards.php -->

The Dashboard provides an at-a-glance view of business financial health.

### Dashboard Management

- **Dashboard Viewing** – View financial summaries with widgets showing key metrics.
- **Dashboard Creation** – Create custom dashboards with selected widgets.
- **Dashboard Editing** – Customize dashboard layout and widgets.
- **Dashboard Switching** – Switch between multiple saved dashboards.
- **Dashboard Enabling/Disabling** – Activate or deactivate dashboards.
- **Widget Configuration** – Add, remove, and arrange dashboard widgets.
- **Date Range Selection** – Filter dashboard data by selected time periods.

---

## Portal Capabilities

<!-- Source: app/Http/Controllers/Portal/Invoices.php, app/Http/Controllers/Portal/Payments.php, routes/portal.php -->

The Customer Portal provides a self-service interface for customers to manage their invoices and payments.

### Invoice Access

- **Invoice Viewing** – Customers view their outstanding and historical invoices.
- **Invoice PDF Download** – Customers download PDF copies of their invoices.
- **Invoice Printing** – Customers print invoices from the portal.
- **Invoice Payment** – Customers pay invoices online through integrated payment gateways.

### Payment History

- **Payment Viewing** – Customers view their payment history and receipts.
- **Payment PDF** – Customers download PDF receipts for payments made.
- **Payment Printing** – Customers print payment receipts.

### Profile Management

- **Profile Editing** – Customers update their contact information and preferences.
- **Overdue Invoice Notifications** – Customers view notifications about overdue invoices.

---

## Modules (App Store) Capabilities

<!-- Source: app/Http/Controllers/Modules/Home.php, app/Http/Controllers/Modules/Item.php, routes/admin.php -->

The App Store enables extension of Akaunting functionality through installable modules.

### Module Discovery

- **App Store Browse** – Explore available modules organized by category.
- **Module Search** – Find specific modules by name or functionality.
- **Category Filtering** – Browse modules by category (paid, free, new).
- **Vendor Browsing** – View modules from specific developers.
- **Module Details** – View detailed information, screenshots, and reviews for modules.

### Module Installation

- **Module Installation** – Download and install modules from the app store.
- **Installation Progress** – Track download, extraction, and installation steps.
- **Module Documentation** – Access documentation for installed modules.

### Module Management

- **Module Enabling** – Enable installed modules to activate their features.
- **Module Disabling** – Disable modules without uninstalling to temporarily deactivate features.
- **Module Uninstallation** – Remove modules and their data from the system.
- **Module Updates** – Check for and install module updates.
- **Module Settings** – Configure module-specific settings.

---

## Multi-Company Support

<!-- Source: routes/admin.php, app/Http/Controllers/Common/Companies.php -->

Akaunting supports managing multiple businesses from a single installation.

- **Company Creation** – Add new companies with separate financial data.
- **Company Switching** – Switch between companies to view or manage different businesses.
- **Company Enabling/Disabling** – Activate or deactivate companies.
- **Separate Data** – Each company maintains completely separate financial records.

---

## User Management

<!-- Source: routes/admin.php, app/Http/Controllers/Auth/Users.php -->

User management capabilities for controlling access to the application.

- **User Creation** – Add new users with login credentials.
- **User Editing** – Update user information and permissions.
- **User Enabling/Disabling** – Activate or deactivate user accounts.
- **User Invitation** – Send email invitations to new users.
- **Profile Management** – Users update their own profile and preferences.
- **Notification Preferences** – Configure bill and invoice notification settings.

---

## See Also

- [User Roles and Permissions](user-roles-and-permissions.md) – Detailed information about access control and permission levels
- [Invoice Creation and Payment Flow](../02-user-flows/invoice-creation-and-payment/flow-document.md) – Step-by-step guide for creating and collecting payment on invoices
- [Bill Recording and Payment Flow](../02-user-flows/bill-recording-and-payment/flow-document.md) – Step-by-step guide for recording and paying bills
- [Bank Reconciliation Flow](../02-user-flows/bank-reconciliation/flow-document.md) – Step-by-step guide for reconciling bank accounts
