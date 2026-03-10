# 📚 BookStore — Full Stack Ecommerce Platform

A full stack Books & Media ecommerce application built with **Spring Boot** and **Angular**. Features include product browsing, search, shopping cart, user authentication and order management.

![Java](https://img.shields.io/badge/Java-21-orange?style=flat-square&logo=openjdk)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.2-green?style=flat-square&logo=springboot)
![Angular](https://img.shields.io/badge/Angular-17-red?style=flat-square&logo=angular)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-3-blue?style=flat-square&logo=tailwindcss)

---

## 🖥️ Features

- **Browse & Search** — search books by title, author or category with live filtering
- **User Auth** — register and login with JWT-based authentication
- **Shopping Cart** — add, update and remove items with live cart count
- **Checkout** — shipping form with mock Stripe payment simulation
- **Order History** — view all past orders with expandable item details
- **H2 Console** — in-browser database inspector for development

---

## 🏗️ Tech Stack

### Backend
| Technology | Purpose |
|---|---|
| Java 21 | Language |
| Spring Boot 3.2 | Application framework |
| Spring Security + JWT | Authentication & authorisation |
| Spring Data JPA + Hibernate | Database ORM |
| H2 (in-memory) | Development database |
| Lombok | Boilerplate reduction |
| Maven | Build tool |

### Frontend
| Technology | Purpose |
|---|---|
| Angular 17 | Frontend framework |
| Tailwind CSS | Styling |
| RxJS | Reactive programming |
| Angular Router | Client-side routing |

---

## 🚀 Getting Started

### Prerequisites

- Java 21
- Node.js 20+ and npm
- Angular CLI (`npm install -g @angular/cli`)

---

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/bookstore-platform.git
cd bookstore-platform
```

---

### 2. Run the backend

Open the `backend` folder in IntelliJ IDEA (or any IDE).

Run the main class:
```
src/main/java/com/bookstore/bookstoreapi/BookstoreApiApplication.java
```

Or via Maven:
```bash
cd backend
./mvnw spring-boot:run
```

The API will start on **http://localhost:8080**

> 💡 Visit **http://localhost:8080/h2-console** to inspect the database.
> Use JDBC URL: `jdbc:h2:mem:bookstoredb`, username: `sa`, no password.

---

### 3. Run the frontend

```bash
cd frontend
npm install
ng serve
```

The app will open at **http://localhost:4200**

---

## 📡 API Endpoints

### Auth
| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | `/api/auth/register` | Register new user | Public |
| POST | `/api/auth/login` | Login and receive JWT | Public |

### Products
| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/api/products` | Get all products | Public |
| GET | `/api/products/{id}` | Get product by ID | Public |
| GET | `/api/products/search?keyword=` | Search products | Public |
| GET | `/api/products/category/{cat}` | Filter by category | Public |
| GET | `/api/products/categories` | List all categories | Public |

### Cart
| Method | Endpoint | Description | Auth |
|---|---|---|---|
| GET | `/api/cart` | Get current user's cart | 🔒 Required |
| POST | `/api/cart` | Add item to cart | 🔒 Required |
| PUT | `/api/cart/{id}?quantity=` | Update item quantity | 🔒 Required |
| DELETE | `/api/cart/{id}` | Remove item from cart | 🔒 Required |

### Orders
| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | `/api/orders/checkout` | Place an order | 🔒 Required |
| GET | `/api/orders` | Get user's order history | 🔒 Required |
| GET | `/api/orders/{id}` | Get order by ID | 🔒 Required |

---

## 🗂️ Project Structure

```
bookstore-platform/
├── backend/
│   └── src/main/java/com/bookstore/bookstoreapi/
│       ├── config/          # Security config & data seeder
│       ├── controller/      # REST controllers
│       ├── dto/             # Request/response objects
│       ├── entity/          # JPA entities (DB tables)
│       ├── repository/      # Spring Data JPA repositories
│       ├── security/        # JWT filter & utilities
│       └── service/         # Business logic
└── frontend/
    └── src/app/
        ├── components/      # UI components (pages)
        ├── guards/          # Route protection
        ├── interceptors/    # JWT attachment
        ├── models/          # TypeScript interfaces
        └── services/        # HTTP API calls
```

---

## 📸 Pages

| Page | Route | Description |
|---|---|---|
| Home / Browse | `/` | Product grid with search and category filter |
| Product Detail | `/products/:id` | Full product info with add-to-cart |
| Login | `/login` | JWT authentication |
| Register | `/register` | New user registration |
| Cart | `/cart` | View and manage cart items |
| Checkout | `/checkout` | Shipping form and mock payment |
| Orders | `/orders` | Order history |

---

## 🔐 Security Notes

- Passwords are hashed with **BCrypt** — never stored in plain text
- JWT tokens expire after **24 hours**
- All cart and order endpoints verify the token and scope data to the authenticated user
- CORS is configured to only allow requests from `http://localhost:4200`

---

## 🛠️ Development Notes

- The H2 database resets on every restart (`ddl-auto=create-drop`) — this is intentional for development
- The `DataSeeder` automatically loads sample books on first startup
- Payment is **simulated** — no real Stripe integration

---

## 📄 Licence

MIT
