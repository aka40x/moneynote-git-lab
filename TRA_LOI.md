# TRẢ LỜI BÀI THỰC HÀNH GIT – MONEYNOTE LITE

## Câu 1
Nhánh `main` lúc mới nhận có **9 commit** (từ `dbf181e` đến `9be76b1`).

4 nhánh còn lại:
- `feature/giao-dien-moi`
- `feature/tieu-de`
- `feature/xuat-csv`
- `hotfix/sua-loi-cong`

## Câu 2
Bạn Lan có **7 commit** trong toàn bộ repo (đếm bằng `git log --all --author="Lan" --oneline`).

## Câu 3
Dòng có `reduce` trong `js/tinh-toan.js` do **Lê Hùng** viết, ở commit `df17ab7` ("Thêm bộ lọc thu/chi").

## Câu 4
- `git diff`: hiển thị các thay đổi **chưa** được đưa vào vùng chờ (staging), tức là chưa `git add`.
- `git diff --staged`: hiển thị các thay đổi **đã** `git add` nhưng chưa `git commit`, tức là nội dung sẽ nằm trong commit tiếp theo.
- File `.env` không nên đưa lên Git vì thường chứa thông tin nhạy cảm:
  - Mật khẩu database.
  - API key, secret key.
  - JWT secret.
  - Cấu hình riêng của từng môi trường.

  Nếu đã commit và push, người khác có thể đọc và lợi dụng. Git lưu toàn bộ lịch sử nên xóa file sau đó vẫn còn dấu vết trong các commit cũ.

## Câu 5
- 3.1: `main` không có commit mới nào kể từ lúc tách nhánh, nên commit của em nằm thẳng phía trước `main`. Git chỉ cần dời con trỏ `main` lên (fast-forward).
- 3.2: `main` và `feature/giao-dien-moi` đã đi theo hai hướng khác nhau từ tổ tiên chung, nên Git phải tạo một merge commit có hai commit cha để nối lại.

## Câu 6
- `feature/giao-dien-moi` chỉ sửa những dòng mà `main` không đụng tới, nên Git tự ghép được, không xung đột.
- `feature/tieu-de` sửa đúng dòng `<h1>` trong `index.html`, trong khi nhánh của Hùng (đã gộp vào `main`) cũng đã đổi dòng đó thành nội dung khác. Cùng một dòng, hai nội dung khác nhau thì Git không biết chọn bên nào nên báo xung đột.

## Câu 7
- `git revert` tạo một commit mới đảo ngược thay đổi của commit cũ, không viết lại lịch sử, nên an toàn với nhánh chung mà đồng đội đã kéo về. Họ chỉ cần `pull` là nhận được bản sửa.
- `git reset` xóa commit khỏi lịch sử. Nếu commit đã được push thì phải force push, khiến lịch sử trên máy đồng đội lệch so với remote, dễ gây xung đột hoặc mất công việc của họ.

## Câu 8
- `reset --soft`: chỉ dời con trỏ nhánh. Staging và thư mục làm việc giữ nguyên, thay đổi của commit bị bỏ vẫn nằm trong staging, sẵn sàng commit lại.
- `reset --mixed` (mặc định): dời con trỏ và làm trống staging. Thay đổi vẫn còn trong thư mục làm việc nhưng ở trạng thái chưa add.
- `reset --hard`: dời con trỏ, làm trống staging và ghi đè thư mục làm việc. Mọi thay đổi chưa commit bị xóa. Commit đã mất có thể cứu bằng `git reflog`, còn thay đổi chưa commit thì mất hẳn.

## Câu 9
Commit gây lỗi là `df17ab7`, thông điệp "Thêm bộ lọc thu/chi", tác giả Lê Hùng.

Trong `js/tinh-toan.js`, hàm `tinhTong` dùng `reduce` với giá trị khởi tạo là chuỗi rỗng `''` thay vì `0`. Khi đó `'' + 5000000` cho ra chuỗi, nên các số bị nối chuỗi thay vì cộng, tổng thu thành "10000050000".

## Câu 10
- Nếu dùng `git merge hotfix/sua-loi-cong`, Git gộp **toàn bộ** các commit của nhánh, kể cả commit thử font Comic Sans chưa được duyệt. Kết quả là font chữ của `main` bị đổi theo ý không mong muốn.
- `git cherry-pick` chỉ lấy đúng commit được chỉ định (`b5056bb`, sửa lỗi `reduce`), bỏ qua commit Comic Sans.

## Câu 11
- Không. Sau rebase, commit "Thêm hàm xuất CSV" có mã mới. Mã commit được tính từ nội dung, tác giả, thời gian và cả commit cha. Rebase đặt commit lên nền mới (đầu `main`) nên commit cha đổi, Git tạo commit mới có nội dung tương tự nhưng mã khác.
- Không nên rebase nhánh mà bạn khác đã kéo về vì rebase viết lại lịch sử. Máy đồng đội còn commit cũ, remote (sau force push) có commit mới, hai bên lệch nhau, dễ gây xung đột, commit trùng lặp hoặc mất công việc.

## Câu 12
- `git fetch`: chỉ tải dữ liệu mới từ remote về máy (cập nhật các nhánh `origin/...`), không thay đổi nhánh hiện tại hay file đang làm.
- `git pull`: bằng `git fetch` rồi tự động `merge` vào nhánh hiện tại, nên code trên máy thay đổi theo.