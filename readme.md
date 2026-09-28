# 🛒 Flask E-Commerce Application

<p align="center">
  <img src="flask.png" alt="Flask E-Commerce Banner" width="600">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Flask-2.x-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask">
  <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite">
  <img src="https://img.shields.io/badge/Bootstrap-5.2-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white" alt="Bootstrap">
  <img src="https://img.shields.io/badge/Font_Awesome-6.0-339AF0?style=for-the-badge&logo=fontawesome&logoColor=white" alt="Font Awesome">
</p>

---

## Project Overview

This repository contains a full-stack **E-Commerce Web Application** built using **Flask** (Python) and **SQLite**. The application delivers a streamlined online shopping experience featuring user authentication, interactive product catalogs, item detail views, shopping cart management, structured checkout processes, and personal user profile management with order history.

---

## Tech Stack

### **Backend Framework & Core**
- **Python 3**: Core application logic.
- **Flask**: Micro web framework handling routing, request processing, and view rendering.
- **Flask-Session**: Server-side filesystem session management.
- **Werkzeug Security**: Password hashing (`generate_password_hash`, `check_password_hash`) and secure password verification.
- **CS50 SQL**: Simplified SQLite execution interface.

### **Database**
- **SQLite 3 (`shop.db`)**: Lightweight relational database storing users, products, cart items, and placed orders.

### **Frontend**
- **HTML5 & CSS3**: Custom styles (`styles.css`) for layout, dynamic buttons, and user interface elements.
- **Jinja2**: Dynamic server-side templating engine for rendering content and pages.
- **Bootstrap 5.2**: Responsive component styling and grid system.
- **Font Awesome 6.0**: Visual icons for navigation, cart UI, and layout enhancements.

### **Libraries & Dependencies**
- `requests`: HTTP client library.
- `pytz` & `datetime`: Timezone and timestamp formatting.
- `urllib` & `uuid`: Utilities for standard parameter encoding and unique identification.

---

## Key Features

- **User Authentication**: Secure registration, login session persistence, logout, and account deletion functionality.
- **Product Catalog**: Interactive homepage displaying available store products with prices and cover images.
- **Detailed Product Views**: Dedicated pages for each product detailing availability, pricing, and quantity selection.
- **Shopping Cart Management**: Add products to cart, specify quantities, and view real-time price calculations.
- **Checkout & Order Processing**: Collect shipping address details (city, street address, postal code, phone number) with strict form validation and order records creation.
- **User Profile & Order History**: View account information, shipping addresses, past order history, and active cart total balance.
- **Custom Apology & Error Handling**: User-friendly error templates (`apology.html`) with meme-style error messaging.

---

## Project Structure

```text
E-commerce/
├── app.py                  # Main Flask application file containing all routes and backend logic
├── helpers.py              # Auxiliary functions (login decorator, apology handler, USD currency formatter)
├── shop.db                 # SQLite database storing users, products, cart, and orders data
├── requirements.txt        # Python dependency manifest
├── flask.png               # E-Commerce banner image
├── templates/              # Jinja2 HTML Templates
│   ├── layout.html         # Base HTML template with navbar and layout elements
│   ├── index.html          # Product catalog homepage
│   ├── login.html          # User login form template
│   ├── register.html       # User registration form template
│   ├── productdetails.html # Product details view template
│   ├── cart.html           # User shopping cart template
│   ├── checkout.html       # Checkout & shipping details form
│   ├── profile.html        # User profile & order history dashboard
│   ├── payment.html        # Payment processing interface template
│   ├── apology.html        # Error rendering template
│   └── remove.html         # User account deletion template
└── README.md               # Project documentation
```

---

## Database Schema (`shop.db`)

The SQLite database consists of four core tables:

1. **`users`**:
   - `id`: Primary Key
   - `username`: Unique username
   - `hash`: Hashed password string

2. **`products`**:
   - `id`: Primary Key
   - `name`: Product name
   - `price`: Product price
   - `availability`: Stock count / status
   - `cover`: Image path/URL

3. **`cart`**:
   - `user_id`: Foreign Key referencing `users(id)`
   - `product_id`: Foreign Key referencing `products(id)`
   - `quantity`: Number of items added

4. **`orders`**:
   - `id`: Primary Key
   - `user_id`: Foreign Key referencing `users(id)`
   - `product_id`: Foreign Key referencing `products(id)`
   - `address`, `city`, `postal_code`, `phone_number`: Shipping details
   - `history`: Order timestamp / record details

---

##API Routes & Endpoints

| Route | Method | Access Level | Description |
|---|---|---|---|
| `/` | `GET` | Public | Displays product catalog homepage |
| `/register` | `GET`, `POST` | Public | Handles user account registration |
| `/login` | `GET`, `POST` | Public | Authenticates user and initializes session |
| `/logout` | `GET`, `POST` | Logged In | Clears session and logs user out |
| `/remove` | `GET`, `POST` | Logged In | Deletes user account and associated cart data |
| `/productdetails/<id>` | `GET`, `POST` | Public | Displays details for product by ID |
| `/addtocart/<id>` | `POST` | Logged In | Adds requested product quantity to user cart |
| `/cart` | `GET` | Logged In | Displays user's active shopping cart items |
| `/checkout` | `GET`, `POST` | Logged In | Submits delivery info & confirms order |
| `/profile` | `GET`, `POST` | Logged In | Displays user profile and order history |

---

## Getting Started

### **Prerequisites**
- **Python 3.8+** installed on your machine.
- `pip` (Python package manager).

### **1. Installation**

Clone or download the project folder, then navigate to the workspace directory:

```bash
cd E-commerce
```

### **2. Install Dependencies**

Install required Python packages listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

*Note: If `cs50` library is not included in your standard packages, install it via:*
```bash
pip install cs50
```

### **3. Running the Application**

Start the Flask development server:

```bash
python app.py
```
*(Or alternatively set `FLASK_APP=app.py` and run `flask run`)*

### **4. Accessing the Web Application**

Open your web browser and navigate to:
```text
http://127.0.0.1:5000/
```

---

## Author & Acknowledgments

- **Developed by**: [tarenjk24](https://github.com/tarenjk24)
- Built with Flask, SQLite, Bootstrap, and Jinja2.