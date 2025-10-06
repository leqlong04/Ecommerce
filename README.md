# 🛒 E-Commerce Full Stack Application

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.3-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-18.3.1-blue.svg)](https://reactjs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-12+-blue.svg)](https://www.postgresql.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A modern full-stack e-commerce application built with Spring Boot and React, featuring Stripe payment integration and comprehensive order management.

## ✨ Features

- 🛍️ **Product Management** - CRUD operations for products and categories
- 🛒 **Shopping Cart** - Add/remove items with real-time updates
- 💳 **Stripe Payment** - Secure online payment processing
- 🔐 **JWT Authentication** - Role-based access control (User/Admin/Seller)
- 📊 **Admin Dashboard** - Complete management interface
- 📦 **Order Management** - Track order status and history
- 🏠 **Address Management** - Multiple shipping addresses
- 📱 **Responsive Design** - Mobile-first approach

## 🛠️ Tech Stack

### Backend
- **Java 24** | **Spring Boot 3.5.3** | **Spring Security**
- **PostgreSQL** | **JPA/Hibernate** | **JWT**
- **Stripe API** | **Lombok** | **ModelMapper**

### Frontend
- **React 18** | **Vite** | **Redux Toolkit**
- **Tailwind CSS** | **Material-UI** | **Axios**
- **React Router** | **React Hook Form** | **Stripe React**

## 🚀 Quick Start

### Prerequisites
- Java 24+, Node.js 18+, PostgreSQL 12+, Maven 3.6+

### Installation

1. **Clone & Setup Database**
```bash
git clone <repository-url>
cd spring-boot-course-main
createdb ecommerce
```

2. **Configure Environment**
```properties
# sb-ecom/src/main/resources/application.properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce
spring.datasource.username=your_username
spring.datasource.password=your_password
stripe.secret.key=your_stripe_secret_key
```

```env
# ecom-frontend/.env
VITE_BACK_END_URL=http://localhost:8080
VITE_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
```

3. **Run Application**
```bash
# Backend
cd sb-ecom && mvn spring-boot:run

# Frontend (new terminal)
cd ecom-frontend && npm install && npm run dev
```

**Access:** Frontend: `http://localhost:5173` | Backend: `http://localhost:8080` | API Docs: `http://localhost:8080/swagger-ui.html`

## 📁 Project Structure

```
spring-boot-course-main/
├── ecom-frontend/          # React Frontend
│   ├── src/components/     # UI Components
│   ├── src/store/         # Redux State Management
│   └── src/api/           # API Configuration
├── sb-ecom/               # Spring Boot Backend
│   ├── src/main/java/com/ecommerce/project/
│   │   ├── controller/    # REST Controllers
│   │   ├── model/         # JPA Entities
│   │   ├── service/       # Business Logic
│   │   ├── repository/    # Data Access
│   │   └── security/      # JWT Security
│   └── pom.xml
└── README.md
```

## 🔧 Key APIs

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/signin` | User login |
| `POST` | `/api/auth/signup` | User registration |
| `GET` | `/api/products` | Get products (paginated) |
| `POST` | `/api/cart/add` | Add to cart |
| `POST` | `/api/orders/create` | Create order |
| `POST` | `/api/payment/create` | Process payment |

## 🚀 Deployment

### Docker
```dockerfile
# Backend
FROM openjdk:24-jdk-slim
COPY target/sb-ecom-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]

# Frontend
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install && npm run build
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
```

### Cloud Platforms
- **Backend:** AWS Elastic Beanstalk, Azure App Service, Google Cloud Run
- **Frontend:** Vercel, Netlify, AWS S3 + CloudFront

## 🧪 Testing

```bash
# Backend tests
cd sb-ecom && mvn test

# Frontend tests
cd ecom-frontend && npm test

# API testing
# Use included Postman collection
```

## 🔐 Security Features

- JWT-based authentication
- Role-based authorization (USER/ADMIN/SELLER)
- Password encryption
- CORS configuration
- Input validation
- SQL injection prevention

## 📊 Database Schema

Key entities: `users`, `products`, `categories`, `cart`, `orders`, `addresses`, `payments`

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 👥 Author

**Le Quang Long** - [GitHub](https://github.com/yourusername)

---

**⭐ Star this repo if you find it helpful!**