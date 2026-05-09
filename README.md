# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421

Lớp: 58KTPM

Bài tập 02:

# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
## deadline : 23h59 ngày 09 tháng 5 năm 2026.<br>

1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)<br>

<img width="1920" height="2560" alt="image" src="https://github.com/user-attachments/assets/2ec1afb1-f0a6-48b1-92db-12606f02385e" /><br>

2. Sử dụng Docker Cấu hình các dịch vụ trên Ubuntu:<br>
   - Tạo thư mục chứa dự án<br>

   <img width="570" height="44" alt="image" src="https://github.com/user-attachments/assets/2894d8f6-35ee-40a5-a436-4410a441b877" /><br>

 - Tạo file để build image cho Django: sudo nano app/Dockerfile<br>
   <img width="730" height="306" alt="image" src="https://github.com/user-attachments/assets/3ff6a5c2-befe-4fda-854e-50158b8014ec" /><br>

 - Tạo file app/requirements.txt: sudo nano app/requirements.txt<br>
   <img width="1099" height="232" alt="image" src="https://github.com/user-attachments/assets/3dffc624-6db4-48d8-afb7-608191938058" /><br>

- Tạo file quản lý các service: sudo nano docker-compose.yml<br>
  <img width="989" height="467" alt="image" src="https://github.com/user-attachments/assets/bf5fd409-f3b0-4042-b5fb-6cf6cb233490" /><br>
- Khởi tạo dự án Django và cấu hình Database:<br>
  + docker compose run web django-admin startproject core .<br>
  + docker compose run web python manage.py startapp management<br>
  <img width="1102" height="478" alt="image" src="https://github.com/user-attachments/assets/7503ef4e-ee3f-4e75-9034-6db6ef99d6a4" /><br>
  <img width="1100" height="177" alt="image" src="https://github.com/user-attachments/assets/06098760-eea6-4c33-bd1b-997559ce0320" /><br>

- Sửa file app/core/settings.py để kết nối MariaDB: sudo nano app/core/settings.py<br>
  <img width="1107" height="623" alt="image" src="https://github.com/user-attachments/assets/c33d9320-b293-4e8c-99e9-7260b4c37d31" /><br>
  <img width="1111" height="623" alt="image" src="https://github.com/user-attachments/assets/ec8de3d3-7a8e-45b3-8226-64d96ef646ee" /><br>

- Định nghĩa các bảng dữ liệu trong model.py và admin.py<br>
  <img width="1092" height="444" alt="image" src="https://github.com/user-attachments/assets/4c7f7bed-c24a-42c6-8d35-d216d2597e44" /><br>
<img width="740" height="322" alt="image" src="https://github.com/user-attachments/assets/f7bd1584-195d-4553-a54e-0bd5d5d675f9" /><br>
- Chạy hệ thống và Tạo dữ liệu bằng các lệnh:<br>
  + docker compose up -d<br>
    <img width="1095" height="152" alt="image" src="https://github.com/user-attachments/assets/d67e6ac9-bc59-40d2-b20d-4d27dd9542e2" /><br>

  + docker compose exec web python manage.py makemigrations<br>
    <img width="1077" height="209" alt="image" src="https://github.com/user-attachments/assets/3c5b35d1-0b80-47af-8018-04bc40f9238f" /><br>

  + docker compose exec web python manage.py migrate<br>
    <img width="1091" height="492" alt="image" src="https://github.com/user-attachments/assets/bcad64e9-abb8-4cc7-a67c-a7c79617a6f0" /><br>

  + docker compose exec web python manage.py createsuperuser<br>
  <img width="1089" height="250" alt="image" src="https://github.com/user-attachments/assets/6235e3a0-9926-4520-b242-00daeb4c06d0" /><br>

  ==> Kết quả:<br>
  + Giao diện php và csdl maria ban đầu:<br>
    <img width="1448" height="614" alt="image" src="https://github.com/user-attachments/assets/f09fa55c-0625-4f64-8ebb-33628fb31c71" /><br>
  + Đăng nhập vào trang quản trị của django và thêm dữ liệu các bảng:<br>
    <img width="1855" height="716" alt="image" src="https://github.com/user-attachments/assets/b1beb23a-9778-46c9-99c7-a6af52a6cc7f" /><br>
<img width="1888" height="764" alt="image" src="https://github.com/user-attachments/assets/dde18419-3152-4c68-b868-b01148fb8ccd" /><br>
+ Các bảng sau khi được thêm dữ liệu từ django<br>
<img width="1709" height="691" alt="image" src="https://github.com/user-attachments/assets/4894eb8e-eb9f-47a7-82dc-16c3a7c75b60" /><br>

- Tạo tranh danh sách các con nợ đến hạn mà chưa trả sử dụng cú pháp jinja2 và lấy context từ 1 view home_page<br>
  + Tạo view xử lí logic: sudo nano app/management/views.py<br>
    <img width="1097" height="562" alt="image" src="https://github.com/user-attachments/assets/c082b043-336a-4f1e-a20b-6d83ef9f8691" /><br>
  + Tạo thư mục chứa template và Template HTML với cú pháp Jinja2:<br>
    sudo chown -R $USER:$USER ~/quan_ly_cam_do/app<br>
    mkdir -p app/management/templates/<br>
    sudo nano app/management/templates/home.html<br>
    <img width="1085" height="569" alt="image" src="https://github.com/user-attachments/assets/482c4d73-17d6-42f3-baaf-6bccbea131af" /><br>
  + Đăng ký URL cho trang Home: sudo nano app/core/urls.py<br>
    
    <img width="1072" height="561" alt="image" src="https://github.com/user-attachments/assets/eb0fb692-9808-4332-8241-1708980678b0" /><br>

  ==> Kết quả:<br>
      <img width="1713" height="718" alt="image" src="https://github.com/user-attachments/assets/725a0311-641e-43c2-afbc-d39c9b78908e" /><br>


  - sử dụng cloudflare tunnel để public kết quả lên domain: nguyentuanem.io.vn:<br>
    + curl -L --output cloudflared.deb https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb<br>
    + sudo dpkg -i cloudflared.deb<br>
    + cloudflared tunnel login<br>
      <img width="1866" height="845" alt="image" src="https://github.com/user-attachments/assets/3f1059fa-7731-4d46-a8e5-3c881369f347" /><br>
    + cloudflared tunnel create camdo-tunnel<br>
    + cloudflared tunnel route dns camdo-tunnel nguyentuanem.io.vn<br>
    + cloudflared tunnel run --url http://localhost:8000 camdo-tunnel<br>
===> Kết quả:<br>
<img width="1711" height="626" alt="image" src="https://github.com/user-attachments/assets/5b221821-fc7b-47b1-9df6-84f1a714c041" /><br>
<img width="1707" height="596" alt="image" src="https://github.com/user-attachments/assets/27459987-0e74-4662-b377-90786d8497e4" /><br>

