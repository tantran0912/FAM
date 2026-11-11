# FAM
Xây dựng hệ thống web Nhà hàng Hạnh Thành
# Nhà hàng Hạnh Thành

Website thử nghiệm cho nhà hàng gần Ngã ba Đồng Lộc, Hà Tĩnh.

## Chạy trong VS Code

Mở thư mục dự án `E:\FAM\hanh-thanh` bằng **File → Open Folder**. Trong **Run and Debug**, chọn **Chạy website Hạnh Thành** rồi nhấn **F5**. VS Code sẽ đóng gói mã nguồn, chạy máy chủ Node.js và mở trình duyệt khi máy chủ sẵn sàng.

Live Server ở cổng 5500 chỉ phục vụ tệp tĩnh. CSS, ảnh và API đặt bàn của dự án được phục vụ qua máy chủ Node.js. Khi chỉnh tệp trong `public/` hoặc `src/`, nhấn **Ctrl+Shift+F5** để chạy lại với bản mới.


## Chạy bằng terminal

Cần Node.js 24 trở lên. Không cần cài gói phụ thuộc.

```powershell
cd E:\FAM\hanh-thanh
node --test
node build.mjs
node local.mjs
```

- Website [http://127.0.0.1:3000](http://127.0.0.1:3000)
- Lễ tân [http://127.0.0.1:3000/le-tan](http://127.0.0.1:3000/le-tan)
- Đặt thử một lượt bằng tên và liên hệ mẫu. Chọn cùng ngày ở màn hình lễ tân để thấy yêu cầu và xếp bàn.
- Bản chạy local chỉ lắng nghe loopback và sử dụng dữ liệu SQLite riêng trong `data/`.

## Cấu trúc

| Vị trí | Vai trò |
|---|---|
| `public/` | HTML, CSS, JavaScript và ảnh của trang khách và màn hình lễ tân |
| `src/config.mjs` | Thực đơn, số chỗ từng bàn và thời gian giữ bàn mẫu |
| `src/worker.mjs` | Phục vụ giao diện, API và kiểm tra truy cập |
| `src/reservations.mjs` | Kiểm tra yêu cầu, chống gửi trùng, xác nhận và tránh trùng bàn |
| `schema.sql` và `drizzle/` | Schema SQLite local và migration D1 cho bản chạy trên Sites |
| `build.mjs`, `local.mjs`, `local-db.mjs` | Đóng gói Worker, chạy local và kết nối SQLite |
| `reservations.test.mjs` | Kiểm thử quy tắc đặt bàn |

## Thay dữ liệu mẫu

- Cập nhật thực đơn, giá và danh sách bàn trong `src/config.mjs`. Địa chỉ tham khảo và đường dẫn bản đồ nằm ở `public/index.html`.
- Xác nhận địa chỉ, số liên hệ, giờ mở cửa và quy trình nhận khách trước khi nhận đặt bàn thật. Phiên bản hiện tại kiểm tra ngày giờ trong tương lai và thời hạn đặt trước 90 ngày.
- Các món, giá, sơ đồ bàn và ảnh bữa ăn đang dùng để trình diễn. Phiên bản hiện tại dùng tiếng Việt.
- Bản chạy trên Sites dành cho chủ tài khoản. Trước khi mở cho khách truy cập, cần quyền nhân viên riêng, cơ chế chống gửi hàng loạt và chính sách xử lý thông tin liên hệ. Lễ tân liên hệ khách sau khi xác nhận.

## Ảnh

- `public/images/meal.jpg` là ảnh minh họa tạo bằng ImageGen theo yêu cầu ảnh mâm cơm miền Trung có gà nướng, cá kho, cơm và rau thơm.
- `public/images/monument.jpg` và `public/images/memorial.jpg` là ảnh của Khoitran1957, giấy phép CC BY-SA 4.0. Ảnh đã được thu nhỏ và nén JPEG. Trang có liên kết nguồn của từng ảnh và giấy phép.
- 
