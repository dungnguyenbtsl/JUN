# JUN

## FOOTFLOW — Hệ thống quản lý tài liệu sản xuất giày thể thao

Giao diện thử nghiệm nằm trong file [`index.html`](./index.html). Đây là website tĩnh, có thể chạy trực tiếp trên GitHub Pages mà không cần cài đặt Node.js hay máy chủ riêng.

### Chức năng

- Thêm, sửa, xóa bản ghi tài liệu sản xuất.
- Thống kê số lượng tài liệu đã nhập kho, chưa nhập kho, đã nhập nhưng chưa xuất hàng và đã xuất kho; mỗi chỉ số hiển thị cả tổng số lượng và số dòng dữ liệu.
- In tem tài liệu sản xuất theo từng dòng, khổ tem mặc định 90 × 55 mm, gồm SKU, mã đơn hàng, nhà cung ứng, màu sắc, số lượng và ngày nhập kho.
- Theo dõi mã đơn hàng, mã mua hàng thu mua, nhà cung ứng, SKU, tài liệu, màu sắc, số lượng và ngày tháng liên quan.
- Tìm kiếm tổng quát và lọc nâng cao riêng theo mã SKU (có chứa hoặc khớp chính xác), nhà cung ứng, tình trạng thông quan và ngày nhập kho.
- Nhập dữ liệu từ CSV và xuất dữ liệu ra CSV mở bằng Excel.
- Lưu dữ liệu thử nghiệm trên trình duyệt bằng `localStorage`.
- Giao diện responsive cho máy tính và điện thoại.

### Chạy thử cục bộ

Mở trực tiếp file `index.html` bằng trình duyệt. Dữ liệu mẫu sẽ được nạp lần đầu và các thay đổi sẽ lưu trong trình duyệt hiện tại.

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
