# Akaunting Functional Documentation

<!-- Source: routes/admin.php, routes/portal.php -->
<!-- Documentation Version: Akaunting 3.1.15 -->

## Overview

This documentation provides a comprehensive functional reference for the Akaunting open-source accounting application. It is designed for product teams, business analysts, and stakeholders who need to understand Akaunting's capabilities for requirements writing, system evaluation, or migration planning.

**Target Audience:**
- **Business Analysts** reviewing system capabilities and business rules
- **Product Managers** defining functional requirements or planning enhancements
- **Stakeholders** evaluating Akaunting for system migration or rationalization

**Documentation Scope:**
This documentation covers *what* users can accomplish in Akaunting, not *how* the system is technically implemented. It focuses exclusively on business capabilities, user workflows, and functional behavior from an end-user perspective.

---

## Documentation Structure

This documentation is organized into four major sections:

| Section | Description |
|---------|-------------|
| **01 - Capabilities Overview** | Complete inventory of business capabilities and user roles/permissions |
| **02 - User Flows** | Step-by-step guides for critical business workflows with screenshots |
| **03 - Integrations** | External system connections, data imports, and exports |
| **04 - Business Rules** | Validation rules, error handling, and conditional logic |

---

## Quick Navigation

### 01 - Capabilities Overview

| Document | Description |
|----------|-------------|
| [Capabilities Inventory](01-capabilities-overview/capabilities-inventory.md) | Complete listing of all Akaunting business capabilities organized by functional area (Sales, Purchases, Banking, Reports, Settings, Portal, Modules) |
| [User Roles and Permissions](01-capabilities-overview/user-roles-and-permissions.md) | Role-based access control documentation including Admin, Manager, User, and Customer roles with permission matrix |

### 02 - User Flows

| Flow | Description |
|------|-------------|
| [Invoice Creation and Payment](02-user-flows/invoice-creation-and-payment/flow-document.md) | Complete workflow for creating invoices, sending to customers, and recording payments |
| [Bill Recording and Payment](02-user-flows/bill-recording-and-payment/flow-document.md) | Complete workflow for recording vendor bills and making payments |
| [Bank Reconciliation](02-user-flows/bank-reconciliation/flow-document.md) | Workflow for matching bank statements with recorded transactions |

### 03 - Integrations

| Document | Description |
|----------|-------------|
| [Integration Map](03-integrations/integration-map.md) | Visual diagram of all external integration points including payment gateways, email services, and APIs |
| [Inbound Interfaces](03-integrations/inbound-interfaces.md) | Data import capabilities including file formats, validation rules, and bank feeds |
| [Outbound Interfaces](03-integrations/outbound-interfaces.md) | Data export capabilities including reports, notifications, and API access |

### 04 - Business Rules

| Document | Description |
|----------|-------------|
| [Validation Rules](04-business-rules/validation-rules.md) | Field-level validation requirements organized by entity type (invoices, bills, contacts, items, transactions) |
| [Error Handling](04-business-rules/error-handling.md) | User-facing error messages with causes and resolution guidance |
| [Conditional Logic](04-business-rules/conditional-logic.md) | Dynamic behaviors including calculations, status transitions, and feature toggles |

---

## Getting Started

Choose your path based on your role and objective:

### For Business Analysts Reviewing Capabilities

1. Start with the [Capabilities Inventory](01-capabilities-overview/capabilities-inventory.md) to understand the full scope of Akaunting's functionality
2. Review [User Roles and Permissions](01-capabilities-overview/user-roles-and-permissions.md) to understand access control
3. Examine the [Validation Rules](04-business-rules/validation-rules.md) to understand data requirements

### For Product Managers Defining Requirements

1. Review the [User Flows](02-user-flows/) section to understand critical business processes:
   - [Invoice Creation and Payment](02-user-flows/invoice-creation-and-payment/flow-document.md) for sales processes
   - [Bill Recording and Payment](02-user-flows/bill-recording-and-payment/flow-document.md) for purchase processes
   - [Bank Reconciliation](02-user-flows/bank-reconciliation/flow-document.md) for banking processes
2. Consult [Conditional Logic](04-business-rules/conditional-logic.md) for business rule documentation
3. Reference [Error Handling](04-business-rules/error-handling.md) for expected system responses

### For Stakeholders Evaluating System Migration

1. Begin with the [Capabilities Inventory](01-capabilities-overview/capabilities-inventory.md) to compare features against current systems
2. Review the [Integration Map](03-integrations/integration-map.md) to understand external system connections
3. Examine [Inbound Interfaces](03-integrations/inbound-interfaces.md) for data migration capabilities
4. Check [Outbound Interfaces](03-integrations/outbound-interfaces.md) for reporting and export options

---

## Functional Areas Summary

Akaunting is an open-source accounting application for small to medium businesses, providing the following major functional areas:

### Sales (Invoicing)
Manage customer invoices, record payments, and track accounts receivable. Includes recurring invoices, PDF generation, and email delivery.

### Purchases (Bills)
Track vendor bills, record payments, and manage accounts payable. Includes recurring bills and vendor management.

### Banking
Manage bank accounts, record transactions, make transfers between accounts, and reconcile bank statements.

### Contacts
Maintain customer and vendor records with contact information, payment terms, and transaction history.

### Items
Create and manage products and services with pricing, tax rates, and categorization.

### Reports
Generate financial reports including Profit & Loss, Income Summary, Expense Summary, and Tax Summary.

### Settings
Configure company profile, currencies, tax rates, categories, invoice templates, and email settings.

### Customer Portal
Self-service portal where customers can view invoices, make payments, and manage their account.

### Modules (App Store)
Extend functionality through the App Store with additional modules for payment gateways, integrations, and features.

---

## Version Information

| Attribute | Value |
|-----------|-------|
| **Application** | Akaunting |
| **Version Documented** | 3.1.15 |
| **Documentation Date** | 2024 |
| **Documentation Type** | Functional/Business Documentation |

---

## Document Conventions

This documentation follows these conventions:

- **Bold text** indicates UI elements (buttons, menu items, field names)
- *Italic text* indicates emphasis or terminology definitions
- `Code formatting` is avoided as this is functional, not technical, documentation
- Screenshots show realistic sample data from the application
- Mermaid diagrams visualize workflows and system architecture
- Tables present structured information (validations, permissions, capabilities)

---

## Related Resources

For technical documentation, developer guides, and API references, please consult the Akaunting GitHub repository and official documentation at [akaunting.com](https://akaunting.com).

---

## See Also

- [Capabilities Inventory](01-capabilities-overview/capabilities-inventory.md) - Start here to understand what Akaunting can do
- [Invoice Creation and Payment](02-user-flows/invoice-creation-and-payment/flow-document.md) - Most common user workflow
- [Integration Map](03-integrations/integration-map.md) - External system connections
- [Validation Rules](04-business-rules/validation-rules.md) - Data requirements and constraints
