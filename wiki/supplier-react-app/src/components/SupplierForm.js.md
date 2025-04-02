# SupplierForm.js Documentation

## Overview
The `SupplierForm` component is a React-based form designed to create supplier records. It includes input fields for supplier details, validation logic for the Brazilian CNPJ (Cadastro Nacional da Pessoa Jurídica), and integration with a service to persist supplier data.

---

## Features
- **State Management**: Utilizes React's `useState` hook to manage form data and error messages.
- **CNPJ Validation**: Implements custom logic to validate the Brazilian CNPJ format.
- **Input Masking**: Uses the `react-input-mask` library to enforce a specific format for the CNPJ field.
- **Error Handling**: Displays error messages for invalid input or failed supplier creation.
- **Integration**: Calls the `createSupplier` function from an external service to save supplier data.

---

## Data Structure
The `supplier` state object holds the following fields:
| Field Name       | Description                          | Example Value          |
|-------------------|--------------------------------------|------------------------|
| `nome`           | Supplier's name                     | `"ABC Supplies"`       |
| `cnpj`           | Supplier's CNPJ (formatted)         | `"12.345.678/0001-99"` |
| `nomeContato`    | Contact person's name               | `"John Doe"`           |
| `emailContato`   | Contact person's email address      | `"john.doe@example.com"` |
| `telefoneContato`| Contact person's phone number       | `"123-456-7890"`       |

---

## Logic
### CNPJ Validation
The `validateCNPJ` function ensures the CNPJ is valid by:
1. Removing non-numeric characters.
2. Checking if the cleaned CNPJ has exactly 14 digits.
3. Performing mathematical checks on the first and second verification digits using modulus operations.

### Form Submission
The `handleSubmit` function:
1. Prevents the default form submission behavior.
2. Validates required fields and the CNPJ format.
3. Calls the `createSupplier` service to persist data.
4. Resets the form state upon successful submission.
5. Displays error messages for validation failures or service errors.

---

## Components
### Input Fields
| Field Name       | Type       | Validation         | Mask/Format                  |
|-------------------|------------|--------------------|------------------------------|
| `nome`           | Text       | Required           | None                         |
| `cnpj`           | Text       | Required, Valid CNPJ | `99.999.999/9999-99`         |
| `nomeContato`    | Text       | Required           | None                         |
| `emailContato`   | Email      | Required           | Valid email format           |
| `telefoneContato`| Text       | Required           | None                         |

### Error Display
- Errors are displayed in red text above the form when validation fails or the supplier creation process encounters an issue.

### Submit Button
- Triggers the `handleSubmit` function to validate and submit the form data.

---

## Insights
- **CNPJ Validation Complexity**: The validation logic for CNPJ is robust but could be simplified using external libraries like `cpf-cnpj-validator` for better maintainability.
- **Error Handling**: The error handling mechanism is basic and could be enhanced with more detailed error messages or field-specific validation feedback.
- **Input Masking**: The use of `react-input-mask` ensures consistent formatting for the CNPJ field, improving user experience.
- **Service Integration**: The `createSupplier` function is assumed to handle API calls, but its implementation is not provided. Ensure proper error handling and response validation in the service layer.
- **Accessibility**: The form lacks accessibility features such as ARIA attributes, which could improve usability for users with disabilities.
