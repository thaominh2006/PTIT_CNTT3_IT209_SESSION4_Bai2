# Báo cáo Bài 2: Quản lý nhánh và giải quyết xung đột

Sinh viên: (Họ tên) - Mã SV: B24DTCN140 - Lớp: HN-KS24-CNTT3

## Các bước thực hiện

1. Khởi tạo repo bằng `git init -b main`, tạo README.md và commit đầu tiên trên main (41fb998).
2. Tạo nhánh bằng `git checkout -b feature-update`, sửa dòng "Mo ta" và commit (a47a1e7).
3. Quay lại main bằng `git checkout main`, sửa chính dòng "Mo ta" đó theo nội dung khác và commit (1256427).
4. Chạy `git merge feature-update`, Git báo CONFLICT trong README.md vì hai nhánh cùng sửa một dòng.
5. Mở README.md, xác định ba ký hiệu: `<<<<<<< HEAD` (nội dung main), `=======` (ngăn cách), `>>>>>>> feature-update` (nội dung nhánh phụ).
6. Giải quyết thủ công: xóa 5 dòng (3 dòng ký hiệu và 2 dòng "Mo ta" cũ), viết một dòng mới kết hợp ý của cả hai phiên bản.
7. Kiểm tra bằng `Select-String` để chắc chắn không còn ký hiệu xung đột.
8. Chạy `git add README.md` và `git commit` để tạo merge commit (51c8980).
9. Chạy `git log --graph --oneline` để xác nhận đồ thị nhánh (ảnh đính kèm).

## Cơ chế gộp 3 vùng (3-Way Merge)

Git so sánh ba điểm: commit tổ tiên chung (41fb998), đầu nhánh main (1256427) và đầu nhánh feature-update (a47a1e7).
- Nếu chỉ một bên thay đổi một vùng so với base, Git tự động lấy thay đổi đó.
- Nếu cả hai bên cùng sửa một vùng theo cách khác nhau, Git không tự quyết định được và đánh dấu xung đột để người dùng xử lý.

Dòng "Mo ta" bị cả hai nhánh sửa khác nhau so với base nên phát sinh xung đột.

## Kết quả

Merge commit 51c8980 có hai commit cha. Đồ thị cho thấy feature-update tách ra từ main rồi gộp lại.

![git log graph](git-log-graph.png)