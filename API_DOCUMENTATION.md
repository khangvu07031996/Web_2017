## Tài liệu API & Thành phần Công khai

### Tổng quan
- Ứng dụng hiện tại bao gồm một trang HTML duy nhất `b1.html`.
- Toàn bộ giao diện được tổ chức bằng các khối `<div>` với class `.header`, `.main`, `.left`, `.right`, và phần tử `footer`.
- Trang phụ thuộc vào tập tin stylesheet `b1.css` (không có trong kho mã hiện tại). Khi triển khai thực tế, cần bảo đảm tập tin CSS này được cung cấp để nhận toàn bộ định dạng.
- Không có JavaScript, API động hay hàm xử lý nào khác; tài liệu này tập trung vào cấu trúc và cách tái sử dụng các thành phần HTML.

### Thành phần bố cục chính

**`<div class="header">`**
- Vai trò: Chứa phần tiêu đề chính của trang.
- Nội dung mặc định: một phần tử `<h1>` hiển thị chữ "Header...".
- Tùy chỉnh:
  - Thay đổi nội dung `<h1>` để cập nhật tiêu đề.
  - Có thể chèn thêm logo, thanh điều hướng, hoặc nút hành động bên trong.

Ví dụ:

```html
<div class="header">
  <div class="index">
    <h1>Trang Chủ Công Ty ABC</h1>
  </div>
</div>
```

**`<div class="main">`**
- Vai trò: Chứa toàn bộ nội dung chính của trang, gồm ba cột: nội dung trung tâm (`.maincontent`), cột trái (`.left`), và cột phải (`.right`).
- Mỗi cột sử dụng cùng một lớp con `.index` (và trong nhiều trường hợp thêm `id="leftText"` để áp dụng định dạng CSS cụ thể).

**`<div class="maincontent">`**
- Vai trò: Khu vực nội dung trung tâm.
- Nội dung mặc định: một `<div class="index" id="leftText">` chứa nhiều cấp tiêu đề (`<h1>`, `<h3>`) và đoạn văn `<p>`.
- Tùy chỉnh:
  - Sử dụng `<h1>` cho tiêu đề chính của bài viết hoặc phần nội dung.
  - Dùng `<h3>` cho tiêu đề con và `<p>` cho đoạn mô tả.
  - Có thể chèn hình ảnh, bảng, hay các thành phần HTML khác bên trong.

Ví dụ thêm nội dung sản phẩm:

```html
<div class="maincontent">
  <div class="index" id="leftText">
    <h1>Sản phẩm nổi bật</h1>
    <p>Giới thiệu ngắn gọn về sản phẩm.</p>
    <h3>Tính năng chính</h3>
    <ul>
      <li>Tính năng A</li>
      <li>Tính năng B</li>
    </ul>
  </div>
</div>
```

**`<div class="left">`**
- Vai trò: Cột phụ bên trái, thường dùng cho phần giới thiệu hoặc thông tin bổ sung.
- Nội dung mặc định: Tiêu đề `<h2>` và hai đoạn văn `<p>`.
- Tùy chỉnh:
  - Chèn thêm các danh sách, box thông báo, hoặc biểu mẫu liên hệ ngắn.
  - Có thể đổi `id="leftText"` thành `class` khác nếu cần tách biệt định dạng CSS.

Ví dụ danh sách bài viết:

```html
<div class="left">
  <div class="index" id="leftText">
    <h2>Bài đăng mới</h2>
    <ul>
      <li><a href="/blog/bai-1.html">Giải pháp cloud 2025</a></li>
      <li><a href="/blog/bai-2.html">Tối ưu chi phí hạ tầng</a></li>
    </ul>
  </div>
</div>
```

**`<div class="right">`**
- Vai trò: Cột phụ bên phải, cung cấp danh sách liên kết hoặc menu.
- Nội dung mặc định: một tiêu đề `<h2>`, theo sau là nhiều khối `<h3>` + `<ul>` gồm các liên kết ảo (`href="#"`).
- Tùy chỉnh:
  - Thay liên kết giả bằng URL thực.
  - Gộp danh sách, thêm icon bằng `<i>` hoặc `<span class="icon">`.
  - Có thể chuyển đổi khối này thành phần sidebar cho các module như “Tin nổi bật”, “Tài liệu”, v.v.

Ví dụ khai báo liên kết tài liệu:

```html
<div class="right">
  <div class="index" id="leftText">
    <h2>Tài liệu</h2>
    <h3>Hướng dẫn triển khai</h3>
    <ul>
      <li><a href="/docs/setup.html">Cài đặt ban đầu</a></li>
      <li><a href="/docs/deploy.html">Triển khai sản phẩm</a></li>
    </ul>
  </div>
</div>
```

**`<footer>`**
- Vai trò: Phần chân trang của toàn bộ ứng dụng.
- Nội dung mặc định: một `<h2>` hiển thị chữ "Footer...".
- Tùy chỉnh:
  - Thay nội dung bằng thông tin bản quyền, liên kết mạng xã hội, hoặc form đăng ký bản tin.

Ví dụ:

```html
<footer>
  <div class="footer">
    <p>© 2025 Công ty ABC. Mọi quyền được bảo lưu.</p>
    <p>
      <a href="/terms.html">Điều khoản</a> | 
      <a href="/privacy.html">Chính sách bảo mật</a>
    </p>
  </div>
</footer>
```

### Quy tắc tái sử dụng & mở rộng
- **Phân lớp CSS:** Các class `.header`, `.main`, `.left`, `.right`, `.footer`, `.index`, `#leftText` có thể được tái sử dụng trong nhiều trang để giữ tính nhất quán. Khi mở rộng, cân nhắc chuyển đổi `id="leftText"` sang class để tránh trùng lặp ID nếu dùng nhiều lần trên cùng một trang.
- **Kết hợp JavaScript:** Mặc dù hiện tại chưa có script, có thể bổ sung `<script>` cuối thân trang để thêm tương tác (ví dụ: đóng/mở sidebar, tải nội dung động).
- **Tương thích CSS:** Bảo đảm mỗi thành phần đều có định dạng trong `b1.css`. Khi tạo trang mới, cập nhật hoặc tạo stylesheet tương ứng.

### Hướng dẫn triển khai
1. **Chuẩn bị môi trường**: 
   - Đặt `b1.html` cùng thư mục với `b1.css`.
   - Cấu hình máy chủ tĩnh (hoặc mở trực tiếp `b1.html` trong trình duyệt để xem).
2. **Tùy chỉnh nội dung**:
   - Thay đổi tiêu đề, đoạn văn, và liên kết theo yêu cầu dự án.
   - Giữ cấu trúc phân cột để đảm bảo bố cục hiển thị đúng với CSS hiện có.
3. **Bổ sung stylesheet (nếu thiếu)**:
   - Nếu `b1.css` chưa tồn tại, tạo mới với các quy tắc định dạng cơ bản cho những class được đề cập.
4. **Kiểm thử hiển thị**:
   - Mở trang trong các trình duyệt phổ biến (Chrome, Firefox, Edge) để đảm bảo tương thích.
   - Kiểm tra phản hồi khi thay đổi kích thước màn hình; bổ sung media queries trong CSS nếu cần.

### Ví dụ trang hoàn chỉnh

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="utf-8">
    <title>Trang giới thiệu sản phẩm</title>
    <link rel="stylesheet" href="b1.css">
  </head>
  <body>
    <div class="header">
      <div class="index">
        <h1>Sản phẩm A+</h1>
      </div>
    </div>

    <div class="main">
      <div class="maincontent">
        <div class="index" id="leftText">
          <h1>Giải pháp tối ưu</h1>
          <p>Đem lại hiệu suất vượt trội và chi phí tối ưu cho doanh nghiệp.</p>
          <h3>Lợi ích</h3>
          <p>Tự động hóa quy trình, giảm thời gian triển khai và dễ dàng mở rộng.</p>
        </div>
      </div>

      <div class="left">
        <div class="index" id="leftText">
          <h2>Khách hàng tiêu biểu</h2>
          <p>Công ty XYZ, Tập đoàn DEF, Start-up GHI.</p>
        </div>
      </div>

      <div class="right">
        <div class="index" id="leftText">
          <h2>Tài nguyên</h2>
          <h3>Tài liệu kỹ thuật</h3>
          <ul>
            <li><a href="/docs/setup.html">Cài đặt</a></li>
            <li><a href="/docs/integration.html">Tích hợp</a></li>
          </ul>
        </div>
      </div>
    </div>

    <div class="clear"></div>

    <footer>
      <div class="footer">
        <p>© 2025 Công ty ABC</p>
      </div>
    </footer>
  </body>
</html>
```

### Ghi chú bổ sung
- `khang.md` chỉ chứa thông tin văn bản đơn giản (“i am khang vu”), không có API hay thành phần tái sử dụng. Nếu dùng làm hồ sơ tác giả, cân nhắc chuyển thành tài liệu markdown chi tiết hơn.
- Khi phát triển thêm các trang/phần mềm mới, nên tách nội dung thành các component rõ ràng (ví dụ sử dụng framework như React, Vue) để dễ quản lý và mở rộng tài liệu API trong tương lai.
