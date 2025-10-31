# Cosmetics Store Application

A comprehensive Spring Boot web application for a cosmetics store with CRUD operations, authentication, and REST API.

## Features

### Grade 3 Requirements ✓
- **CRUD Operations**: Full Create, Read, Update, Delete functionality for all entities
- **8+ Related Tables**: 
  - Users, Roles, Categories, Brands, Products, Orders, OrderItems, Reviews, Cart
  - Complex relationships with foreign keys
- **Data Validation**: Server-side validation using Bean Validation annotations

### Grade 4 Requirements ✓
- **Authentication & Registration**: Secure login and registration system
- **3 Roles with Different Access**:
  - **USER**: Browse and purchase products
  - **MANAGER**: Manage products and orders
  - **ADMIN**: Full system access including user management
- **Role-Based Navigation**: Users only see links relevant to their role in the header

### Grade 5 Requirements ✓
- **REST API**: RESTful endpoints for database operations
- **API Endpoints**:
  - `/api/auth/register` - User registration
  - `/api/products` - Product CRUD operations
  - `/api/orders` - Order management

## Technology Stack

- **Spring Boot 3.2.0**
- **Spring Security** for authentication
- **Spring Data JPA** for database operations
- **PostgreSQL** database
- **Thymeleaf** for templating
- **Maven** for dependency management
- **Docker** for containerization

## Database Schema

### Tables (9 total)
1. **roles** - User role definitions (ADMIN, MANAGER, USER)
2. **users** - User accounts with encrypted passwords
3. **user_roles** - Many-to-many relationship
4. **categories** - Product categories
5. **brands** - Brand information
6. **products** - Product details with relationships
7. **product_brands** - Many-to-many relationship
8. **orders** - Customer orders
9. **order_items** - Order line items
10. **reviews** - Product reviews and ratings
11. **cart** - Shopping cart items

## Setup Instructions

### Prerequisites
- Java 17+
- Maven
- Docker and Docker Compose

### Running with Docker (Recommended)

1. **Navigate to the project directory:**
```bash
cd LastPractice
```

2. **Build the application:**
```bash
mvn clean package
```

3. **Start using Docker Compose:**
```bash
docker-compose up -d
```

4. **Access the application:**
- Application: http://localhost:8080
- PostgreSQL: localhost:5432

### Running without Docker

1. **Start PostgreSQL:**
```bash
docker run -d --name cosmetics-postgres \
  -e POSTGRES_DB=cosmetics_db \
  -e POSTGRES_USER=cosmetics_user \
  -e POSTGRES_PASSWORD=cosmetics_password \
  -p 5432:5432 postgres:15-alpine
```

2. **Run the application:**
```bash
mvn spring-boot:run
```

## Default Users

The application initializes with these default accounts:

| Username | Password | Role   |
|----------|----------|--------|
| admin    | admin123 | ADMIN  |
| manager  | manager123 | MANAGER |
| user     | user123  | USER   |

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user

### Products
- `GET /api/products` - Get all products
- `GET /api/products/{id}` - Get product by ID
- `POST /api/products` - Create product
- `PUT /api/products/{id}` - Update product
- `DELETE /api/products/{id}` - Delete product

### Orders
- `GET /api/orders` - Get all orders
- `GET /api/orders/{id}` - Get order by ID
- `POST /api/orders` - Create order
- `PUT /api/orders/{id}/status` - Update order status
- `DELETE /api/orders/{id}` - Delete order

## Role-Based Access

### USER Role
- Access: `/user/dashboard`
- Can browse products and view orders
- Cannot manage products or users

### MANAGER Role
- Access: `/manager/dashboard`, `/manager/products`, `/manager/orders`
- Can manage products and orders
- Cannot manage users or system settings

### ADMIN Role
- Access: `/admin/dashboard`, `/admin/users`, `/admin/products`, `/admin/orders`
- Full access to all functionality
- Can manage users and system settings

## Project Structure

```
LastPractice/
├── src/
│   ├── main/
│   │   ├── java/com/example/cosmetics/
│   │   │   ├── config/           # Security and data initialization
│   │   │   ├── controller/       # Web and REST controllers
│   │   │   ├── dto/              # Data Transfer Objects
│   │   │   ├── model/            # Entity models
│   │   │   ├── repository/      # JPA repositories
│   │   │   └── service/          # Business logic
│   │   └── resources/
│   │       ├── templates/        # Thymeleaf templates
│   │       ├── static/           # CSS and static files
│   │       └── application.properties
├── pom.xml
├── docker-compose.yml
├── Dockerfile
└── README.md
```

## Validation Rules

- **Username**: Minimum 3 characters, unique
- **Email**: Valid email format, unique
- **Password**: Minimum 6 characters
- **Product Price**: Must be greater than 0
- **Stock Quantity**: Must be 0 or positive
- **Review Rating**: Between 1 and 5

## Features Implementation

- ✓ Database relationships (One-to-Many, Many-to-Many)
- ✓ Data validation with Bean Validation
- ✓ Role-based access control
- ✓ Password encryption (BCrypt)
- ✓ REST API for database operations
- ✓ Role-based UI navigation
- ✓ Docker containerization
- ✓ Initial data seeding

## Development

### Building
```bash
mvn clean install
```

### Running Tests
```bash
mvn test
```

## License

This project is created for educational purposes.

# UPFour
# Upshka
