# PizzaStore API

A Minimal API implementation using ASP.NET Core and Entity Framework Core with an In-Memory database. This project demonstrates how to perform CRUD operations on a simple "Pizza" entity.

## Features

*   **Minimal API**: Lightweight and fast API built with ASP.NET Core.
*   **Entity Framework Core**: Uses EF Core for data access.
*   **In-Memory Database**: Uses the `Microsoft.EntityFrameworkCore.InMemory` provider for rapid testing and development (data is not persisted to disk).
*   **Swagger/OpenAPI**: Integrated Swagger UI for interactive API documentation and testing.

## Prerequisites

*   [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) or later.

## Getting Started

1.  **Navigate to the project directory**:
    ```bash
    cd PizzaStore
    ```

2.  **Run the application**:
    ```bash
    dotnet run
    ```
    To enable Swagger UI (Development environment):
    ```bash
    dotnet run --environment Development
    ```

3.  **Access the API**:
    The application will start listening on `http://localhost:5000` (or the port shown in your terminal).

## API Endpoints

| Method | Endpoint | Description | Request Body |
| :--- | :--- | :--- | :--- |
| `GET` | `/` | Returns a "Hello World!" message. | N/A |
| `GET` | `/pizzas` | Returns a list of all pizzas. | N/A |
| `GET` | `/pizza/{id}` | Returns a specific pizza by ID. | N/A |
| `POST` | `/pizza` | Creates a new pizza. | JSON (Name, Description) |
| `PUT` | `/pizza/{id}` | Updates an existing pizza. | JSON (Name, Description) |
| `DELETE` | `/pizza/{id}` | Deletes a pizza by ID. | N/A |

## Testing the API

### Using Swagger UI
If running in Development mode, open your browser and navigate to:
`http://localhost:5000/swagger`

### Using cURL

**Create a Pizza:**
```bash
curl -X POST -H "Content-Type: application/json" -d '{"name":"Pepperoni", "description":"Classic"}' http://localhost:5000/pizza
```

**Get All Pizzas:**
```bash
curl http://localhost:5000/pizzas
```

**Get a Single Pizza:**
```bash
curl http://localhost:5000/pizza/1
```

**Update a Pizza:**
```bash
curl -X PUT -H "Content-Type: application/json" -d '{"name":"Pepperoni", "description":"Extra Cheese"}' http://localhost:5000/pizza/1
```

**Delete a Pizza:**
```bash
curl -X DELETE http://localhost:5000/pizza/1
```

## Important Note

This project uses an **In-Memory Database**. This means:
*   Data is stored in RAM.
*   **All data is lost** when the application stops or restarts.
*   There is no physical database file (like `.db` or `.mdf`) to inspect.

## Project Structure

*   `Program.cs`: Contains the application startup logic, middleware configuration, and API route definitions.
*   `Pizza.cs`: Defines the `Pizza` data model.
*   `PizzaDb`: The `DbContext` class managing the session with the database.
