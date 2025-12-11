# Error Handling

<!-- Source: resources/lang/en-GB/validation.php, resources/lang/en-GB/messages.php, resources/lang/en-GB/errors.php -->

## Overview

Akaunting provides clear, actionable error messages to help users identify and resolve issues quickly. Errors are displayed prominently on the screen when they occur, with specific guidance on what went wrong and how to fix it.

---

## Validation Errors

<!-- Source: resources/lang/en-GB/validation.php -->

Validation errors appear when user-entered data does not meet the required format or business constraints. These errors display next to the affected field.

### Required Field Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] field is required." | A mandatory field was left empty | Enter a value for the highlighted field |
| "The [field] field is required when [other] is [value]." | A conditionally required field is missing | Fill in the field based on your other selections |
| "The [field] field must have a value." | An empty value was submitted | Provide a valid, non-empty value |

### Format and Type Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] must be a valid email address." | Email format is incorrect | Enter email in correct format (example@domain.com) |
| "The [field] must be a number." | Non-numeric characters in a number field | Enter only numeric values (digits, decimal point) |
| "The [field] must be an integer." | Decimal value in a whole number field | Enter a whole number without decimals |
| "The [field] must be a string." | Wrong data type entered | Enter text characters only |
| "The [field] must be a valid date." | Date format is unrecognized | Enter date in the expected format |
| "The [field] does not match the format [format]." | Input does not follow required pattern | Format the input according to the specified pattern |
| "The [field] must be a valid URL." | URL format is incorrect | Enter a complete URL (https://example.com) |
| "The [field] format is invalid." | General format mismatch | Check the expected format and re-enter |

### Uniqueness and Duplicate Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] has already been taken." | Value already exists in the system | Use a unique value (e.g., different invoice number) |
| "The [field] field has a duplicate value." | Same value appears multiple times | Ensure each entry has a distinct value |

### Date and Time Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] must be a date after [date]." | Date is too early | Select a date after the specified date |
| "The [field] must be a date after or equal to [date]." | Date is before the minimum allowed | Select a date on or after the specified date |
| "The [field] must be a date before [date]." | Date is too late | Select a date before the specified date |
| "The [field] must be a date before or equal to [date]." | Date exceeds the maximum allowed | Select a date on or before the specified date |

### Numeric Range Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] must be greater than [value]." | Value is too small | Enter a number larger than the minimum |
| "The [field] must be greater than or equal to [value]." | Value is below the minimum | Enter a number at least equal to the minimum |
| "The [field] must be less than [value]." | Value is too large | Enter a number smaller than the maximum |
| "The [field] must be less than or equal to [value]." | Value exceeds the maximum | Enter a number at most equal to the maximum |
| "The [field] must be between [min] and [max]." | Value is outside the allowed range | Enter a number within the specified range |

### Length and Size Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] must be at least [min] characters." | Input is too short | Add more characters to meet the minimum length |
| "The [field] must not be greater than [max] characters." | Input exceeds maximum length | Shorten the input to fit within the limit |
| "The [field] must be between [min] and [max] characters." | Input length is outside the range | Adjust input length to be within the specified range |
| "The [field] must be [size] characters." | Input is not the exact required length | Enter exactly the specified number of characters |

### File Upload Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] must be a file of type: [types]." | Wrong file format uploaded | Upload a file with one of the allowed extensions |
| "The [field] must not be greater than [max] kilobytes." | File is too large | Reduce file size or upload a smaller file |
| "The [field] must be at least [min] kilobytes." | File is too small | Upload a file that meets the minimum size |
| "The [field] must be an image." | Non-image file uploaded to image field | Upload an image file (jpg, png, gif) |
| "The [field] has invalid image dimensions." | Image dimensions exceed limits | Resize the image (maximum 1000x1000 pixels) |
| "The [field] failed to upload." | Upload process was interrupted | Try uploading again; check file and connection |
| "The file extension is invalid." | Unsupported file type | Use an allowed file type (pdf, xlsx, csv, jpg, png) |

### Selection and Reference Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The selected [field] is invalid." | Invalid option selected | Choose a valid option from the dropdown list |
| "The [field] confirmation does not match." | Confirmation field differs from original | Ensure both fields contain identical values |
| "The [field] and [other] must be different." | Two fields have the same value | Enter different values for each field |

### Custom Validation Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The [field] code is invalid." | Invalid currency code entered | Select a valid currency from the dropdown |
| "The amount [field] is invalid." | Malformed monetary amount | Enter a valid amount using numbers and decimals |
| "The payment method is invalid." | Invalid payment method selected | Select a valid payment method from the list |
| "The [field] dimensions must be max [width] x [height] px." | Image too large | Resize image to fit within dimension limits |

---

## Business Rule Errors

<!-- Source: resources/lang/en-GB/messages.php, resources/lang/en-GB/invoices.php -->

Business rule errors occur when an action violates Akaunting's business logic, such as payment limits or relationship constraints.

### Payment and Amount Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "Payment not added! The amount you entered passes the total: [amount]" | Payment exceeds the remaining balance | Enter an amount equal to or less than the outstanding balance |
| "The total amount of split must be exactly the same as the [transaction] total: [amount]" | Split transaction amounts don't equal original | Adjust split amounts until they equal the total |
| "[type] not connected! The amount you entered can not exceed the payment total: [amount]" | Connection amount exceeds available total | Enter an amount within the available payment limit |

### Access and Permission Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "You are not allowed to manage this company!" | User lacks permission for this company | Request access from administrator or switch to an authorized company |
| "User not created! [name] already uses this email address." | Duplicate email in customer creation | Use a different email address for this customer |

### File and Import Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "No file selected!" | Import attempted without selecting a file | Select a file before clicking the import button |
| "No email address for this customer!" | Sending invoice to customer without email | Add an email address to the customer record first |

### Category and Type Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "Can not delete the last [type] category!" | Attempting to delete the only category | Create a new category before deleting this one |
| "Can not delete the transfer [type] category!" | Attempting to delete system transfer category | This category is required; use another category instead |
| "Can not change the type because it has [text] related!" | Changing type when dependencies exist | Remove all related items before changing the type |

### API and Integration Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "The API Key entered is invalid!" | Invalid API key format or value | Enter a valid API key from your integration provider |
| "You have not entered your API Key!" | API key field is empty | Enter your API key in the settings |

### Invoice and Document Errors

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "Invoice totals are required. Please edit the [type] and save it again." | Document has missing total calculations | Open the document, review line items, and save again |
| "Your invoice must show at least one of the [name] or [description]." | Line items missing required identification | Add a name or description to each line item |

---

## Warning Messages

<!-- Source: resources/lang/en-GB/messages.php -->

Warning messages alert users to potential issues without blocking the action. They appear as yellow/orange notifications.

### Deletion and Modification Warnings

| Warning Message | Cause | Resolution |
|-----------------|-------|------------|
| "You are not allowed to delete [name] because it has [text] related." | Item has dependent records | Remove or reassign related records before deleting |
| "You are not allowed to disable [name] because it has [text] related." | Item has active dependencies | Deactivate related items first |
| "You are not allowed to change/delete transaction because it is reconciled!" | Transaction has been reconciled | Unreconcile the transaction before modifying |
| "You are not allowed to change/delete [type] because it has reconciled transactions!" | Document contains reconciled transactions | Unreconcile all related transactions first |
| "You are not allowed to disable or change the currency of [name] because it has [text] related." | Currency has active usage | Remove dependencies before changing currency settings |

### Transaction Warnings

| Warning Message | Cause | Resolution |
|-----------------|-------|------------|
| "You have cancelled your recent [method] payment!" | User cancelled a payment process | Retry payment if cancellation was unintentional |
| "The transfer related to this transaction is missing." | Orphaned transfer transaction detected | Consider deleting this transaction if transfer is lost |

### Tax Warnings

| Warning Message | Cause | Resolution |
|-----------------|-------|------------|
| "This [type] has a tax amount. Taxes added to the [type] can not be connected, so the tax will be added to the total and calculated accordingly." | Tax handling limitation on connection | The system will handle tax calculation automatically |

---

## System Errors

<!-- Source: resources/lang/en-GB/errors.php -->

System errors indicate technical issues or access restrictions beyond data validation.

### HTTP Status Errors

| Error Code | Message | Resolution |
|------------|---------|------------|
| 403 Forbidden | "You can not access this page." | You lack permission to view this page. Contact your administrator to request access |
| 404 Not Found | "We could not find the page you were looking for." | The page does not exist. Check the URL or return to the dashboard |
| 500 Internal Server Error | "We will work on fixing that right away." | A system error occurred. Wait a moment and try again. If the problem persists, contact support |

### Data Access Errors

| Error Type | Message | Resolution |
|------------|---------|------------|
| Record Not Found | "We could not find the record you were looking for." | The record may have been deleted. Check for archived records or return to the list |
| Invalid Amount | "This page contains invalid amounts! Please, contact the system administrator." | Contact your administrator to investigate the data issue |

---

## Import Errors

<!-- Source: resources/lang/en-GB/messages.php -->

Import errors provide specific information about issues found in imported data files.

| Error Message | Cause | Resolution |
|---------------|-------|------------|
| "Column name: [column]. Line number: [line]." | Data issue found in specific row of import file | Open your import file, locate the specified row and column, fix the data, and re-import |
| "Sheet name is not valid. Please, check the sample file." | Excel worksheet has incorrect name | Rename the worksheet to match the expected name from the sample template |

---

## See Also

- [Validation Rules](validation-rules.md) - Detailed field requirements and format specifications
- [Conditional Logic](conditional-logic.md) - Dynamic behavior and calculated field rules
