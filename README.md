# Baitap2
Phát triển ứng dụng nguồn mở
Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
Lớp: 58KTPM

Bài tập 02:

- SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:
- Khởi động docker
  <img width="959" height="352" alt="Screenshot 2026-05-07 201203" src="https://github.com/user-attachments/assets/0024e040-e165-49ad-b72f-e3c2d1857f00" />
- TẠO THƯ MỤC PROJECT-> tạo thư mục Django
  <img width="959" height="352" alt="Screenshot 2026-05-07 201203" src="https://github.com/user-attachments/assets/16faa444-82e6-411f-8a76-631444c4e220" />
- Tạo Dockerfile
  <img width="966" height="1023" alt="Screenshot 2026-05-07 200851" src="https://github.com/user-attachments/assets/2e2ab0ec-56ab-41f9-8ca6-780a9f9262c6" />
- Tạo file requirements.txt
  + Tạo file requirements.txt : sudo nano requirements.txt
  <img width="962" height="1017" alt="Screenshot 2026-05-07 201128" src="https://github.com/user-attachments/assets/fdfb98fc-fe89-4972-8bfd-0b2c2adbd637" />
 - TẠO docker-compose.yml
     + Quay lại thư mục gốc : cd
     + Tạo docker-compose.yml: sudo nano docker-compose.yml
  <img width="964" height="1023" alt="Screenshot 2026-05-07 201304" src="https://github.com/user-attachments/assets/dc5da17c-9424-475a-b2f8-99180a9e88c1" />
- kiểm tra lại bằng lệnh ls
  <img width="956" height="92" alt="Screenshot 2026-05-07 201322" src="https://github.com/user-attachments/assets/9a78deee-7fe7-4f49-b7b0-9dd6726cb296" />
- BUILD VÀ CHẠY
  + Build project: sudo docker compose up -d --build > - Docker sẽ: tải MariaDB tải PhpMyAdmin build Django
<img width="939" height="703" alt="Screenshot 2026-05-07 202541" src="https://github.com/user-attachments/assets/03a27879-0025-449c-b4de-fa85e582e21f" />
  + kiểm tra container docker ps
<img width="1918" height="286" alt="Screenshot 2026-05-07 202627" src="https://github.com/user-attachments/assets/5ceefe61-2c5d-4041-b19f-dc0b333f1e5e" />
- Tạo TẠO DJANGO PROJECT
  + docker compose exec django bash
- Tạo project Django
  + django-admin startproject config .
- Tạo app
  + python manage.py startapp pawnshop
<img width="959" height="178" alt="Screenshot 2026-05-07 203136" src="https://github.com/user-attachments/assets/00ab1f78-d6a1-4859-9ba4-3e7f11bc9409" />
- SỬA settings.py
  + Mở file: sudo nano django_app/config/settings.py
  + Sửa ALLOWED_HOSTS,Thêm app Tìm: INSTALLED_APPS = [
    <img width="951" height="377" alt="Screenshot 2026-05-07 203345" src="https://github.com/user-attachments/assets/a339ffd9-4ba7-444e-a00c-a520271fe516" />
  + Sửa DATABASES
    <img width="948" height="389" alt="Screenshot 2026-05-07 203506" src="https://github.com/user-attachments/assets/8709623e-74ad-41a8-82eb-a092762c9722" />
- TẠO MODELS
  + sudo nano django_app/pawnshop/models.py
    <img width="959" height="1015" alt="Screenshot 2026-05-07 203546" src="https://github.com/user-attachments/assets/e8685cd5-54b4-4c81-bd98-9e4c9b344c89" />
- Vào MIGRATE DATABASE
  + Vào container: docker compose exec django bash
  + Tạo migratio: python manage.py makemigrations
  + Apply: python manage.py migrate
- Cấu hình Django Admin
  + Tạo tài khoản admin : docker compose exec django python manage.py createsuperuser
  + python manage.py createsuperuser
- Đăng ký model vào admin
Mở file: sudo nano django_app/pawnshop/admin.py
<img width="962" height="1021" alt="Screenshot 2026-05-07 210906" src="https://github.com/user-attachments/assets/ce877da5-b05d-4d71-a253-7446e9eb276d" />
- Restart Django: docker compose restart django
- Truy cập Django Admin: http:/192.168.1.7:8000/admin
  <img width="1914" height="1079" alt="Screenshot 2026-05-07 205624" src="https://github.com/user-attachments/assets/b5dabcf7-925b-4e3c-8714-492f1d07759d" />
- Sau khi login thành công > - KQ được trang admin, yêu cầu đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng
  <img width="1920" height="1080" alt="Screenshot 2026-05-07 211434" src="https://github.com/user-attachments/assets/1aa2c4de-3f9f-459f-950b-4e42a479f876" />
- Kiểm tra FK bằng PhpMyAdmin
  <img width="1920" height="1080" alt="Screenshot 2026-05-07 214542" src="https://github.com/user-attachments/assets/abe6ba9a-524f-433a-b9d7-6abd8c2f0344" />
  <img width="1920" height="1080" alt="Screenshot 2026-05-07 214549" src="https://github.com/user-attachments/assets/3bef86af-d452-4931-b88e-aeabf33dc265" />
  <img width="1920" height="1080" alt="Screenshot 2026-05-07 214558" src="https://github.com/user-attachments/assets/e25d3c14-d36c-4604-b48a-6f7e95cd741f" />


