# **goPostgresGorm**
## **Project Structure**
```
goPostgresGorm/
├── middleware/
│   ├── handlers.go
├── models/
│   ├── stock.go
├── router/
│   ├── routes.go
├── .env
├── go.mod
├── go.sum
└── main.go
```
## **Overview**
This repository is a Go project designed to utilize PostgreSQL as the database and GORM as the Object-Relational Mapping (ORM) library. The application is structured to facilitate the management of stock data.

## **Requirements**
- Go (version 1.16 or later)
- PostgreSQL
- GORM library
## **Installation**
1. Clone the repository:

```bash
git clone https://github.com/MikeOnBoard/goPostgresGorm.git
cd goPostgresGorm
```
2. Install the necessary dependencies:

```bash
go mod tidy
```
3. Configure your database connection in the ``.env`` file:

```plaintext
POSTGRES_URL="postgres://postgres:password@localhost:5432/stockdb"
```
## **Usage**
1.Start your PostgreSQL server.

2. Run the application:

```bash
go run main.go
```
3. The server will start on port ``8080``. You can access the API at ``http://localhost:8080``.

## **API Endpoints**
### **Create Stock**
- **Endpoint**: ``POST /stocks``

- **Description**: Adds a new stock record to the database.

- **Request Body**:

```json
{
    "name": "Stock Name",
    "price": 100,
    "company": "Company Name"
}
```
### **Get All Stocks**
- **Endpoint**: ``GET /stocks``
- **Description**: Retrieves all stock records from the database.
### **Get Stock by ID**
- **Endpoint**: ``GET /stocks/{id}``
- **Description**: Fetches a specific stock record by its ID.
### **Update Stock**
- **Endpoint**: ``PUT /stocks/{id}``

- **Description**: Updates an existing stock record.

- **Request Body**:

```json
{
    "name": "Updated Stock Name",
    "price": 150,
    "company": "Updated Company Name"
}
```
### **Delete Stock**
- **Endpoint**: ``DELETE /stocks/{id}``
- **Description**: Deletes a stock record by its ID.
## **File Details**
### **``main.go``**
This is the entry point of the application. It initializes the server and sets up the routes. It loads environment variables and establishes a connection to the PostgreSQL database using GORM.

### **``middleware/handlers.go``**
This file contains the HTTP handlers that implement the logic for each API endpoint. It includes functions to create, retrieve, update, and delete stock records. Each function interacts with the database through the models defined in the ``models`` package.

### **``models/stock.go``**
In this file, the Stock model is defined. It specifies the structure of the stock records, including fields such as ``stockid``, ``name``, ``price``, and ``company``. GORM annotations are used to define database table mappings.

### **``router/routes.go``**
This file defines the routing logic for the application. It sets up the endpoints and links them to the corresponding handler functions. This allows for organized routing and easy addition of new endpoints in the future.

## Environment Variables
The application relies on the following environment variable:

- **POSTGRES_URL**: Connection string for PostgreSQL.
## Conclusion
This project provides a foundational structure for managing stock data using Go, PostgreSQL, and GORM. It serves as a base for further development and customization according to your application's requirements.