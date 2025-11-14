# 🍳 Cooking Social Network

Mạng xã hội nấu ăn - Nền tảng chia sẻ công thức nấu ăn, tương tác với cộng đồng và kết nối những người yêu thích ẩm thực.

## 📋 Mục lục

- [Giới thiệu](#giới-thiệu)
- [Tính năng](#tính-năng)
- [Công nghệ sử dụng](#công-nghệ-sử-dụng)
- [Cấu trúc dự án](#cấu-trúc-dự-án)
- [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)
- [Cài đặt](#cài-đặt)
- [Cấu hình](#cấu-hình)
- [Chạy dự án](#chạy-dự-án)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Đóng góp](#đóng-góp)
- [License](#license)

## 🎯 Giới thiệu

Cooking Social Network là một nền tảng mạng xã hội dành cho những người yêu thích nấu ăn. Người dùng có thể:
- Chia sẻ công thức nấu ăn chi tiết với hình ảnh và video
- Tương tác với bài viết (like, comment, share)
- Lưu công thức và bài viết yêu thích
- Tìm kiếm công thức theo nhiều tiêu chí (loại món, nguyên liệu, độ khó, thời gian nấu...)
- Nhắn tin real-time với người dùng khác
- Nhận thông báo về các hoạt động liên quan

## ✨ Tính năng

### 🔐 Xác thực và Bảo mật
- Đăng ký/Đăng nhập với JWT
- Xác thực email qua OTP
- Đặt lại mật khẩu
- Quản lý session và refresh token
- Bảo mật mật khẩu với bcrypt

### 📝 Quản lý Công thức (Recipes)
- Tạo và chỉnh sửa công thức nấu ăn
- Thêm nguyên liệu, bước nấu, hình ảnh
- Phân loại theo:
  - Loại bữa ăn (Breakfast, Lunch, Dinner, Snack, Dessert)
  - Ẩm thực (Vietnamese, Japanese, Korean, Chinese, Thai, Indian, European, American, Mexican)
  - Dịp đặc biệt (Party, Birthday, Holiday, Vegetarian Day, Weather Based Food)
  - Chế độ ăn (Vegetarian, Vegan, Keto, Gluten Free, Weight Loss...)
  - Nguyên liệu chính (Chicken, Beef, Pork, Seafood, Egg, Vegetables, Tofu)
  - Phương pháp nấu (Fry, Grill, Steam, Stir Fry, Boil, Simmer, Soup)
  - Thời gian nấu (Under 15 min, 15-30 min, Over 1 hour)
  - Độ khó (Easy, Medium, Hard)
- Đánh giá và bình luận công thức
- Lưu công thức yêu thích

### 📱 Bài viết (Posts)
- Tạo bài viết chia sẻ công thức
- Upload hình ảnh và video
- Tương tác: Like, Comment, Share
- Bình luận đa cấp (reply to comments)
- Lưu bài viết

### 💬 Tin nhắn (Messages)
- Nhắn tin real-time với Socket.io
- Tin nhắn nhóm và tin nhắn cá nhân
- Gửi tin nhắn văn bản, hình ảnh, video
- Chia sẻ công thức và bài viết trong tin nhắn
- Phản ứng với tin nhắn (emoji reactions)
- Đánh dấu đã xem (seen status)
- Trả lời tin nhắn (reply to messages)

### 🔔 Thông báo (Notifications)
- Thông báo real-time về:
  - Like, comment, share bài viết
  - Follow/Unfollow
  - Tin nhắn mới
  - Các hoạt động khác

### 👥 Người dùng (Users)
- Hồ sơ người dùng với avatar, bio
- Follow/Unfollow người dùng khác
- Xem công thức và bài viết của người dùng
- Quản lý thông tin cá nhân

### 🥘 Nguyên liệu (Ingredients)
- Quản lý database nguyên liệu
- Thông tin dinh dưỡng (calories, protein, fat, carbs)
- Tìm kiếm nguyên liệu

## 🛠 Công nghệ sử dụng

### Backend
- **Framework**: NestJS (Node.js)
- **Language**: TypeScript
- **Database**: MySQL với Prisma ORM
- **Authentication**: JWT (Passport.js)
- **Real-time**: Socket.io
- **File Upload**: Cloudinary, Multer
- **Email**: Nodemailer với Handlebars templates
- **Validation**: class-validator, class-transformer

### Frontend
- **Framework**: React 19
- **Language**: TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **Routing**: React Router DOM
- **HTTP Client**: Axios
- **Real-time**: Socket.io Client
- **UI Components**: 
  - Radix UI
  - Heroicons
  - Lucide React
  - Emoji Picker React
- **Carousel**: Embla Carousel
- **Notifications**: React Toastify
- **Date Handling**: date-fns

## 📁 Cấu trúc dự án

```
hcm_9-naitei-nodejs-cooking_social_network/
├── backend/                 # Backend NestJS
│   ├── src/
│   │   ├── modules/        # Các module chính
│   │   │   ├── auth/       # Xác thực
│   │   │   ├── users/      # Quản lý người dùng
│   │   │   ├── recipes/    # Công thức nấu ăn
│   │   │   ├── posts/      # Bài viết
│   │   │   ├── comments/   # Bình luận
│   │   │   ├── ingredients/# Nguyên liệu
│   │   │   ├── conversations/ # Cuộc trò chuyện
│   │   │   ├── messages/   # Tin nhắn
│   │   │   ├── notifications/ # Thông báo
│   │   │   ├── cloudinary/ # Upload ảnh/video
│   │   │   ├── email/      # Gửi email
│   │   │   └── prisma/     # Prisma service
│   │   ├── common/         # Shared utilities
│   │   │   ├── constants/  # Constants
│   │   │   ├── decorators/ # Custom decorators
│   │   │   ├── dto/        # Data Transfer Objects
│   │   │   ├── guards/     # Auth guards
│   │   │   └── utils/      # Utility functions
│   │   └── main.ts         # Entry point
│   ├── prisma/
│   │   ├── schema.prisma   # Database schema
│   │   └── migrations/     # Database migrations
│   └── package.json
│
├── frontend/               # Frontend React
│   ├── src/
│   │   ├── components/    # React components
│   │   │   ├── common/    # Common components
│   │   │   ├── layout/    # Layout components
│   │   │   ├── Post/      # Post components
│   │   │   ├── Message/   # Message components
│   │   │   ├── modals/    # Modal components
│   │   │   ├── popup/     # Popup components
│   │   │   ├── sections/  # Section components
│   │   │   └── ui/        # UI components
│   │   ├── pages/         # Page components
│   │   │   ├── auth/      # Auth pages
│   │   │   ├── main/      # Main pages
│   │   │   ├── recipe/    # Recipe pages
│   │   │   └── blog/      # Blog pages
│   │   ├── services/      # API services
│   │   ├── contexts/      # React contexts
│   │   ├── hooks/         # Custom hooks
│   │   ├── types/         # TypeScript types
│   │   ├── utils/         # Utility functions
│   │   └── router/        # Routing
│   └── package.json
│
└── README.md
```

## 💻 Yêu cầu hệ thống

- **Node.js**: >= 18.x
- **npm**: >= 9.x hoặc **yarn**
- **MySQL**: >= 8.0
- **Git**

## 🚀 Cài đặt

### 1. Clone repository

```bash
git clone <repository-url>
cd hcm_9-naitei-nodejs-cooking_social_network
```

### 2. Cài đặt Backend

```bash
cd backend
npm install
```

### 3. Cài đặt Frontend

```bash
cd frontend
npm install
```

## ⚙️ Cấu hình

### Backend Environment Variables

Tạo file `.env` trong thư mục `backend/` với các biến sau:

```env
# Database
DATABASE_URL="mysql://user:password@localhost:3306/cooking_social_network"

# JWT
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=7d
JWT_REFRESH_SECRET=your_refresh_token_secret
JWT_REFRESH_EXPIRES_IN=30d

# Server
PORT=3000
FRONTEND_URL=http://localhost:5173

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email (Nodemailer)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
EMAIL_FROM=noreply@cookingsocial.com

# OTP
OTP_EXPIRES_IN=300000
```

### Frontend Environment Variables

Tạo file `.env` trong thư mục `frontend/`:

```env
VITE_API_URL=http://localhost:3000/api
VITE_SOCKET_URL=http://localhost:3000
```

### Database Setup

1. Tạo database MySQL:

```sql
CREATE DATABASE cooking_social_network;
```

2. Chạy migrations:

```bash
cd backend
npx prisma migrate dev
```

3. (Tùy chọn) Seed database với dữ liệu mẫu:

```bash
npx prisma db seed
```

## ▶️ Chạy dự án

### Development Mode

#### Backend

```bash
cd backend
npm run start:dev
```

Backend sẽ chạy tại: `http://localhost:3000`

#### Frontend

```bash
cd frontend
npm run dev
```

Frontend sẽ chạy tại: `http://localhost:5173`

### Production Mode

#### Build Backend

```bash
cd backend
npm run build
npm run start:prod
```

#### Build Frontend

```bash
cd frontend
npm run build
npm run preview
```

## 📚 API Documentation

API base URL: `http://localhost:3000/api`

### Các endpoints chính:

- **Auth**: `/api/auth/*`
  - POST `/api/auth/register` - Đăng ký
  - POST `/api/auth/login` - Đăng nhập
  - POST `/api/auth/logout` - Đăng xuất
  - POST `/api/auth/refresh` - Refresh token
  - POST `/api/auth/forgot-password` - Quên mật khẩu
  - POST `/api/auth/reset-password` - Đặt lại mật khẩu

- **Users**: `/api/users/*`
  - GET `/api/users/profile` - Lấy thông tin profile
  - PUT `/api/users/profile` - Cập nhật profile
  - GET `/api/users/:id` - Lấy thông tin user
  - POST `/api/users/:id/follow` - Follow user
  - DELETE `/api/users/:id/follow` - Unfollow user

- **Recipes**: `/api/recipes/*`
  - GET `/api/recipes` - Danh sách công thức
  - POST `/api/recipes` - Tạo công thức
  - GET `/api/recipes/:id` - Chi tiết công thức
  - PUT `/api/recipes/:id` - Cập nhật công thức
  - DELETE `/api/recipes/:id` - Xóa công thức
  - POST `/api/recipes/:id/save` - Lưu công thức
  - POST `/api/recipes/:id/rating` - Đánh giá công thức

- **Posts**: `/api/posts/*`
  - GET `/api/posts` - Danh sách bài viết
  - POST `/api/posts` - Tạo bài viết
  - GET `/api/posts/:id` - Chi tiết bài viết
  - PUT `/api/posts/:id` - Cập nhật bài viết
  - DELETE `/api/posts/:id` - Xóa bài viết
  - POST `/api/posts/:id/like` - Like bài viết
  - POST `/api/posts/:id/share` - Share bài viết
  - POST `/api/posts/:id/save` - Lưu bài viết

- **Comments**: `/api/comments/*`
  - GET `/api/comments/post/:postId` - Lấy comments của post
  - POST `/api/comments` - Tạo comment
  - PUT `/api/comments/:id` - Cập nhật comment
  - DELETE `/api/comments/:id` - Xóa comment
  - POST `/api/comments/:id/like` - Like comment

- **Messages**: `/api/messages/*`
  - GET `/api/messages/conversation/:conversationId` - Lấy tin nhắn
  - POST `/api/messages` - Gửi tin nhắn
  - PUT `/api/messages/:id` - Cập nhật tin nhắn
  - DELETE `/api/messages/:id` - Xóa tin nhắn

- **Conversations**: `/api/conversations/*`
  - GET `/api/conversations` - Danh sách cuộc trò chuyện
  - POST `/api/conversations` - Tạo cuộc trò chuyện
  - GET `/api/conversations/:id` - Chi tiết cuộc trò chuyện

- **Notifications**: `/api/notifications/*`
  - GET `/api/notifications` - Danh sách thông báo
  - PUT `/api/notifications/:id/read` - Đánh dấu đã đọc

- **Ingredients**: `/api/ingredients/*`
  - GET `/api/ingredients` - Danh sách nguyên liệu
  - POST `/api/ingredients` - Tạo nguyên liệu
  - GET `/api/ingredients/:id` - Chi tiết nguyên liệu

- **Upload**: `/api/upload/*`
  - POST `/api/upload/image` - Upload hình ảnh
  - POST `/api/upload/video` - Upload video

## 🗄️ Database Schema

Dự án sử dụng Prisma ORM với MySQL. Các model chính:

- **User**: Thông tin người dùng
- **Recipe**: Công thức nấu ăn
- **RecipeCategory**: Phân loại công thức
- **RecipeIngredient**: Nguyên liệu trong công thức
- **RecipeStep**: Các bước nấu
- **RecipeRating**: Đánh giá công thức
- **Post**: Bài viết chia sẻ
- **PostMedia**: Media của bài viết
- **PostLike**: Like bài viết
- **PostComment**: Bình luận bài viết
- **PostShare**: Share bài viết
- **Ingredient**: Nguyên liệu
- **Conversation**: Cuộc trò chuyện
- **Message**: Tin nhắn
- **Notification**: Thông báo
- **Relationship**: Quan hệ follow
- **Session**: Session đăng nhập
- **Otp**: Mã OTP

Xem chi tiết trong file `backend/prisma/schema.prisma`

## 🧪 Testing

### Backend Tests

```bash
cd backend
# Unit tests
npm run test

# E2E tests
npm run test:e2e

# Test coverage
npm run test:cov
```

### Frontend Tests

```bash
cd frontend
npm run test
```

## 📝 Scripts hữu ích

### Backend

```bash
# Development
npm run start:dev

# Production
npm run build
npm run start:prod

# Linting
npm run lint

# Format code
npm run format

# Prisma
npx prisma studio          # Mở Prisma Studio
npx prisma migrate dev     # Tạo migration mới
npx prisma generate        # Generate Prisma Client
```

### Frontend

```bash
# Development
npm run dev

# Build
npm run build

# Preview production build
npm run preview

# Linting
npm run lint
```

## 🤝 Đóng góp

1. Fork dự án
2. Tạo feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Mở Pull Request

## 📄 License

Dự án này được phát triển bởi team hcm_9-naitei.

## 👥 Team

- Team: hcm_9-naitei
- Project: Cooking Social Network

## 📞 Liên hệ

Nếu có câu hỏi hoặc góp ý, vui lòng tạo issue trên repository.

---

⭐ Nếu dự án này hữu ích, hãy cho một star!
