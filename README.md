# BÀI TẬP 02 - WEB QUẢN LÝ TIỆM CẦM ĐỒ BẰNG DJANGO

## Thông tin sinh viên

* **Môn học:** Phát triển ứng dụng với mã nguồn mở - TEE0421
* **Lớp:** 58KTPM
* **Họ tên sinh viên:** Vũ Bảo Khánh
* **Mã số sinh viên:** K225480106028

---

# ĐỀ TÀI

Xây dựng hệ thống quản lý tiệm cầm đồ sử dụng:

* Django
* Docker
* MariaDB
* PhpMyAdmin
* Cloudflare Tunnel

Hệ thống cho phép:

* Quản lý khách hàng
* Quản lý hợp đồng cầm đồ
* Theo dõi các khoản nợ đến hạn
* Hiển thị danh sách khách hàng chưa thanh toán
* Quản trị dữ liệu bằng Django Admin

---

# CÔNG NGHỆ SỬ DỤNG

| Công nghệ         | Mục đích                          |
| ----------------- | --------------------------------- |
| Django            | Framework backend Python          |
| MariaDB           | Hệ quản trị cơ sở dữ liệu         |
| PhpMyAdmin        | Quản lý và kiểm tra cơ sở dữ liệu |
| Docker            | Triển khai các service            |
| Cloudflare Tunnel | Public website ra Internet        |
| HTML/CSS          | Giao diện web                     |

---

# KIẾN TRÚC HỆ THỐNG

Hệ thống gồm 3 service chính:

```yaml
services:
  - django
  - mariadb
  - phpmyadmin
```

## Chức năng từng service

### 1. Django

* Chạy ứng dụng web
* Xử lý nghiệp vụ
* Kết nối database MariaDB
* Render template HTML

### 2. MariaDB

* Lưu trữ dữ liệu khách hàng
* Lưu hợp đồng cầm đồ
* Lưu thông tin khoản nợ

### 3. PhpMyAdmin

* Kiểm tra dữ liệu trong database
* Quan sát khóa ngoại và dữ liệu bảng

---

# CẤU TRÚC CƠ SỞ DỮ LIỆU

## Bảng Khách Hàng

* Họ tên
* Số điện thoại
* Địa chỉ

## Bảng Hợp Đồng Cầm Đồ

* Tài sản cầm cố
* Số tiền vay
* Ngày đến hạn
* Trạng thái thanh toán
* Liên kết tới khách hàng (Foreign Key)

---

# TRIỂN KHAI DOCKER

## Dockerfile

Dockerfile dùng để build container Django.

Các bước chính:

1. Sử dụng image Python
2. Cài thư viện từ requirements.txt
3. Copy source code
4. Chạy server Django

---

# REQUIREMENTS.TXT

```txt
Django
mysqlclient
pymysql
```

## Ý nghĩa

* Django: framework backend
* mysqlclient / pymysql: kết nối MariaDB

---

# CHỨC NĂNG DJANGO ADMIN

Hệ thống cho phép:

* Thêm dữ liệu
* Sửa dữ liệu
* Xóa dữ liệu
* Chọn khóa ngoại bằng text

Các bảng được quản lý:

* Khách hàng
* Hợp đồng cầm đồ

---

# TEMPLATE HIỂN THỊ DANH SÁCH NỢ ĐẾN HẠN

Trang web sử dụng:

* HTML
* CSS
* Template Django (Jinja2)

Dữ liệu được truyền từ view `home_page`.

Trang hiển thị:

* Tên khách hàng
* Số điện thoại
* Tài sản cầm cố
* Số tiền nợ
* Ngày đến hạn

---

# HÌNH ẢNH KẾT QUẢ

## 1. Code giao diện template HTML

<img width="1603" height="897" alt="image" src="https://github.com/user-attachments/assets/057d1afa-7bbc-4597-8745-5f2b53398f2e" />

---

## 2. Giao diện danh sách nợ đến hạn

<img width="1599" height="897" alt="image" src="https://github.com/user-attachments/assets/4fdcf338-e753-497e-a395-a57766b2e422" />

---

## 3. Django Admin quản lý hợp đồng cầm đồ

<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/b1a84360-bdbd-48e6-a2ea-1b36aac68061" />

---

# PUBLIC WEBSITE BẰNG CLOUDFLARE TUNNEL

Website đã được public bằng Cloudflare Tunnel.

Ví dụ domain:

```txt
quanly.baokhanh2004.id.vn
```

---

# KẾT QUẢ ĐẠT ĐƯỢC

✅ Tạo thành công hệ thống quản lý tiệm cầm đồ

✅ Kết nối Django với MariaDB bằng Docker

✅ Quản trị dữ liệu bằng Django Admin

✅ Hiển thị danh sách nợ đến hạn

✅ Public website bằng Cloudflare Tunnel

---

# HƯỚNG DẪN CHẠY DỰ ÁN

## Bước 1: Clone source

```bash
git clone <repository>
cd project
```

## Bước 2: Chạy Docker Compose

```bash
docker compose up -d
```

## Bước 3: Migrate database

```bash
docker compose exec django python manage.py migrate
```

## Bước 4: Tạo tài khoản admin

```bash
docker compose exec django python manage.py createsuperuser
```

## Bước 5: Truy cập hệ thống

### Django Admin

```txt
http://localhost:8000/admin
```

### Trang danh sách nợ

```txt
http://localhost:8000/
```

---

# KẾT LUẬN

Qua bài tập này đã thực hiện được:

* Sử dụng Django để xây dựng ứng dụng web
* Kết nối MariaDB bằng Docker
* Quản lý dữ liệu bằng Django Admin
* Render dữ liệu bằng template HTML
* Public website bằng Cloudflare Tunnel

Đây là mô hình triển khai phù hợp cho các ứng dụng quản lý cơ bản sử dụng mã nguồn mở.
