# E-Commerce Website — Online Bookstore

A web-based **E-Commerce Website** designed as an individual academic project following the **Software Development Life Cycle (SDLC)**.

The project focuses on developing a specialized online bookstore where users can browse, search, and purchase books through a simple and user-friendly interface.

---

## 📌 Project Overview

The proposed system is an online bookstore focused on **Books & Literature**, including fiction, non-fiction, and academic books.

The website will provide customers with a focused platform for discovering books by category, genre, author, and keywords. Users will be able to manage their shopping cart, place orders, and view their order history.

An administrative section will allow authorized administrators to manage book listings, categories, inventory, and customer orders.

This project is being developed as an **individual academic assignment** and will be implemented incrementally through multiple SDLC sprints.

---

## 🎯 Project Objectives

The main objectives of the project are to:

* Develop a functional online bookstore.
* Provide users with an easy way to browse and search for books.
* Organize books using categories and genres.
* Allow users to manage a shopping cart.
* Provide a simple checkout and order-processing workflow.
* Allow users to view their previous orders.
* Provide basic inventory and order management for administrators.
* Apply Software Development Life Cycle concepts throughout the project.
* Deploy and host the completed e-commerce website.

---

## 👥 Target Audience

The primary target audience is:

> **Casual and avid readers aged 18–40** looking for an easy way to browse, discover, and purchase new and second-hand books online.

The platform focuses specifically on books and literature instead of mixing books with unrelated products found on general marketplaces.

---

## 🛒 Planned MVP Features

The Minimum Viable Product (MVP) includes:

| Category       | Feature                            | Description                                                                 |
| -------------- | ---------------------------------- | --------------------------------------------------------------------------- |
| Authentication | User Registration & Authentication | Users can register, log in, and log out securely.                           |
| Catalog        | Product List & Search              | Users can browse and search books by category, genre, author, and keywords. |
| Cart           | Cart Management                    | Users can add books, update quantities, and remove items from their cart.   |
| Checkout       | Order Processing                   | Users can provide checkout information and place orders.                    |
| Admin          | Inventory Control                  | Administrators can manage book listings, categories, and stock.             |
| Account        | Order History                      | Users can view previous orders and their current order status.              |

---

## 💻 Technology Stack

### Frontend

* **HTML5**
* **CSS3**
* **Bootstrap**
* **JavaScript**

### Backend

* **Core PHP**

### Database

* **MySQL**

### Development Tools

* Visual Studio Code
* XAMPP
* Apache
* MySQL / MariaDB
* phpMyAdmin
* Git
* GitHub

---

## 🔧 Technology Selection

### HTML, CSS & Bootstrap

HTML and CSS will be used to structure and style the website. Bootstrap will help create responsive layouts that work across desktop and mobile devices.

### JavaScript

JavaScript will be used to provide client-side interactivity, validation, and dynamic behavior.

### Core PHP

Core PHP will handle server-side processing, authentication, sessions, product management, shopping cart operations, checkout, and order processing.

### MySQL

MySQL will be used as the relational database for storing users, categories, products, carts, orders, and order items.

---

## 🌐 Alternative Development Approach

**WordPress with WooCommerce** will also be explored as an alternative implementation approach.

If WordPress is suitable for the project requirements, permitted by the instructor, and practical for deployment, it may be considered for implementation.

However, the **primary implementation plan** is based on:

```text
HTML
CSS
Bootstrap
JavaScript
Core PHP
MySQL
```

If WordPress does not provide the required customization or does not align with the academic requirements, development will continue using the PHP/MySQL-based implementation.

---

## 🗄️ Database Design

The planned database contains the following main entities:

```text
USERS
   │
   ├── ORDERS
   │      │
   │      └── ORDER_ITEMS
   │               │
   │               └── PRODUCTS
   │
   └── CART
          │
          └── CART_ITEMS
                    │
                    └── PRODUCTS

CATEGORIES
      │
      └── PRODUCTS
```

### Main Entities

* **USERS** — Stores customer and administrator accounts.
* **CATEGORIES** — Stores book categories and genres.
* **PRODUCTS** — Stores book information, prices, stock, authors, and ISBN.
* **ORDERS** — Stores customer order information.
* **ORDER_ITEMS** — Stores individual books included in orders.
* **CART** — Stores a user's active shopping cart.
* **CART_ITEMS** — Stores books added to shopping carts.

The complete ERD is available in the Sprint 1 documentation.

---

## 📂 Repository Structure

The repository is organized as follows:

```text
E-commerce-2k23-CSM-102/
│
├── docs/
│   └── SPRINT_1.md
│
└── README.md
```

Additional application folders and files will be added in the upcoming sprints as development progresses.

---

## 📋 SDLC Sprint Progress

| Sprint   | Focus                           | Status      |
| -------- | ------------------------------- | ----------- |
| Sprint 1 | Architecture & Scope Definition | ✅ Completed |
| Sprint 2 | To be assigned                  | ⏳ Pending   |
| Sprint 3 | To be assigned                  | ⏳ Pending   |
| Sprint 4 | To be assigned                  | ⏳ Pending   |
| Sprint 5 | To be assigned                  | ⏳ Pending   |
| Sprint 6 | To be assigned                  | ⏳ Pending   |

> Sprint progress will be updated as new requirements are assigned and completed.

---

## 📖 Sprint 1 Documentation

The complete Sprint 1 architecture and planning document is available here:

```text
/docs/SPRINT_1.md
```

It contains:

* Target Audience & Market Focus
* User Persona
* Problem Definition
* MVP Feature Scope
* Technology Stack & Justification
* Entity-Relationship Diagram (ERD)
* Database Relationships
* Primary Keys and Foreign Keys
* Database Constraints

---

## 🚀 Future Development

Future sprints will progressively add the functionality required to transform the planned architecture into a complete e-commerce website.

Planned development areas include:

* Frontend implementation
* Database implementation
* User authentication
* Product and category management
* Shopping cart
* Checkout and order processing
* Administrative functionality
* Testing
* Deployment and hosting

Features will be implemented according to the requirements assigned for each sprint.

---

## 👤 Project Type

**Individual Academic Project**

**Project Domain:** E-Commerce / Online Bookstore

**Market Focus:** Books & Literature

**Backend:** Core PHP

**Database:** MySQL

**Frontend:** HTML, CSS, Bootstrap, JavaScript

**Alternative Platform:** WordPress + WooCommerce

---

## 📄 License

This project is developed for **academic and educational purposes** as part of an individual SDLC assignment.
