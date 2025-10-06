# E-Commerce Full Stack Application

Một ứng dụng thương mại điện tử full-stack được xây dựng với Spring Boot (Backend) và React (Frontend), tích hợp thanh toán Stripe và quản lý đơn hàng toàn diện.

## 🚀 Tổng quan

Đây là một hệ thống e-commerce hoàn chỉnh với các tính năng:
- Quản lý sản phẩm và danh mục
- Giỏ hàng và thanh toán
- Hệ thống xác thực và phân quyền
- Dashboard quản trị
- Tích hợp thanh toán Stripe
- Quản lý đơn hàng và địa chỉ giao hàng

## 🛠️ Tech Stack

### Backend
- **Java 24**
- **Spring Boot 3.5.3**
- **Spring Security** - Xác thực và phân quyền
- **Spring Data JPA** - ORM
- **PostgreSQL** - Cơ sở dữ liệu chính
- **JWT** - Token-based authentication
- **Stripe API** - Thanh toán trực tuyến
- **Lombok** - Giảm boilerplate code
- **ModelMapper** - Object mapping
- **SpringDoc OpenAPI** - API documentation

### Frontend
- **React 18.3.1**
- **Vite** - Build tool
- **Redux Toolkit** - State management
- **React Router DOM** - Routing
- **Tailwind CSS** - Styling
- **Material-UI (MUI)** - UI components
- **Axios** - HTTP client
- **React Hook Form** - Form handling
- **Stripe React** - Payment integration
- **React Hot Toast** - Notifications

## 📁 Cấu trúc Project

```
spring-boot-course-main/
├── ecom-frontend/          # React Frontend
│   ├── src/
│   │   ├── components/     # React components
│   │   │   ├── admin/      # Admin dashboard components
│   │   │   ├── auth/       # Authentication components
│   │   │   ├── cart/       # Shopping cart components
│   │   │   ├── checkout/   # Checkout flow components
│   │   │   ├── home/       # Home page components
│   │   │   ├── products/   # Product listing components
│   │   │   └── shared/     # Shared UI components
│   │   ├── store/          # Redux store và reducers
│   │   ├── api/            # API configuration
│   │   └── utils/          # Utility functions
│   └── package.json
├── sb-ecom/                # Spring Boot Backend
│   ├── src/main/java/com/ecommerce/project/
│   │   ├── controller/     # REST Controllers
│   │   ├── model/          # JPA Entities
│   │   ├── service/        # Business logic
│   │   ├── repository/     # Data access layer
│   │   ├── security/       # Security configuration
│   │   └── payload/        # DTOs
│   └── pom.xml
└── README.md
```

## 🚀 Cài đặt và Chạy Project

### Yêu cầu hệ thống
- Java 24+
- Node.js 18+
- PostgreSQL 12+
- Maven 3.6+

### Backend Setup

1. **Clone repository**
```bash
git clone <repository-url>
cd spring-boot-course-main
```

2. **Cấu hình Database**
```sql
-- Tạo database PostgreSQL
CREATE DATABASE ecommerce;
```

3. **Cấu hình application.properties**
```properties
# Cập nhật thông tin database trong sb-ecom/src/main/resources/application.properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce
spring.datasource.username=your_username
spring.datasource.password=your_password
```

4. **Cấu hình Stripe**
```properties
# Thêm Stripe secret key
stripe.secret.key=your_stripe_secret_key
```

5. **Chạy Backend**
```bash
cd sb-ecom
mvn spring-boot:run
```

Backend sẽ chạy tại: `http://localhost:8080`

### Frontend Setup

1. **Cài đặt dependencies**
```bash
cd ecom-frontend
npm install
```

2. **Cấu hình environment**
Tạo file `.env` trong thư mục `ecom-frontend`:
```env
VITE_BACK_END_URL=http://localhost:8080
VITE_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
```

3. **Chạy Frontend**
```bash
npm run dev
```

Frontend sẽ chạy tại: `http://localhost:5173`

## 🔧 Cấu hình Database

### Các bảng chính:
- **users** - Thông tin người dùng
- **roles** - Vai trò người dùng (USER, ADMIN, SELLER)
- **products** - Sản phẩm
- **categories** - Danh mục sản phẩm
- **cart** - Giỏ hàng
- **cart_items** - Chi tiết giỏ hàng
- **orders** - Đơn hàng
- **order_items** - Chi tiết đơn hàng
- **addresses** - Địa chỉ giao hàng
- **payments** - Thông tin thanh toán

## 📋 Tính năng chính

### 👤 Người dùng
- Đăng ký/Đăng nhập
- Duyệt sản phẩm theo danh mục
- Tìm kiếm và lọc sản phẩm
- Thêm sản phẩm vào giỏ hàng
- Thanh toán với Stripe
- Quản lý địa chỉ giao hàng
- Xem lịch sử đơn hàng

### 🛒 Giỏ hàng
- Thêm/Xóa sản phẩm
- Cập nhật số lượng
- Tính toán tổng tiền
- Lưu trữ local storage

### 💳 Thanh toán
- Tích hợp Stripe
- Hỗ trợ nhiều phương thức thanh toán
- Xác nhận thanh toán
- Lưu trữ thông tin giao dịch

### 👨‍💼 Admin Dashboard
- Quản lý sản phẩm (CRUD)
- Quản lý danh mục
- Quản lý người bán
- Quản lý đơn hàng
- Thống kê doanh thu
- Quản lý người dùng

### 🏪 Người bán
- Thêm sản phẩm mới
- Quản lý sản phẩm của mình
- Xem đơn hàng
- Cập nhật trạng thái đơn hàng

## 🔐 Bảo mật

- JWT Authentication
- Role-based Authorization
- Password encryption
- CORS configuration
- Input validation
- SQL injection prevention

## 📚 API Documentation

API documentation có sẵn tại: `http://localhost:8080/swagger-ui.html`

### Các endpoint chính:
- `POST /api/auth/signin` - Đăng nhập
- `POST /api/auth/signup` - Đăng ký
- `GET /api/products` - Lấy danh sách sản phẩm
- `POST /api/cart/add` - Thêm vào giỏ hàng
- `POST /api/orders/create` - Tạo đơn hàng
- `POST /api/payment/create` - Tạo thanh toán

## 🚀 Deployment

### Backend (Spring Boot)
```bash
cd sb-ecom
mvn clean package
java -jar target/sb-ecom-0.0.1-SNAPSHOT.jar
```

### Frontend (React)
```bash
cd ecom-frontend
npm run build
# Deploy thư mục dist/ lên hosting
```

## 🤝 Đóng góp

1. Fork project
2. Tạo feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Mở Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 👥 Tác giả

- **Le Quang Long** - *Initial work* - [GitHub](https://github.com/yourusername)

## 🙏 Acknowledgments

- Spring Boot team
- React team
- Stripe team
- Material-UI team
- Tất cả các thư viện open source được sử dụng

---

**Lưu ý**: Đây là project học tập, vui lòng cấu hình đúng thông tin database và Stripe keys trước khi chạy.
