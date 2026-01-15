# Grocery Web Application 🛒
A simple full-stack Grocery Management Web Application. It is a 3 tier application,
1. Front end: UI is written in HTML/CSS/Javascript/Bootstrap
2. Backend: Python and Flask
3. Database: mysql
This project demonstrates relational database design, CRUD operations, and a layered backend architecture using the DAO pattern.

![homepage](https://github.com/user-attachments/assets/96f0d73c-a4f1-4e3b-a721-ef9c5ec59e89)



## 🚀 Features

- Add, view, and delete grocery products
- Unit of Measurement (UOM) management
- Create orders with multiple products
- MySQL database with proper primary and foreign key relationships
- Backend API built using Python
- Clear separation between API, database access, and database schema

---

## 🏗️ Project Architecture

```

Frontend (UI)
↓
Backend API (server.py)
↓
DAO Layer
↓
MySQL Database

```

---

## 📁 Project Structure

```

grocery_webapp_main/
│
├── backend/
│   ├── server.py              # API layer
│   ├── sql_connection.py      # Database connection
│   ├── products_dao.py        # Product database operations
│   ├── orders_dao.py          # Order database operations
│   └── uom_dao.py             # UOM database operations
│
├── schema.sql                 # Database and table creation
│              
│
├── ui/                        # Frontend files
│
└── README.md

````

---

## 🗄️ Database Design

The database schema is defined separately and created **before running the backend**.

### Tables
- `uom` – Unit of measurement
- `products` – Grocery products
- `orders` – Customer orders
- `order_details` – Products within each order

### Relationships
- `products.uom_id` → `uom.uom_id`
- `order_details.order_id` → `orders.order_id`
- `order_details.product_id` → `products.product_id`

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Zahbee/Grocery_web_app.git
cd grocery_webapp_main
````

---

### 2️⃣ Database Setup

1. Install **MySQL**
2. Open **MySQL Workbench**
3. Execute the SQL file:

   ```
   database/schema.sql
   ```
4. This will create the database and all required tables.

---

### 3️⃣ Configure Database Connection

Update database credentials in:

```
backend/sql_connection.py
```

Example:

```python
mysql.connector.connect(
    host="localhost",
    user="root",
    password="your_password",
    database="grocery_store"
)
```

---

### 4️⃣ Run the Backend Server

```bash
python backend/server.py
```

---

### 5️⃣ Run the Frontend

Open the UI files in a browser or serve them using a local server.

---

## 🧠 Design Decisions

* Database schema is managed separately from application runtime
* Backend code assumes the schema already exists
* DAO pattern is used to isolate database logic
* Parameterized SQL queries are used to prevent SQL injection
* Auto-generated primary keys are captured using `lastrowid`

---

## 🧪 Testing

DAO modules can be tested independently using the `__main__` block:

```bash
python backend/products_dao.py
```

---

## 📌 Future Improvements

* Add authentication and authorization
* Add update/edit functionality
* Use ORM or database migrations
* Deploy using Docker or cloud services

---

