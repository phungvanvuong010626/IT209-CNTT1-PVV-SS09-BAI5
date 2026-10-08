# Bài 5: Khởi chạy dịch vụ đơn giản với Docker Compose

## Mục tiêu

Dùng Docker Compose CLI v2 để khởi chạy 1 dịch vụ web (Nginx) thay cho lệnh `docker run`.

## Nội dung `docker-compose.yml`

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8082:80"
```

- `services.web`: khai báo một dịch vụ tên `web`.
- `image: nginx:alpine`: dùng image Nginx bản alpine (nhẹ).
- `ports: "8082:80"`: ánh xạ cổng 8082 của máy host tới cổng 80 trong container.

> Lưu ý: file YAML thụt lề bằng 2 dấu cách, không dùng phím Tab.

## Các bước thực hiện

1. Khởi chạy dịch vụ ở chế độ nền:

   ```bash
   docker compose up -d
   ```

2. Kiểm tra trạng thái dịch vụ:

   ```bash
   docker compose ps
   ```

   Kết quả mong đợi: service `web` ở trạng thái `running`, cột PORTS hiển thị `0.0.0.0:8082->80/tcp`.

3. Truy cập thử dịch vụ:

   ```bash
   curl http://localhost:8082
   ```

   Kết quả mong đợi: trả về trang chào mừng của Nginx (`<title>Welcome to nginx!</title>` ... `Welcome to nginx!`).

4. Hạ dịch vụ xuống (dừng và xóa container, network):

   ```bash
   docker compose down
   ```

## Kết quả

<!-- Dán ảnh chụp màn hình / output thực tế của docker compose ps và curl tại đây trước khi nộp. -->
