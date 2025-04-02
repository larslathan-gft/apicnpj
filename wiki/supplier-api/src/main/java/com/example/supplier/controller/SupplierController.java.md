# Documentation: SupplierController.java

## Overview
The `SupplierController` class is a RESTful controller in a Spring Boot application that manages CRUD operations for `Supplier` entities. It provides endpoints for creating, reading, updating, and deleting suppliers. The controller interacts with the `SupplierService` to perform business logic and data manipulation.

## Class Details

### Package
The class is part of the `com.example.supplier.controller` package.

### Annotations
- `@RestController`: Indicates that this class is a REST controller.
- `@RequestMapping("/api/suppliers")`: Maps all endpoints in this controller to the base URL `/api/suppliers`.

### Dependencies
- **SupplierService**: The service layer responsible for handling business logic related to suppliers. It is injected using `@Autowired`.

## Endpoints

| HTTP Method | Endpoint            | Description                                                                 | Request Body         | Response Type         |
|-------------|---------------------|-----------------------------------------------------------------------------|----------------------|-----------------------|
| `GET`       | `/api/suppliers`    | Retrieves a list of all suppliers.                                          | None                 | `List<Supplier>`      |
| `GET`       | `/api/suppliers/{id}` | Retrieves a specific supplier by its ID.                                    | None                 | `ResponseEntity<Supplier>` |
| `POST`      | `/api/suppliers`    | Creates a new supplier.                                                     | `Supplier`           | `Supplier`            |
| `PUT`       | `/api/suppliers/{id}` | Updates an existing supplier by its ID.                                     | `Supplier`           | `ResponseEntity<Supplier>` |
| `DELETE`    | `/api/suppliers/{id}` | Deletes a supplier by its ID.                                               | None                 | `ResponseEntity<Void>` |

## Method Details

### `getAllSuppliers()`
- **Description**: Fetches all suppliers from the database.
- **Return Type**: `List<Supplier>`
- **Logic**: Delegates the call to `SupplierService.getAllSuppliers()`.

---

### `getSupplierById(Long id)`
- **Description**: Fetches a supplier by its ID.
- **Parameters**:
  - `@PathVariable Long id`: The ID of the supplier to retrieve.
- **Return Type**: `ResponseEntity<Supplier>`
- **Logic**: 
  - Calls `SupplierService.getSupplierById(id)`.
  - Returns `ResponseEntity.ok(supplier)` if the supplier exists.
  - Returns `ResponseEntity.notFound().build()` if the supplier does not exist.

---

### `createSupplier(Supplier supplier)`
- **Description**: Creates a new supplier.
- **Parameters**:
  - `@RequestBody Supplier supplier`: The supplier object to be created.
- **Return Type**: `Supplier`
- **Logic**: Delegates the call to `SupplierService.createSupplier(supplier)`.

---

### `updateSupplier(Long id, Supplier supplierDetails)`
- **Description**: Updates an existing supplier.
- **Parameters**:
  - `@PathVariable Long id`: The ID of the supplier to update.
  - `@RequestBody Supplier supplierDetails`: The updated supplier details.
- **Return Type**: `ResponseEntity<Supplier>`
- **Logic**:
  - Calls `SupplierService.updateSupplier(id, supplierDetails)`.
  - Returns `ResponseEntity.ok(updatedSupplier)` if the update is successful.
  - Returns `ResponseEntity.notFound().build()` if the supplier does not exist.

---

### `deleteSupplier(Long id)`
- **Description**: Deletes a supplier by its ID.
- **Parameters**:
  - `@PathVariable Long id`: The ID of the supplier to delete.
- **Return Type**: `ResponseEntity<Void>`
- **Logic**:
  - Calls `SupplierService.deleteSupplier(id)`.
  - Returns `ResponseEntity.noContent().build()` if the deletion is successful.
  - Returns `ResponseEntity.notFound().build()` if the supplier does not exist.

## Insights

- **Error Handling**: The controller uses `ResponseEntity` to handle cases where a supplier is not found (`404 Not Found`) or when a deletion is successful (`204 No Content`).
- **RESTful Design**: The endpoints follow RESTful principles, using appropriate HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) for CRUD operations.
- **Dependency Injection**: The `SupplierService` is injected using Spring's `@Autowired` annotation, promoting loose coupling between the controller and service layers.
- **Path Variables and Request Body**: The controller uses `@PathVariable` for dynamic URL parameters and `@RequestBody` for JSON payloads in POST and PUT requests.
- **Optional Handling**: The `getSupplierById` method leverages Java's `Optional` to handle null values gracefully.
