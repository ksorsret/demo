# Hướng Dẫn Cài Đặt Và Chạy Laravel

## Yêu Cầu Hệ Thống

- **PHP** >= 8.1
- **Composer** >= 2.0
- **Database**: MySQL, PostgreSQL, SQLite hoặc SQL Server

## Cài Đặt Laravel

### 1. Clone Project
```bash
git clone https://github.com/ten-cua-ban/ten-du-an.git
cd ten-du-an
```

### 2. Cài Đặt Dependencies
```bash
composer install
```

### 3. Tạo File Environment
```bash
cp .env.example .env
```

Cấu hình thông tin database trong file `.env`:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=ten_database
DB_USERNAME=ten_user
DB_PASSWORD=mat_khau
```

### 4. Tạo Application Key
```bash
php artisan key:generate
```

### 5. Chạy Migration và Seeder (nếu có)
```bash
php artisan migrate --seed
```

### 6. Thiết Lập Quyền Cho Thư Mục (nếu cần)
```bash
chmod -R 775 storage bootstrap/cache
```

## Chạy Ứng Dụng

### 1. Chạy Server Local
```bash
php artisan serve
```

Truy cập ứng dụng tại: [http://localhost:8000](http://localhost:8000)

### 2. Chạy Queue (nếu có sử dụng)
```bash
php artisan queue:work
```

### 3. Chạy Schedule (nếu có sử dụng)
```bash
php artisan schedule:work
```

## Debug và Kiểm Tra

1. Kiểm tra log nếu gặp lỗi:
```bash
tail -f storage/logs/laravel.log
```

2. Xóa cache nếu cần:
```bash
php artisan cache:clear
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

## Triển Khai Production (Tóm Tắt)

1. Cài đặt các package:
```bash
composer install --no-dev --optimize-autoloader
```

2. Chạy migrate:
```bash
php artisan migrate --force
```

3. Xóa và cache lại cấu hình:
```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

4. Thiết lập quyền thư mục:
```bash
chmod -R 775 storage bootstrap/cache
```

5. Khởi động queue:
```bash
php artisan queue:work --daemon
```

## Tài Liệu Tham Khảo

- [Laravel Documentation](https://laravel.com/docs)
