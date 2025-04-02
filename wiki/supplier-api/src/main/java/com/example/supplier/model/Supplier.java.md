# Documentation: Supplier Data Structure

## Overview
The `Supplier` class is a data structure representing a supplier entity in a system. It is annotated with JPA (Jakarta Persistence API) annotations to map it to a database table. This class contains fields for supplier details, including identification, contact information, and business registration number.

## Metadata
- **File Name**: `Supplier.java`
- **Package**: `com.example.supplier.model`

## Class Details

### Annotations
| Annotation                  | Purpose                                                                 |
|-----------------------------|-------------------------------------------------------------------------|
| `@Entity`                   | Marks the class as a JPA entity, mapping it to a database table.        |
| `@Id`                       | Specifies the primary key of the entity.                               |
| `@GeneratedValue(strategy = GenerationType.IDENTITY)` | Configures the primary key to be auto-generated using the identity strategy. |

### Fields
| Field Name       | Type    | Description                                                                 |
|-------------------|---------|-----------------------------------------------------------------------------|
| `id`             | `Long`  | Unique identifier for the supplier.                                         |
| `nome`           | `String`| Name of the supplier.                                                       |
| `cnpj`           | `long`  | Business registration number (CNPJ) of the supplier.                       |
| `nomeContato`    | `String`| Name of the contact person for the supplier.                                |
| `emailContato`   | `String`| Email address of the contact person.                                        |
| `telefoneContato`| `String`| Phone number of the contact person.                                         |

### Methods
| Method Name               | Return Type | Description                                                                 |
|---------------------------|-------------|-----------------------------------------------------------------------------|
| `getId()`                 | `Long`      | Retrieves the unique identifier of the supplier.                           |
| `setId(Long id)`          | `void`      | Sets the unique identifier of the supplier.                                |
| `getNome()`               | `String`    | Retrieves the name of the supplier.                                        |
| `setNome(String nome)`    | `void`      | Sets the name of the supplier.                                             |
| `getCnpj()`               | `long`      | Retrieves the business registration number (CNPJ) of the supplier.         |
| `setCnpj(long cnpj)`      | `void`      | Sets the business registration number (CNPJ) of the supplier.              |
| `getNomeContato()`        | `String`    | Retrieves the name of the contact person for the supplier.                 |
| `setNomeContato(String nomeContato)` | `void` | Sets the name of the contact person for the supplier.                      |
| `getEmailContato()`       | `String`    | Retrieves the email address of the contact person.                         |
| `setEmailContato(String emailContato)` | `void` | Sets the email address of the contact person.                              |
| `getTelefoneContato()`    | `String`    | Retrieves the phone number of the contact person.                          |
| `setTelefoneContato(String telefoneContato)` | `void` | Sets the phone number of the contact person.                               |

## Insights
- **Persistence**: The class is designed for persistence using JPA, making it suitable for integration with relational databases.
- **Encapsulation**: The fields are private and accessed via getter and setter methods, ensuring encapsulation.
- **Contact Information**: The class includes detailed contact information fields (`nomeContato`, `emailContato`, `telefoneContato`), which are useful for communication purposes.
- **CNPJ Field**: The `cnpj` field is a long type, which is appropriate for storing numeric business registration numbers in Brazil.
- **Auto-Generated ID**: The `id` field is auto-generated using the identity strategy, simplifying database operations for primary key management.
