# JUN

## FOOTFLOW — Hệ thống quản lý tài liệu sản xuất giày thể thao

Giao diện thử nghiệm nằm trong file [`index.html`](./index.html). Đây là website tĩnh, có thể chạy trực tiếp trên GitHub Pages mà không cần cài đặt Node.js hay máy chủ riêng.

### Chức năng

- Thêm, sửa, xóa bản ghi tài liệu sản xuất.
- Thống kê số lượng tài liệu đã nhập kho, chưa nhập kho, đã nhập nhưng chưa xuất hàng và đã xuất kho; mỗi chỉ số hiển thị cả tổng số lượng và số dòng dữ liệu.
- In tem tài liệu sản xuất theo từng dòng, khổ tem mặc định 90 × 55 mm, gồm SKU, mã đơn hàng, nhà cung ứng, màu sắc, số lượng và ngày nhập kho.
- Tự động thêm mã QR tra cứu vào tem; nút **Quét QR** dùng camera trình duyệt để tra cứu nhanh theo QR, SKU hoặc mã đơn hàng.
- Chọn nhiều dòng bằng checkbox, chọn tất cả các dòng đang hiển thị và in nhiều tem trong một lần; bố cục nhiều tem được sắp trên khổ A4.
- Đăng nhập và phân quyền thử nghiệm cho **Admin**, **Nhân viên kho** và **Bộ phận sản xuất**.
- Audit Log theo từng tài khoản: ghi thời gian, tài khoản, vai trò, hành động, đối tượng và chi tiết; Admin có thể lọc và xuất lịch sử CSV.
- Theo dõi mã đơn hàng, mã mua hàng thu mua, nhà cung ứng, SKU, tài liệu, màu sắc, số lượng và ngày tháng liên quan.
- Tìm kiếm tổng quát và lọc nâng cao riêng theo mã SKU (có chứa hoặc khớp chính xác), nhà cung ứng, tình trạng thông quan và ngày nhập kho.
- Nhập dữ liệu từ CSV và xuất dữ liệu ra CSV mở bằng Excel.
- Lưu dữ liệu thử nghiệm trên trình duyệt bằng `localStorage`.
- Giao diện responsive cho máy tính và điện thoại.

### Chạy thử cục bộ

Mở trực tiếp file `index.html` bằng trình duyệt. Dữ liệu mẫu sẽ được nạp lần đầu và các thay đổi sẽ lưu trong trình duyệt hiện tại.

### Tài khoản thử nghiệm và quyền hạn

| Vai trò | Tài khoản | Quyền chính |
|---|---|---|
| Super Admin | `superadmin / superadmin123` | Toàn bộ quyền hệ thống, bao gồm Audit Log và quyền mở rộng trong tương lai |
| Admin | `admin / admin123` | Xem, thêm, sửa, xóa, nhập/xuất CSV, in tem, quét QR |
| Nhân viên kho | `kho / kho123` | Xem, thêm, sửa, nhập/xuất CSV, in tem, quét QR; không xóa |
| Bộ phận sản xuất | `sanxuat / sx123` | Xem, lọc, xuất CSV, in tem, quét QR; không sửa dữ liệu |

### Bật GitHub Pages

1. Mở **Settings → Pages** của repository.
2. Chọn **Deploy from a branch**.
3. Chọn branch `main` và thư mục `/ (root)`.
4. Bấm **Save**.

Sau khi triển khai, website sẽ có địa chỉ dạng:

```text
https://dungnguyenbtsl.github.io/JUN/
```

> Phiên bản hiện tại phù hợp để chạy thử giao diện. Dữ liệu chưa đồng bộ giữa nhiều người dùng vì đang lưu bằng `localStorage`. Khi vận hành thật, nên kết nối thêm Supabase/Firebase hoặc API cơ sở dữ liệu.

> **Lưu ý bảo mật:** phân quyền hiện tại là phân quyền phía trình duyệt để chạy thử trên GitHub Pages. Tài khoản/mật khẩu nằm trong mã JavaScript nên không phù hợp bảo vệ dữ liệu thật. Khi vận hành chính thức, cần chuyển xác thực và kiểm tra quyền sang backend/Supabase/Firebase, kèm cơ sở dữ liệu dùng chung.

Audit Log cũng đang lưu trong `localStorage` của trình duyệt và giới hạn 1.000 dòng gần nhất. Khi triển khai thật, cần lưu log ở backend để tránh người dùng có thể xóa hoặc sửa log phía máy khách.

Tài khoản `superadmin` chỉ dùng để kiểm thử bản GitHub Pages hiện tại. Khi đưa vào vận hành thật, cần thay mật khẩu mẫu bằng cơ chế xác thực backend và không lưu thông tin đăng nhập trong mã nguồn frontend.

### Mã QR và camera

Mã QR trên tem chứa mã bản ghi, SKU và mã đơn hàng. QR được tạo qua dịch vụ ảnh QR bên ngoài để giữ file GitHub Pages nhẹ. Khi quét, trình duyệt cần chạy trên HTTPS (GitHub Pages đáp ứng điều kiện này) và người dùng cần cấp quyền camera. Chrome/Edge trên thiết bị hỗ trợ `BarcodeDetector` sẽ quét trực tiếp; nếu không, có thể nhập SKU hoặc mã đơn hàng vào ô tra cứu thủ công.
