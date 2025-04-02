# Documentation: `GlobalExceptionHandler.java`

## Overview
The `GlobalExceptionHandler` class is a centralized exception handling mechanism for a Spring Boot application. It uses the `@ControllerAdvice` annotation to intercept and handle exceptions thrown by controllers globally. This approach ensures consistent error responses across the application.

## Features
- Handles specific exceptions (`ConstraintViolationException`, `IllegalArgumentException`) and provides appropriate HTTP responses.
- Provides a fallback mechanism for handling generic exceptions (`Exception`).
- Returns structured error responses using the `ErrorResponse` class.

## Dependencies
The class relies on the following dependencies:
- **Spring Framework**:
  - `@ControllerAdvice`: Marks the class as a global exception handler.
  - `@ExceptionHandler`: Specifies the exception types to handle.
  - `ResponseEntity`: Represents the HTTP response.
  - `HttpStatus`: Defines HTTP status codes.
- **Jakarta Validation**:
  - `ConstraintViolationException`: Represents validation errors.

## Exception Handling Logic

### 1. ConstraintViolationException
Handles validation errors caused by constraints defined in the application (e.g., `@NotNull`, `@Size`).
- **HTTP Status**: `400 BAD_REQUEST`
- **Response Body**:
  - `status`: `BAD_REQUEST`
  - `message`: Validation error message extracted from the exception.

### 2. IllegalArgumentException
Handles cases where invalid arguments are passed to methods.
- **HTTP Status**: `400 BAD_REQUEST`
- **Response Body**:
  - `status`: `BAD_REQUEST`
  - `message`: Exception message.

### 3. Generic Exception
Handles all other uncaught exceptions.
- **HTTP Status**: `500 INTERNAL_SERVER_ERROR`
- **Response Body**:
  - `status`: `INTERNAL_SERVER_ERROR`
  - `message`: Generic error message extracted from the exception.

Additionally, the stack trace of the exception is printed to the console for debugging purposes.

## ErrorResponse Class
The `ErrorResponse` class is used to structure the error response. Although not provided in the code snippet, it is assumed to have the following fields:
- `status`: Represents the HTTP status code as a string.
- `message`: Describes the error.

### Example ErrorResponse Structure
| Field   | Type   | Description                          |
|---------|--------|--------------------------------------|
| status  | String | HTTP status code (e.g., `BAD_REQUEST`) |
| message | String | Detailed error message              |

## Insights
- **Centralized Error Handling**: The use of `@ControllerAdvice` simplifies exception management by consolidating it into a single class.
- **Custom Error Responses**: The application provides meaningful error messages to clients, improving user experience.
- **Scalability**: Additional exception handlers can be added to handle more specific exceptions as the application grows.
- **Debugging**: Printing the stack trace for generic exceptions aids in identifying issues during development. However, this may need to be disabled or logged securely in production environments.
