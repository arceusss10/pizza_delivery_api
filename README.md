#  Pizza Delivery API

A secure, production-ready backend service for a pizza delivery application, built with **FastAPI**, **PostgreSQL**, and **JWT authentication**. It supports user registration/login, role-based access, and complete order management capabilities for both users and staff.


##  Features

-  **JWT-based authentication** with access and refresh tokens.
-  **User management**: registration, login, role distinction (`is_staff`, `is_active`).
-  **Order management**: create, read, update, delete pizza orders.
-  **Role-based access control**: staff users can view and manage all orders; regular users can view their own.
-  **Interactive API documentation** with Swagger UI and integrated JWT support.

---

##  Tech Stack

- **Python** (FastAPI)
- **PostgreSQL** (Relational Database)
- **SQLAlchemy** (ORM)
- **Pydantic** (Data validation)
- **fastapi-jwt-auth** (JWT Authentication)
- **Werkzeug** (Password hashing)

---

## How to run the Project
- Install Postgreql
- Install Python
- Git clone the project with ``` git clone https://github.com/arceusss10/pizza_delivery_api.git```
- Create your virtualenv with `Pipenv` or `virtualenv` and activate it.
- Install the requirements 
- Set Up your PostgreSQL database and set its URI in your ```database.py```
```
engine=create_engine('postgresql://postgres:<username>:<password>@localhost/<db_name>',
    echo=True
)
```



---

##  Project Structure

```
.
├── main.py             # FastAPI app with routing and OpenAPI customization
├── auth_routes.py      # Authentication routes (signup, login, refresh)
├── order_routes.py     # Order CRUD operations and admin controls
├── models.py           # SQLAlchemy models for User and Order
├── schemas.py          # Pydantic schemas for request/response validation
├── database.py         # Database engine and session management
├── init_db.py          # Script to initialize DB tables
├── .gitignore

```

---

##  API Endpoints

###  Auth

| Method | Endpoint         | Description                  |
|--------|------------------|------------------------------|
| POST   | `/auth/signup`   | Register a new user          |
| POST   | `/auth/login`    | User login (returns tokens)  |
| GET    | `/auth/refresh`  | Refresh access token         |

---

###  Orders

| Method | Endpoint                    | Access     | Description                           |
|--------|-----------------------------|------------|---------------------------------------|
| POST   | `/orders/order`             | User       | Place a new pizza order               |
| GET    | `/orders/orders`            | Staff only | List all orders                       |
| GET    | `/orders/orders/{id}`       | Staff only | Get specific order by ID              |
| GET    | `/orders/user/orders`       | User       | List current user's orders            |
| GET    | `/orders/user/order/{id}/`  | User       | Get a specific order by ID            |
| PUT    | `/orders/order/update/{id}/`| User       | Update order quantity or size         |
| PATCH  | `/orders/order/update/{id}/`| Staff only | Update order status (e.g. DELIVERED)  |
| DELETE | `/orders/order/delete/{id}/`| User       | Cancel an order                       |

---



