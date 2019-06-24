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

#### Утилизация потоков в асинхронной модели

| Breakpoint | Thread ID   | Thread Managed ID | Thread Name   |
| ---------- | ----------- | ----------------- | ------------- |
| #1.1       | 15872       | 1	               | Main Thread   |
| #1.2       | 16276       | 7                 | Worked Thread |
| #1.3       | 15872       | 1	               | Main Thread   |
| #2.1       | 15540       | 1	               | Main Thread   |
| #2.2       | 16264       | 7                 | Worked Thread |
| #2.3       | 16264       | 7                 | Worked Thread |
