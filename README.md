# Baitap2
Phát triển ứng dụng nguồn mở
Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
Lớp: 58KTPM

# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
## deadline : 23h59 ngày 09 tháng 5 năm 2026.
1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)
2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:
   
- Mariadb : chứa csdl của hệ thống này

- Phpmyadmin: để soi được csdl (chỉ để xem, ko cần tạo bảng từ đây, django sẽ làm hết)

- Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file

sau khi có 3 service này trong file docker-compose.yml :

- run nó, cấu hình để Django nhận csdl mariadb (sửa file settings.py), cấu hình user login ban đầu, mô tả các bảng trong models.py, .... (đc phép sử dụng AI để làm) => KQ được trang admin, y/c đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)

- chú ý kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file.

- sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!

- sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain => chụp kết quả

- Hướng dẫn:

+ Tạo thư mục để chứa image tự buid cho django

+ Vào thư mục đó tạo file tên: Dockerfile (nội dung hỏi AI xem file này cần có nội dung gì, full comment cho từng dòng lệnh trong file này => mục tiêu kép: để hiểu và để hệ thống chạy được)

+ AI sẽ nói cần thêm file requirements.txt để cài các thư viện cho python (cài qua lệnh pip) => tạo file requirements.txt với nội dung tưng ứng, trong file này cũng comment được => comment xem thư viện nào dùng để làm gì

+ Sau mỗi lần sửa đỏi có thể phải chạy lệnh dạng : docker compose exec TÊN_SERVICE_DJANGO_CỦA_BẠN python manage.py migrate để tác động vào django (còn nhiều lệnh khác chứ ko luôn như này), để django thay đổi csdl hoặc thay đổi cấu hình.

# BÀI LÀM

- SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

<img width="592" height="1280" alt="z7805530251818_27da3810f90d2b0098e5ce5887cbb8c5" src="https://github.com/user-attachments/assets/14cfe2e0-683a-4901-826d-8a25a314a100" />

<img width="592" height="1280" alt="z7805566009519_b3262d45287966e7eaa2c204fef5dc2c" src="https://github.com/user-attachments/assets/df78c948-74ee-4a8d-8ad3-6cd8857f1be0" />

<img width="592" height="1280" alt="z7805570721818_461c8d0295680bedd96ce6898564f70d" src="https://github.com/user-attachments/assets/0cce1049-03ad-42bf-af5f-75deeacfc515" />

2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:
- Khởi động docker

  <img width="959" height="352" alt="Screenshot 2026-05-07 201203" src="https://github.com/user-attachments/assets/0024e040-e165-49ad-b72f-e3c2d1857f00" />

-  TẠO THƯ MỤC PROJECT-> tạo thư mục Django

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
  <img width="1914" height="1079" alt="Screenshot 2026-05-07 205624" src="https://github.com/user-attachments/assets/27b4802c-24bb-4199-9c95-d74d61376d8f" />
- Đăng ký model vào admin
- Mở file: sudo nano django_app/pawnshop/admin.py
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

- Test FK hoạt động đúng:
  
   + Thêm dữ liệu thử

      + Thêm khách hàng
  
    <img width="952" height="1034" alt="Screenshot 2026-05-07 211042" src="https://github.com/user-attachments/assets/196aca95-71fd-4ba9-adeb-ab7109afafb2" />
   
    <img width="1920" height="1080" alt="Screenshot 2026-05-07 211434" src="https://github.com/user-attachments/assets/95389cda-f18f-4e7c-95e4-256f621593ab" />

  + Thêm đồ cầm
  
    <img width="1920" height="1080" alt="Screenshot 2026-05-08 134528" src="https://github.com/user-attachments/assets/59581843-6e86-444e-ad59-2d6fbefce2b8" />
  
- Template HTML + Jinja2 + View
  
- Tạo thư mục templates > - Đang ở: ~/camdo_project
  
  + Chạy: mkdir -p ~/camdo_project/django_app/templates
    
- Tạo file home.html:sudo nano ~/camdo_project/django_app/templates/home.html

  <img width="972" height="1029" alt="Screenshot 2026-05-07 211715" src="https://github.com/user-attachments/assets/559116fc-2acd-4979-b54f-88ae8b7885a5" />

- Tạo view

   + sudo nano ~/camdo_project/django_app/pawnshop/views.py
  
   <img width="983" height="1041" alt="Screenshot 2026-05-07 211744" src="https://github.com/user-attachments/assets/f8389285-9a4b-4aa2-8dc1-801edb9f028b" />

- Mở: sudo nano ~/camdo_project/django_app/config/urls.py

   <img width="969" height="1031" alt="Screenshot 2026-05-07 211824" src="https://github.com/user-attachments/assets/b937bbd6-c9dc-4ffb-bfd7-4121e26df2f4" />

- sau đó Restart Django: docker compose restart django

- Mở website vào : http://192.168.1.7:8000 -> sẽ thấy: Danh sách con nợ quá hạn,đã trả và chưa hết hạn

   <img width="1920" height="1080" alt="Screenshot 2026-05-07 214239" src="https://github.com/user-attachments/assets/c9ad4447-ab53-4ab8-a81f-d1ba84cb77b9" />

- Kiểm tra dữ liệu bằng phpMyAdmin

   <img width="1920" height="1080" alt="Screenshot 2026-05-07 214549" src="https://github.com/user-attachments/assets/b5ecb361-487e-4db2-b39e-22c932f5f740" />

   <img width="1920" height="1080" alt="Screenshot 2026-05-07 214558" src="https://github.com/user-attachments/assets/eadb3cfe-ba7b-4333-8266-96c9abd037f0" />

- Cài cloudflared

   + wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
    
  + sudo dpkg -i cloudflared-linux-amd64.deb
    
- Chạy domain tunnel tạm thời: cloudflared tunnel --url http://localhost:8000 nó sẽ hiện thị-> sau đó sửa file :sudo nano django_app/config/settings.py

   <img width="1476" height="758" alt="Screenshot 2026-05-07 221558" src="https://github.com/user-attachments/assets/05a6a884-9852-4c9f-8a22-8dd783c43413" />

- test

  + Mở http://camdo.nguyenthilinhk58.id.vn/admin
  <img width="1920" height="1080" alt="Screenshot 2026-05-07 222651" src="https://github.com/user-attachments/assets/c42f6d78-135c-44f4-92f1-6ce6aa7ada9d" />

  + Mở http://camdo.nguyenthilinhk58.id.vn
    <img width="1920" height="1080" alt="Screenshot 2026-05-08 134458" src="https://github.com/user-attachments/assets/21efa2c8-3104-4a78-83a3-be7be3c12036" />



