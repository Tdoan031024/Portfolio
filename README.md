# 🚀 DOANTECH Portfolio

> Trang web Portfolio cá nhân hiện đại kết hợp mô hình 3D tương tác, hiệu ứng chuyển động mượt mà và hệ thống quản lý tin nhắn liên hệ full-stack.

---

## 📌 Mục Lục

- [Giới Thiệu](#-giới-thiệu)
- [Công Nghệ Sử Dụng](#-công-nghệ-sử-dụng)
- [Cấu Trúc Thư Mục](#-cấu-trúc-thư-mục)
- [Yêu Cầu Môi Trường](#-yêu-cầu-môi-trường)
- [Hướng Dẫn Cài Đặt & Khởi Chạy](#-hướng-dẫn-cài-đặt--khởi-chạy)
  - [1. Thiết Lập Cơ Sở Dữ Liệu](#1-thiết-lập-cơ-sở-dữ-liệu-mysql)
  - [2. Khởi Chạy Backend (NestJS)](#2-khởi-chạy-backend-nestjs)
  - [3. Khởi Chạy Frontend (Next.js)](#3-khởi-chạy-frontend-nextjs)
- [Biến Môi Trường (Environment Variables)](#-biến-môi-trường)
- [Các Tính Năng Nổi Bật](#-các-tính-năng-nổi-bật)

---

## 📖 Giới Thiệu

**DOANTECH Portfolio** là dự án website portfolio cá nhân được thiết kế để giới thiệu kỹ năng, kinh nghiệm và các dự án thực chiến:
* **Mặt hình ảnh & tương tác:** Tích hợp mô hình 3D với Three.js, hiệu ứng mượt mà từ Framer Motion & GSAP.
* **Mặt dữ liệu & xử lý:** Backend NestJS mạnh mẽ, kết nối cơ sở dữ liệu MySQL qua TypeORM để lưu trữ và quản lý form liên hệ (`Contact`).

---

## 🛠 Công Nghệ Sử Dụng

### 🌐 Frontend
- **Framework:** [Next.js 16](https://nextjs.org/) (App Router, React 19)
- **Styling:** [TailwindCSS v4](https://tailwindcss.com/)
- **3D Graphics:** [Three.js](https://threejs.org/) (Mô hình 3D phòng IT `room_IT_3d.glb`)
- **Animation:** [Framer Motion](https://www.framer.com/motion/) & [GSAP](https://greensock.com/gsap/)
- **Icons:** [Simple Icons](https://simpleicons.org/)
- **Ngôn ngữ:** TypeScript

### ⚙️ Backend
- **Framework:** [NestJS 11](https://nestjs.com/) (Node.js framework)
- **ORM:** [TypeORM](https://typeorm.io/)
- **Database Driver:** `mysql2`
- **Validation:** `class-validator`, `class-transformer`
- **Ngôn ngữ:** TypeScript

### 🗄️ Database
- **Hệ quản trị:** [MySQL](https://www.mysql.com/) / MariaDB

---

## 📁 Cấu Trúc Thư Mục

```text
doan_portfolio/
├── frontend/             # Ứng dụng Next.js (Giao diện người dùng)
│   ├── public/           # Tài nguyên tĩnh, ảnh, mô hình 3D (.glb)
│   ├── src/
│   │   ├── app/          # App router Next.js
│   │   └── components/   # Các component & section (Hero, 3D Intro, Skills, Projects,...)
│   ├── package.json
│   └── .gitignore
│
├── backend/              # Ứng dụng NestJS (REST API)
│   ├── src/
│   │   ├── contact/      # Module xử lý gửi tin nhắn liên hệ
│   │   ├── app.module.ts # Root module & kết nối database TypeORM
│   │   └── main.ts       # Entry point backend (Port 4000, CORS)
│   ├── .env.example      # File mẫu cấu hình biến môi trường
│   ├── package.json
│   └── .gitignore
│
├── database/             # Script khởi tạo cơ sở dữ liệu
│   └── schema.sql        # Script tạo database & bảng `contact_messages`
│
├── huongdan/             # Tài liệu, ghi chú và tài nguyên hướng dẫn thiết kế
│
└── .gitignore            # Git ignore tổng quan dự án
```

---

## 📋 Yêu Cầu Môi Trường

Trước khi bắt đầu, hãy đảm bảo máy tính đã cài đặt:
- **Node.js:** phiên bản `18.x` trở lên (khuyến nghị `20.x` LTS)
- **npm** hoặc **yarn / pnpm**
- **MySQL Server** (hoặc XAMPP, Laragon, Docker MySQL)

---

## 🚀 Hướng Dẫn Cài Đặt & Khởi Chạy

### 1. Thiết Lập Cơ Sở Dữ Liệu (MySQL)
1. Mở công cụ quản lý MySQL (HeidiSQL, MySQL Workbench, phpMyAdmin hoặc CLI).
2. Chạy file SQL tại `database/schema.sql`:
   ```sql
   CREATE DATABASE IF NOT EXISTS portfolio CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

   USE portfolio;

   CREATE TABLE IF NOT EXISTS contact_messages (
     id INT UNSIGNED NOT NULL AUTO_INCREMENT,
     name VARCHAR(120) NOT NULL,
     email VARCHAR(200) NOT NULL,
     subject VARCHAR(200) NULL,
     message TEXT NOT NULL,
     created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
     PRIMARY KEY (id)
   );
   ```

---

### 2. Khởi Chạy Backend (NestJS)

1. Mở terminal và di chuyển vào thư mục backend:
   ```bash
   cd backend
   ```
2. Cài đặt các thư viện (nếu chưa cài):
   ```bash
   npm install
   ```
3. Tạo file `.env` từ file mẫu:
   ```bash
   cp .env.example .env
   ```
   *Chỉnh sửa các thông số kết nối MySQL (`DB_USER`, `DB_PASS`, `DB_NAME`,...) cho phù hợp với máy của bạn.*

4. Chạy server ở chế độ phát triển (Development):
   ```bash
   npm run start:dev
   ```
   > 📡 Backend API sẽ chạy tại: `http://localhost:4000` (Prefix: `/api`)

---

### 3. Khởi Chạy Frontend (Next.js)

1. Mở một cửa sổ terminal mới và di chuyển vào thư mục frontend:
   ```bash
   cd frontend
   ```
2. Cài đặt các thư viện:
   ```bash
   npm install
   ```
3. Khởi chạy server phát triển:
   ```bash
   npm run dev
   ```
   > 🌐 Mở trình duyệt và truy cập: [http://localhost:3000](http://localhost:3000)

---

## 🔐 Biến Môi Trường

### Backend (`backend/.env`)
| Tên Biến | Giá trị mặc định | Mô tả |
| :--- | :--- | :--- |
| `PORT` | `4000` | Cổng chạy Backend API |
| `DB_HOST` | `localhost` | Địa chỉ máy chủ MySQL |
| `DB_PORT` | `3306` | Cổng kết nối MySQL |
| `DB_USER` | `root` | Tài khoản MySQL |
| `DB_PASS` | `your_password` | Mật khẩu MySQL |
| `DB_NAME` | `portfolio` | Tên cơ sở dữ liệu |
| `CORS_ORIGIN` | `http://localhost:3000` | URL Frontend được phép gọi API |

---

## ✨ Các Tính Năng Nổi Bật

- [x] **Intro 3D Model:** Tích hợp mô hình Three.js sống động ngay phần mở đầu trang.
- [x] **Hero & About:** Trình bày thông tin cá nhân và định hướng phát triển trực quan.
- [x] **Skills Showcase:** Hiển thị kỹ năng với icon thương hiệu chuyên nghiệp.
- [x] **Experience & Projects:** Giới thiệu quá trình làm việc và các sản phẩm nổi bật.
- [x] **Contact Form:** Gửi tin nhắn liên hệ trực tiếp, xác thực dữ liệu và lưu trữ an toàn vào cơ sở dữ liệu.
- [x] **Responsive:** Tối ưu hóa hiển thị trên máy tính, máy tính bảng và điện thoại.

---

## 👤 Tác Giả
- **Developer:** Doan
- **GitHub:** [@Tdoan031024](https://github.com/Tdoan031024)
- **Dự án:** [myportfolio](https://github.com/Tdoan031024/myportfolio.git)
