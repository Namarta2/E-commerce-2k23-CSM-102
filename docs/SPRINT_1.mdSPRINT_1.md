# Sprint 1: System Architecture & Scope Definition

## Section 1: Target Audience & Market Focus

* **Primary Persona:** Casual and avid readers aged 18–40 looking for an easy way to browse, discover, and buy new and second-hand books online, without wading through a generic marketplace's unrelated listings.

* **Core Pain Point:** General e-commerce platforms don't offer book-specific discovery by genre, author, or series and often mix books with unrelated products, making it difficult to browse a focused catalog and track orders for a specific title or series.

* **Domain Scope:** Books & Literature — a focused e-commerce vertical covering fiction, non-fiction, and academic titles organized by genre, author, and category.

### User Needs

The target users need a simple and user-friendly platform where they can:

* Browse books by category or genre.
* Search for books using keywords.
* View book details, price, availability, and other relevant information.
* Add books to a shopping cart.
* Update or remove cart items.
* Place orders through a simple checkout process.
* View their previous orders and current order status.

The platform will focus on providing a specialized online bookstore experience rather than a general marketplace containing unrelated product categories.

---

## Section 2: MVP Feature Scope

The Minimum Viable Product (MVP) will focus on the core functionality required to operate a basic online bookstore.

| Category       | Feature                            | Description                                                                                                                              | Priority   |
| -------------- | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| Authentication | User Registration & Authentication | Users can register, log in, and log out. Passwords will be securely hashed and PHP sessions will be used for authentication.             | High (MVP) |
| Catalog        | Product List & Search              | Users can browse books and search or filter them by genre, author, category, and keywords.                                               | High (MVP) |
| Cart           | Cart Management                    | Users can add books to a persistent MySQL-backed shopping cart, update quantities, and remove items.                                     | High (MVP) |
| Checkout       | Order Processing                   | Users can provide checkout information and place orders. The system will create the corresponding order and order-item records in MySQL. | High (MVP) |
| Admin          | Inventory Control                  | Administrators can perform CRUD operations for book listings, categories, and stock quantities.                                          | Medium     |
| Account        | Order History                      | Authenticated users can view their previous orders and current order status.                                                             | Medium     |

### MVP Scope Boundaries

The initial MVP will focus on the essential online bookstore workflow:

1. User registration and authentication.
2. Book browsing and searching.
3. Book category and genre filtering.
4. Book detail viewing.
5. Shopping cart management.
6. Checkout and order placement.
7. Basic inventory management.
8. Order history and order status.

The following features are outside the initial MVP scope:

* Real payment gateway integration.
* Advanced recommendation systems.
* Real-time delivery tracking.
* Multi-vendor marketplace functionality.
* AI-based search or recommendations.
* Mobile application development.
* Advanced analytics and reporting.

These features may be considered in future development if time and project requirements permit.

---

## Section 3: Tech Stack Selection & Justification

### Frontend: HTML, CSS, Bootstrap, JavaScript

**Justification:** HTML and CSS will provide the basic structure and styling of the website. Bootstrap will be used to create responsive layouts and reusable interface components. JavaScript will provide client-side interactivity such as form validation, search interactions, cart quantity controls, and other dynamic behavior.

This frontend stack keeps the project lightweight and directly compatible with server-rendered PHP pages without requiring the additional build-tooling complexity of a large JavaScript framework.

### Backend Infrastructure: Core PHP

**Justification:** Core PHP will handle server-side processing, user authentication, sessions, product and category management, shopping cart operations, checkout, and order processing.

PHP integrates well with MySQL and is suitable for server-rendered web applications. It also allows the project to implement the required backend functionality without requiring a separate API layer.

### Database Management System: MySQL

**Justification:** MySQL will store users, products, categories, orders, order items, carts, and cart items.

The e-commerce domain contains structured relational data with clear relationships and referential integrity requirements. For example, every order item must reference a valid order and product. MySQL is therefore suitable for maintaining these relationships through primary keys and foreign keys.

MySQL also integrates naturally with PHP using database extensions such as MySQLi or PDO.

### Alternative Platform Option: WordPress with WooCommerce

**Justification:** WordPress with WooCommerce will be explored as an alternative implementation approach. WooCommerce provides built-in e-commerce functionality such as product management, shopping carts, checkout, and order management.

If WordPress is suitable for the project requirements, permitted by the instructor, and practical for the deployment environment, it may be considered for implementation.

However, the **primary implementation plan** is to develop the system using:

* HTML
* CSS
* Bootstrap
* JavaScript
* Core PHP
* MySQL

If WordPress does not provide the required level of customization or does not align with the academic requirements, development will continue using the primary PHP/MySQL-based approach.

### Caching & Asynchronous Processing (Optional)

Caching and asynchronous processing are not required for the initial MVP. They can be considered in a later sprint if the catalog size, traffic, or performance requirements increase.

The initial system will prioritize a simple and maintainable architecture suitable for an individual academic project.

---

## Section 4: Entity-Relationship Diagram (ERD)

The database design contains the following core entities:

* **USERS**
* **CATEGORIES**
* **PRODUCTS**
* **ORDERS**
* **ORDER_ITEMS**
* **CART**
* **CART_ITEMS**

The ERD represents the relationships between customers, books, categories, shopping carts, and orders.

### Mermaid ERD

```mermaid
erDiagram

    USERS ||--o{ ORDERS : places
    USERS ||--o| CART : owns
    CATEGORIES ||--o{ PRODUCTS : contains
    ORDERS ||--|{ ORDER_ITEMS : contains
    PRODUCTS ||--o{ ORDER_ITEMS : included_in
    CART ||--o{ CART_ITEMS : contains
    PRODUCTS ||--o{ CART_ITEMS : added_to

    USERS {
        INT user_id PK
        VARCHAR name
        VARCHAR email UK
        VARCHAR password
        VARCHAR phone
        VARCHAR address
        ENUM role
        DATETIME created_at
    }

    CATEGORIES {
        INT category_id PK
        VARCHAR name UK
        TEXT description
    }

    PRODUCTS {
        INT product_id PK
        INT category_id FK
        VARCHAR name
        TEXT description
        DECIMAL price
        INT stock_quantity
        VARCHAR author
        VARCHAR isbn UK
        VARCHAR image
        DATETIME created_at
    }

    ORDERS {
        INT order_id PK
        INT user_id FK
        DECIMAL total_amount
        ENUM order_status
        VARCHAR shipping_address
        DATETIME order_date
    }

    ORDER_ITEMS {
        INT order_item_id PK
        INT order_id FK
        INT product_id FK
        INT quantity
        DECIMAL unit_price
    }

    CART {
        INT cart_id PK
        INT user_id FK UK
        DATETIME created_at
    }

    CART_ITEMS {
        INT cart_item_id PK
        INT cart_id FK
        INT product_id FK
        INT quantity
    }
```

---

## Relationship & Cardinality Notes

* **USERS (1) — (N) ORDERS:** One user can place zero or many orders; each order belongs to exactly one user.

* **USERS (1) — (0..1) CART:** Each user can have at most one active shopping cart.

* **ORDERS (1) — (N) ORDER_ITEMS:** Each order contains one or more order items; each order item belongs to exactly one order.

* **PRODUCTS (1) — (N) ORDER_ITEMS:** A book can appear in many order items across different orders; each order item references exactly one book.

* **CATEGORIES (1) — (N) PRODUCTS:** A category can contain many books; each book belongs to exactly one primary category.

* **CART (1) — (N) CART_ITEMS:** A cart can contain multiple cart items; each cart item belongs to exactly one cart.

* **PRODUCTS (1) — (N) CART_ITEMS:** A book can appear in many cart items across different users' carts.

### N:M Relationships

The relationships between **Orders and Products** and between **Carts and Products** are many-to-many relationships.

These relationships are resolved using the associative entities:

* `ORDER_ITEMS` for Orders ↔ Products.
* `CART_ITEMS` for Carts ↔ Products.

These associative entities contain their own primary keys and foreign keys to both related entities. They also store transactional attributes such as `quantity` and `unit_price`.

---

## PHP/MySQL Implementation Notes

The following database design rules will be followed during implementation:

* Primary keys will use `INT AUTO_INCREMENT`.
* Foreign keys will reference the appropriate parent table.
* Foreign-key actions such as `ON DELETE CASCADE` or `ON DELETE RESTRICT` will be selected according to the relationship and data-integrity requirements.
* `PRODUCTS.isbn` will use a `UNIQUE` constraint where an ISBN is available.
* User email addresses will use a `UNIQUE` constraint.
* `CART.user_id` will use a `UNIQUE` constraint to support one active cart per user.
* The combination of `cart_id` and `product_id` in `CART_ITEMS` should be unique so that the same product does not appear as duplicate rows within the same cart.
* `DECIMAL` will be used for monetary values such as product prices and order totals.
* Passwords will be stored using secure password hashing rather than plain text.
* Foreign keys will be used to maintain referential integrity between related records.

---

## Conclusion

Sprint 1 establishes the initial architecture and scope for the proposed online bookstore. The project will focus on providing a specialized platform for browsing and purchasing books while keeping the MVP feasible for an individual academic project.

The primary technology stack will consist of **HTML, CSS, Bootstrap, JavaScript, Core PHP, and MySQL**. WordPress with WooCommerce will also be explored as an alternative if it is suitable and permitted by the project requirements.

The defined MVP features and ERD provide the foundation for the remaining SDLC sprints, including system implementation, testing, deployment, and hosting.
