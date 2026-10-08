# 🎓 Techedu - Hệ Thống Website Học Trực Tuyến (LMS)

[![Django](https://img.shields.io/badge/Django-5.1+-092e20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776ab?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Channels](https://img.shields.io/badge/Channels-WebSocket-44b78b?style=for-the-badge&logo=django&logoColor=white)](https://channels.readthedocs.io/)
[![SQLite](https://img.shields.io/badge/Database-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://www.sqlite.org/)

## 1. Giới Thiệu Dự Án

**Techedu** là nền tảng quản trị và hỗ trợ dạy - học trực tuyến (Learning Management System - LMS) được xây dựng nhằm mang đến giải pháp học tập linh động, chất lượng và hoàn toàn miễn phí cho học sinh, sinh viên và cộng đồng người học kỹ thuật số.

Hệ thống cho phép:

- **Người học (Student)**: Dễ dàng tìm kiếm và đăng ký khóa học, học qua video bài giảng nhúng từ YouTube, làm bài tập trắc nghiệm tự động chấm điểm và theo dõi tiến độ học tập cá nhân.
- **Giảng viên (Instructor)**: Biên soạn và tạo mới khóa học, cấu trúc theo từng Chương (Chapter), từng Bài học (Lesson lý thuyết/trắc nghiệm), theo dõi số lượng học viên.
- **Cộng đồng học tập & Blog**: Chia sẻ kiến thức qua các bài viết blog chuyên ngành với trình soạn thảo phong phú (CKEditor), thảo luận và bình luận thời gian thực qua giao thức WebSocket.
- **Quản trị viên (Admin)**: Quản lý toàn bộ danh mục khóa học, bài viết, người dùng và bình luận trong hệ thống.

---

## 2. Tech Stack (Công Nghệ Sử Dụng)

### Backend

- **Ngôn ngữ**: [Python 3.10+](https://www.python.org/)
- **Framework chính**: [Django 5.1.x](https://docs.djangoproject.com/en/5.1/) (Kiến trúc MTV - Model-Template-View)
- **Xử lý Bất đồng bộ & Real-time**: [Django Channels 4.x](https://channels.readthedocs.io/) (Giao thức WebSocket) & `channels-redis`
- **ASGI Server**: [Daphne](https://github.com/django/daphne)
- **Trình soạn thảo văn bản giàu tính năng**: [django-ckeditor](https://github.com/django-ckeditor/django-ckeditor) (Tích hợp MathJax, upload ảnh đa phương tiện)
- **Xử lý hình ảnh**: [Pillow](https://python-pillow.org/) (Upload Avatar, Thumbnail khóa học)
- **REST Framework & API Docs**: `djangorestframework`, `drf-spectacular`, `drf-yasg`
- **Xác thực qua Email**: Django Mail SMTP (Google Mail Server)

### Frontend

- **Cấu trúc & Trình bày**: HTML5 ngữ nghĩa (Semantic HTML), CSS3 chuẩn Responsive (Flexbox, CSS Grid)
- **Tương tác Client-side**: JavaScript thuần (ES6+), [jQuery](https://jquery.com/)
- **Kỹ thuật tải dữ liệu ngầm**: AJAX (Live search khóa học, phân loại category, bài viết blog)
- **Bộ icon hiển thị**: Font Awesome 5 Pro

### Database & Message Broker

- **Hệ quản trị CSDL mặc định**: [SQLite3](https://www.sqlite.org/) (Nhúng, gọn nhẹ, đã có sẵn dữ liệu demo ban đầu `db.sqlite3`)
- **Message Broker / Cache**: [Redis](https://redis.io/) (Phục vụ Channel Layer cho tính năng real-time chat/comment)

---

## 3. Các Tính Năng Chính

| Nhóm chức năng | Mô tả chi tiết |
| :--- | :--- |
| **Xác thực & Người dùng** | • Đăng ký tài khoản gửi mã OTP xác thực qua Email<br>• Đăng nhập, đăng xuất bảo mật<br>• Quên mật khẩu và nhận mã đặt lại qua Email<br>• Cập nhật thông tin cá nhân (Họ tên, SĐT, ngày sinh, mô tả bản thân, avatar)<br>• Phân quyền 3 cấp độ: `Student`, `Instructor`, `Admin` |
| **Quản lý Khóa học** | • Xem danh sách khóa học kèm bộ lọc danh mục và mức độ (Beginner, Intermediate, Advanced)<br>• Tìm kiếm khóa học theo thời gian thực (AJAX)<br>• Xem chi tiết khóa học, nội dung giáo trình, giảng viên<br>• Đăng ký khóa học và lưu vào tủ khóa học của tôi (`My Courses`) |
| **Không gian Học tập** | • Học lý thuyết với video bài giảng tích hợp YouTube Embed<br>• Làm bài thi trắc nghiệm (Quiz 4 lựa chọn) với hệ thống chấm điểm tức thì<br>• Tính toán và cập nhật % tiến độ học tập (`progress`) theo từng học viên |
| **Giảng viên soạn bài** | • Tạo mới khóa học với tiêu đề, thời lượng, cấp độ, ảnh đại diện, danh mục<br>• Thiết lập phân nhánh Chương (`Chapter`) và Bài học (`Lesson`)<br>• Chỉnh sửa và xóa các khóa học do chính mình tạo |
| **Blog & Tương tác** | • Danh sách bài viết tin tức, bài học công nghệ mới nhất<br>• Soạn thảo và đăng bài viết mới với công cụ CKEditor phong phú<br>• Bình luận bài viết và trả lời bình luận nhiều cấp<br>• WebSocket hỗ trợ gửi nhận bình luận tức thời không cần reload trang |
| **Trang Quản trị Admin** | • Quản lý tất cả bảng dữ liệu: Users, Courses, Chapters, Lessons, Questions, Enrollments, Categories, Blogs, Comments |

---

## 4. Cấu Trúc Thư Mục Dự Án

```plaintext
LMS_website_Techedu/
├── B22DCAT129_final_report.pdf    # Báo cáo tổng kết đồ án thực tập cơ sở
├── Propossal/                     # Tài liệu đề cương dự án
├── requirements.txt               # Danh sách thư viện Python cần cài đặt
├── README.md                      # Tài liệu hướng dẫn sử dụng & triển khai
└── sourceCode/
    └── lms_website/
        ├── manage.py              # CLI quản lý ứng dụng Django
        ├── db.sqlite3             # CSDL SQLite lưu trữ dữ liệu mẫu
        ├── requirements.txt       # Bản sao file phụ thuộc
        ├── lms_website/           # Thư mục cấu hình chính của Django
        │   ├── settings.py        # Thiết lập cấu hình hệ thống
        │   ├── urls.py            # Định tuyến URL toàn hệ thống
        │   ├── asgi.py            # Cấu hình ASGI & định tuyến WebSockets
        │   └── wsgi.py            # Cấu hình WSGI cho máy chủ web truyền thống
        ├── app/                   # Ứng dụng nghiệp vụ chính (LMS App)
        │   ├── models.py          # Khai báo các mô hình dữ liệu (User, Course, Lesson, Quiz...)
        │   ├── views.py           # Xử lý toàn bộ logic và phản hồi HTTP/AJAX
        │   ├── consumers.py       # Xử lý kết nối WebSocket cho bình luận Blog
        │   ├── routing.py         # Định tuyến WebSocket URL
        │   ├── forms.py           # Khai báo biểu mẫu nhập liệu
        │   ├── admin.py           # Cấu hình hiển thị trang Admin
        │   ├── templates/         # Giao diện HTML của ứng dụng
        │   └── scripts/           # Script hỗ trợ cập nhật dữ liệu tự động
        ├── static/                # Tệp tĩnh: CSS, JavaScript, hình ảnh
        ├── staticfiles/           # Tệp tĩnh thu thập cho production (collectstatic)
        └── media/                 # Tệp đa phương tiện người dùng tải lên (Avatar, Thumbnail)
```

---

## 5. Hướng Dẫn Tải Và Chạy Code

### Yêu cầu tiên quyết

1. **Python 3.10** trở lên (Khuyến nghị Python 3.10, 3.11 hoặc 3.12).
2. **Git** đã được cài đặt trên máy.
3. *(Tùy chọn)* **Redis Server** (Nếu muốn trải nghiệm tính năng WebSocket Channel Layer đầy đủ trên môi trường nội bộ).

---

### 🔹 Bước 1: Clone mã nguồn về máy

Mở Terminal / PowerShell và thực hiện lệnh:

```bash
git clone https://github.com/tvhoang12/LMS_website_Techedu.git
cd LMS_website_Techedu
```

---

### Bước 2: Tạo và kích hoạt môi trường ảo (Virtual Environment)

- **Cách 1: Sử dụng `venv` tiêu chuẩn của Python (Khuyên dùng)**
  - Trên Windows:

    ```powershell
    python -m venv venv
    .\venv\Scripts\activate
    ```

  - Trên macOS / Linux:

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

- **Cách 2: Sử dụng Anaconda / Miniconda**

  ```bash
  conda create -n lms_env python=3.10 -y
  conda activate lms_env
  ```

---

### 🔹 Bước 3: Cài đặt các thư viện cần thiết

Cài đặt tất cả các dependencies thông qua file [requirements.txt](file:///c:/Users/hh950/Documents/project/LMS_website_Techedu/requirements.txt):

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

### Bước 4: Di chuyển vào thư mục chứa mã nguồn chính

```bash
cd sourceCode/lms_website
```

---

### Bước 5: Cấu hình Cơ sở dữ liệu và Tệp tĩnh

Dự án đã đính kèm sẵn tệp cơ sở dữ liệu `db.sqlite3` với đầy đủ danh mục khóa học, dữ liệu bài giảng và tài khoản quản trị mẫu.

Nếu bạn muốn đồng bộ hoặc khởi tạo lại cơ sở dữ liệu:

```bash
python manage.py makemigrations
python manage.py migrate
```

Thu thập tài nguyên tĩnh (Static files):

```bash
python manage.py collectstatic --noinput
```

*(Tùy chọn)* Nếu bạn muốn tạo một tài khoản Superuser quản trị mới:

```bash
python manage.py createsuperuser
```

---

### Bước 6: Khởi chạy máy chủ (Run Server)

#### Chạy chế độ thông thường (HTTP Development Server)

```bash
python manage.py runserver
```

#### Hoặc chạy qua ASGI Server (Hỗ trợ đầy đủ WebSockets qua Daphne)

```bash
daphne -b 127.0.0.1 -p 8000 lms_website.asgi:application
```

---

### Bước 7: Truy cập ứng dụng

Sau khi khởi chạy thành công, mở trình duyệt web và truy cập vào:

- **Trang chủ học tập**: [http://127.0.0.1:8000](http://127.0.0.1:8000)
- **Trang quản trị Django Admin**: [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

> **Tài khoản Administrator có sẵn trong dữ liệu mẫu:**
>
> - **Username**: `admin`
> - **Email**: `bustren12@gmail.com`
> - *(Ghi chú)*: Nếu không nhớ mật khẩu cũ trong database, bạn có thể chạy lệnh sau để đặt lại mật khẩu admin ngay lập tức:
>
>   ```bash
>   python manage.py changepassword admin
>   ```

---

## 6. Hướng Dẫn Cấu Hình Bổ Sung

### 1. Cấu hình gửi Email (OTP & Quên mật khẩu)

Trong file [settings.py](file:///c:/Users/hh950/Documents/project/LMS_website_Techedu/sourceCode/lms_website/lms_website/settings.py), hệ thống sử dụng giao thức SMTP của Google:

```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = 'your-email@gmail.com'
EMAIL_HOST_PASSWORD = 'your-google-app-password'  # Mật khẩu ứng dụng (App Password)
DEFAULT_FROM_EMAIL = EMAIL_HOST_USER
```

> Để gửi email thực tế, hãy bật tính năng **Xác minh 2 bước** trên tài khoản Google và tạo một **App Password (Mật khẩu ứng dụng)** 16 ký tự để điền vào `EMAIL_HOST_PASSWORD`.

### 2. Cấu hình Redis cho WebSocket Channel Layer

Trong [settings.py](file:///c:/Users/hh950/Documents/project/LMS_website_Techedu/sourceCode/lms_website/lms_website/settings.py):

```python
CHANNEL_LAYERS = {
    "default": {
        "BACKEND": "channels_redis.core.RedisChannelLayer",
        "CONFIG": {
            "hosts": [("127.0.0.1", 6379)],
        },
    },
}
```

* **Khi chạy Production hoặc có Redis**: Đảm bảo Redis server đang mở ở cổng `6379`.
- **Khi thử nghiệm nhanh không cần cài Redis**: Bạn có thể tạm thời thay thế bằng In-Memory Layer:

  ```python
  CHANNEL_LAYERS = {
      "default": {
          "BACKEND": "channels.layers.InMemoryChannelLayer"
      },
  }
  ```

---

## 7. Hướng Dẫn Triển Khai Lên Máy Chủ (Production Deployment)

Khi triển khai trên môi trường Production (như Ubuntu/Linux VPS):

1. **Thiết lập biến môi trường an toàn**:
   - Chuyển `DEBUG = False` trong `settings.py`.
   - Thêm tên miền hoặc IP máy chủ vào `ALLOWED_HOSTS = ['yourdomain.com', 'server_ip']`.
   - Thay đổi `SECRET_KEY` bằng một khóa ngẫu nhiên và bảo mật.
2. **Web Server & Reverse Proxy**:
   - Sử dụng **Nginx** làm Reverse Proxy tiếp nhận HTTPS (cổng 443/80).
   - Định tuyến các request HTTP thông thường và kết nối WebSocket (`Upgrade: websocket`) tới máy chủ **Daphne**.
3. **Quản lý tiến trình (Process Supervisor)**:
   - Sử dụng **Systemd** hoặc **Supervisor** để quản lý tiến trình Daphne và Redis server tự động khởi động cùng hệ thống.
4. **Cơ sở dữ liệu lớn**:
   - Có thể cấu hình chuyển đổi sang **PostgreSQL** hoặc **MySQL** đơn giản bằng cách thay đổi phần `DATABASES` trong `settings.py`.

---

## 8. Tác Giả & Bản Quyền

- **Họ và tên**: Trần Văn Hoàng
- **Email**: `bustren12@gmail.com`
- **GitHub**: [@tvhoang12](https://github.com/tvhoang12)

---
*Dự án phục vụ mục đích học tập, nghiên cứu và phát triển giáo dục mở.*
