# SupplierService Documentation

## Overview
The `SupplierService` class is a service layer in a Spring-based application that manages operations related to suppliers. It interacts with the `SupplierRepository` to perform CRUD (Create, Read, Update, Delete) operations and includes validation logic for supplier data, such as verifying the validity of a CNPJ (Brazilian company registration number).

---

## Class Details

### Package
`com.example.supplier.service`

### Annotations
- `@Service`: Marks the class as a Spring service component, making it eligible for Spring's component scanning and dependency injection.

---

## Dependencies

### Injected Dependencies
| Dependency              | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| `SupplierRepository`     | Repository interface for database operations related to `Supplier` entities. |
| `CodigoUtil`             | Utility class for validating CNPJ values.                                   |

---

## Methods

### `createSupplier(Supplier supplier)`
Creates a new supplier in the database after validating the CNPJ.

#### Parameters
| Name       | Type      | Description                     |
|------------|-----------|---------------------------------|
| `supplier` | `Supplier`| The supplier entity to be created. |

#### Returns
| Type      | Description                     |
|-----------|---------------------------------|
| `Supplier`| The saved supplier entity.      |

#### Exceptions
| Type                        | Description                     |
|-----------------------------|---------------------------------|
| `IllegalArgumentException`  | Thrown if the CNPJ is invalid. |

---

### `getAllSuppliers()`
Retrieves all suppliers from the database.

#### Parameters
None.

#### Returns
| Type            | Description                     |
|------------------|---------------------------------|
| `List<Supplier>`| List of all supplier entities.  |

---

### `getSupplierById(Long id)`
Fetches a supplier by its unique identifier.

#### Parameters
| Name | Type   | Description                     |
|------|--------|---------------------------------|
| `id` | `Long` | The unique identifier of the supplier. |

#### Returns
| Type                | Description                     |
|---------------------|---------------------------------|
| `Optional<Supplier>`| The supplier entity wrapped in an `Optional`. |

---

### `updateSupplier(Long id, Supplier supplierDetails)`
Updates an existing supplier's details after validating the CNPJ.

#### Parameters
| Name              | Type      | Description                     |
|-------------------|-----------|---------------------------------|
| `id`              | `Long`    | The unique identifier of the supplier to be updated. |
| `supplierDetails` | `Supplier`| The updated supplier details.   |

#### Returns
| Type      | Description                     |
|-----------|---------------------------------|
| `Supplier`| The updated supplier entity.    |

#### Exceptions
| Type                        | Description                     |
|-----------------------------|---------------------------------|
| `IllegalArgumentException`  | Thrown if the CNPJ is invalid. |
| `RuntimeException`           | Thrown if the supplier is not found. |

---

### `deleteSupplier(Long id)`
Deletes a supplier by its unique identifier.

#### Parameters
| Name | Type   | Description                     |
|------|--------|---------------------------------|
| `id` | `Long` | The unique identifier of the supplier to be deleted. |

#### Returns
| Type     | Description                     |
|----------|---------------------------------|
| `boolean`| Returns `true` if the deletion is successful. |

#### Exceptions
| Type              | Description                     |
|-------------------|---------------------------------|
| `RuntimeException`| Thrown if the supplier is not found. |

---

## Insights

1. **Validation Logic**: The class uses `CodigoUtil.isValidCNPJ` to ensure that the CNPJ is valid before creating or updating a supplier. This adds a layer of data integrity to the application.

2. **Error Handling**: The service throws specific exceptions (`IllegalArgumentException` and `RuntimeException`) to handle invalid input and missing entities, respectively. This ensures clear communication of errors to the caller.

3. **CRUD Operations**: The class provides complete CRUD functionality for suppliers, making it a central component for supplier management.

4. **Optional Usage**: The `getSupplierById` method returns an `Optional<Supplier>`, which is a good practice for handling potentially null values.

5. **Spring Integration**: The use of `@Service` and `@Autowired` annotations demonstrates seamless integration with the Spring framework for dependency injection and service management.
