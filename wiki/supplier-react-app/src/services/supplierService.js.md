# Documentation: `supplierService.js`

## Overview
This file contains utility functions for interacting with a supplier-related API. It provides methods to fetch all suppliers and create a new supplier. The API is hosted on a server defined by the `serverUrl` constant.

---

## Functions

### `getAllSuppliers()`
Fetches all suppliers from the API.

#### **Usage**
```javascript
getAllSuppliers()
    .then(suppliers => console.log(suppliers))
    .catch(error => console.error(error));
```

#### **Details**
- **Endpoint**: `/api/suppliers`
- **HTTP Method**: `GET`
- **Returns**: A promise that resolves to the list of suppliers in JSON format.
- **Error Handling**: Throws an error if the response status is not `ok`.

---

### `createSupplier(supplier)`
Creates a new supplier by sending supplier data to the API.

#### **Usage**
```javascript
const newSupplier = {
    name: 'Supplier Name',
    cnpj: '12.345.678/0001-99',
    address: '123 Supplier Street'
};

createSupplier(newSupplier)
    .then(createdSupplier => console.log(createdSupplier))
    .catch(error => console.error(error));
```

#### **Details**
- **Endpoint**: `/api/suppliers`
- **HTTP Method**: `POST`
- **Parameters**:
  - `supplier` (Object): The supplier data to be sent. Must include a `cnpj` field.
- **Behavior**:
  - Removes all non-numeric characters from the `cnpj` field before sending the request.
  - Sends the supplier data as a JSON payload.
- **Headers**:
  - `Content-Type`: `application/json`
- **Returns**: A promise that resolves to the created supplier object in JSON format.
- **Error Handling**: Throws an error if the response status is not `ok`.

---

## Constants

### `serverUrl`
- **Value**: `'http://localhost:8081'`
- **Purpose**: Base URL for the API endpoints.

---

## Insights

1. **Error Handling**:
   - Both functions include error handling for failed HTTP requests. This ensures that the application can gracefully handle API errors.

2. **Data Sanitization**:
   - The `createSupplier` function sanitizes the `cnpj` field by removing non-numeric characters. This ensures that the data sent to the API is clean and consistent.

3. **Modular Design**:
   - The functions are designed to be reusable and modular, making it easy to integrate them into different parts of the application.

4. **Asynchronous Operations**:
   - Both functions use `async/await` for handling asynchronous operations, which improves readability and simplifies error handling.

5. **API Dependency**:
   - The file assumes the API is running locally on port `8081`. This dependency should be configurable for different environments (e.g., development, staging, production).
