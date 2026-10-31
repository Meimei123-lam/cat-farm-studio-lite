# Cat Farm Asset Studio v3 Lite

Website tĩnh dành cho game Nông Trại Mèo. Chạy trực tiếp trên GitHub Pages, không cần Python, Render, API key hoặc thẻ thanh toán.

## Chức năng
- Tạo prompt hàng loạt theo tên asset và hướng (trước/sau/trái/phải/chéo), dùng với ChatGPT Free/Plus.
- Tải ảnh tham chiếu để xem tại chỗ. **Ảnh tham chiếu không tự động gửi sang ChatGPT**: người dùng đính kèm thủ công khi tạo ảnh.
- Nhập nhiều PNG/JPG/WebP; tùy chọn xóa nền gần đồng màu từ mép bằng flood-fill; chuẩn hóa khung hình PNG RGBA, tỷ lệ vật thể và chân đế.
- Xem trước trên nền caro; sửa tên và hướng; tải từng PNG hoặc ZIP chứa PNG + manifest.json.
- Không cần CDN hay thư viện ngoài. ZIP được đóng gói ngay trong trình duyệt.

## Đưa lên GitHub Pages từ Android
1. Mở repository GitHub của bạn. **Nên tạo repository mới** `cat-farm-studio-lite` để không lẫn mã Python cũ.
2. Repository phải **Public** để dùng GitHub Pages trên GitHub Free. Trước khi công khai, đảm bảo không có `.env`, API key hay mật khẩu thật.
3. Tại trang repository, chọn `Add file` → `Upload files` (hoặc `+` → `Upload files`), tải ba file `index.html`, `style.css`, `app.js` lên **thư mục gốc**, không đặt trong thư mục con. File README.md có thể tải thêm.
4. Chọn `Commit changes`.
5. Vào `Settings` → `Pages` → `Build and deployment` → `Source: Deploy from a branch` → `Branch: main` và `/(root)` → `Save`.
6. Đợi trang hoàn tất triển khai; link có dạng `https://TEN-GITHUB.github.io/cat-farm-studio-lite/`.
7. Mở link bằng Chrome Android → menu ⋮ → `Thêm vào màn hình chính`.

**Nếu thay thế repository v3 cũ:** xóa `server.py`, `requirements.txt`, `.env.example`, `.gitignore`, thư mục `static` và file cũ không dùng; tải `index.html`, `style.css`, `app.js` mới vào root. Cẩn thận không xóa dữ liệu bạn muốn giữ. Có thể dùng repository mới để an toàn hơn.

## Cách dùng
1. Nhập danh sách asset, chọn hướng, kích thước và tỷ lệ, bấm **Tạo prompt hàng loạt**.
2. Sao chép prompt, mở ChatGPT Free/Plus, gửi prompt và **đính kèm ảnh tham chiếu trực tiếp trong ChatGPT**.
3. Tải ảnh AI về điện thoại; nhập nhiều ảnh vào bước 2.
4. Nếu ảnh đã trong suốt, chọn **Giữ alpha có sẵn**. Nếu nền phẳng, thử **Xóa nền đồng màu từ mép** rồi kiểm tra viền.
5. Bấm **Chuẩn hóa toàn bộ**; chỉnh tên/hướng, xem nền caro, xuất ZIP.

## Giới hạn cần biết
- Không thể gọi trực tiếp ChatGPT Free/Plus để tạo ảnh tự động từ website tĩnh; OpenAI Image API là dịch vụ tính phí riêng.
- Tách nền flood-fill không chính xác với nền phức tạp, chi tiết mảnh, hoặc nền trùng màu vật thể; ảnh JPEG thường cần kiểm tra lại.
- Kích thước canvas và bounding box được chuẩn hóa tự động nhưng **không bảo đảm nhận diện, tỷ lệ nội tại hay phối cảnh đồng nhất tuyệt đối** giữa các hình AI.
- Ảnh xử lý trong RAM trình duyệt, **không lưu qua lần tải lại trang**. Hãy tải ZIP ngay. Điện thoại yếu có thể hết RAM khi xử lý nhiều ảnh lớn.
- ZIP sử dụng định dạng STORE không nén; các PNG vốn đã nén nên ZIP có thể lớn.
- Không có API key hay dữ liệu ảnh nào được gửi về server của công cụ.
