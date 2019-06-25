### Модель Northwind

| PK Table      | Cardinality PK Table | FK Table             | Cardinality FK Table | Relationship |
| ------------- | -------------------- | -------------------- | -------------------- | ------------ |
| shippers      | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| employees     | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| employees     | Zero-or-One          | employees            |  One-or-Many         | One-to-Many  |
| employees     | -                    | territories          | -                    | Many-to-Many |
| customers     | Zero-or-One          | orders               |  One-or-Many         | One-to-Many  |
| customers     | -                    | customerdemographics | -                    | Many-to-Many |
| orders        | One-and-Only-One     | orderdetails         |  One-or-Many         | One-to-Many  |
| products      | One-and-Only-One     | orderdetails         |  One-or-Many         | One-to-Many  |
| suppliers     | Zero-or-One          | products             |  One-or-Many         | One-to-Many  |
| categories    | Zero-or-One          | products             |  One-or-Many         | One-to-Many  |
| region        | One-and-Only-One     | territories          |  One-or-Many         | One-to-Many  |

### Northwind OData Service

| Query Description                                    | HTTP Verb | Url                                                              |
| -----------------------------------------------------| --------- | ---------------------------------------------------------------- |
| Get service metadata.                                | GET       | /$metadata                                                       |
| Get all customers.                                   | GET       | /Customers                                                       |
| Get a customer with "ALFKI" id.                      | GET       | /Customers('ALFKI')                                              |
| Get all orders.                                      | GET       | /Orders                                                          |
| Get an order with "10248" id.                        | GET       | /Orders(10248)                                                   |
| Get all orders for a customer with "ANATR" id.       | GET       | /Customers('ANATR')/Orders                                       |
| Get a customer for an order with "10248" id.         | GET       | /Orders(10248)/Customer                                          |
|                                                      |           |                                                                  |
| Get a customer CompanyName with "ALFKI" id.          | GET       | /Customers('ALFKI')/CompanyName/$value                           |
| Get all customers from Germany.                      | GET       | /Customers?$filter=Country eq 'Germany'                          |
| Get order details with "10308" id.                   | GET       | /Customers('ANATR')/Orders(10308)/Order_Details                  |
| Get first 5 products.                                | GET       | /Products?$top=5                                                 |
| Get all products with price between 18 and 20.       | GET       | /Products?$filter=UnitPrice le 20.0000 and UnitPrice gt 18.0000  |
| Get product Chai.                                    | GET       | /Products?$filter=ProductName eq 'Chai'                          |
| Sort products.                                       | GET       | /Products?$orderby=ProductName                                   |
| Counting products.                                   | GET       | /Products/$count                                                 |
| Select CompanyName and Country from Suppliers.       | GET       | /Suppliers?$select=CompanyName,Country                           |

#### Утилизация потоков в асинхронной модели

| Breakpoint | Thread ID   | Thread Managed ID | Thread Name   |
| ---------- | ----------- | ----------------- | ------------- |
| #1.1       | 15872       | 1	               | Main Thread   |
| #1.2       | 16276       | 7                 | Worked Thread |
| #1.3       | 15872       | 1	               | Main Thread   |
| #2.1       | 15540       | 1	               | Main Thread   |
| #2.2       | 16264       | 7                 | Worked Thread |
| #2.3       | 16264       | 7                 | Worked Thread |
