# Documentation: `CodigoUtil.java`

## Overview
The `CodigoUtil` class provides utility methods for validating Brazilian CNPJ numbers. A CNPJ (Cadastro Nacional da Pessoa Jurídica) is a unique identifier assigned to companies in Brazil. This class includes logic to verify the validity of a CNPJ based on its checksum calculation.

---

## Class: `CodigoUtil`

### Package
`com.example.supplier.util`

### Purpose
The class is designed to validate CNPJ numbers using the official algorithm, which involves calculating two verification digits based on weighted sums of the digits in the CNPJ.

---

## Method Details

### `isValidCNPJ(long cnpj)`
#### Description
Validates a given CNPJ number by checking its format and calculating its checksum using the official algorithm.

#### Parameters
| Name  | Type   | Description                          |
|-------|--------|--------------------------------------|
| `cnpj` | `long` | The CNPJ number to be validated.    |

#### Return Value
| Type      | Description                              |
|-----------|------------------------------------------|
| `boolean` | Returns `true` if the CNPJ is valid, otherwise `false`. |

#### Logic
1. **Formatting**: Converts the `long` CNPJ number into a 14-character string, padding with leading zeros if necessary.
2. **Length Check**: Ensures the CNPJ string has exactly 14 characters.
3. **Checksum Calculation**:
   - **First Verification Digit**:
     - Uses the first 12 digits of the CNPJ and multiplies them by a predefined weight array (`weight1`).
     - Computes the sum of the products and calculates the modulus (`mod`) by 11.
     - Determines the first verification digit based on the modulus.
   - **Second Verification Digit**:
     - Uses the first 13 digits of the CNPJ and multiplies them by another predefined weight array (`weight2`).
     - Computes the sum of the products and calculates the modulus (`mod`) by 11.
     - Determines the second verification digit based on the modulus.
4. **Validation**: Compares the calculated verification digits with the last two digits of the CNPJ.
5. **Error Handling**: Returns `false` if any exception occurs during processing.

#### Example Usage
```java
long cnpj = 12345678000195L; // Example CNPJ
System.out.println("CNPJ is valid: " + CodigoUtil.isValidCNPJ(cnpj));
```

---

### `main(String[] args)`
#### Description
A simple entry point to test the `isValidCNPJ` method with a sample CNPJ number.

#### Parameters
| Name  | Type       | Description                          |
|-------|------------|--------------------------------------|
| `args` | `String[]` | Command-line arguments (not used).  |

#### Behavior
- Calls the `isValidCNPJ` method with a hardcoded example CNPJ (`12345678000195L`).
- Prints the result of the validation to the console.

---

## Insights

### Validation Algorithm
- The validation algorithm adheres to the official CNPJ checksum rules:
  - The first verification digit is calculated using weights `[5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2]`.
  - The second verification digit is calculated using weights `[6, 5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2]`.
- The modulus operation (`mod % 11`) determines the verification digits, with special handling for cases where `mod < 2`.

### Error Handling
- The method gracefully handles exceptions (e.g., invalid input or unexpected errors) by returning `false`.

### Limitations
- The method assumes the input CNPJ is a valid `long` number. It does not handle cases where the input is in a different format (e.g., a string with special characters).
- The hardcoded example in the `main` method may not represent a real-world CNPJ.

### Practical Applications
- This utility can be integrated into systems that require validation of Brazilian company identifiers, such as financial systems, e-commerce platforms, or government applications.

---

## File Metadata
| Key         | Value                  |
|-------------|------------------------|
| `FILE_NAME` | `CodigoUtil.java`      |
