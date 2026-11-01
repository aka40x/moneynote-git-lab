Câu 1: feature/giao-dien-moi, feature/tieu-de, feature/xuat-csv, hotfix/sua-loi-cong
Câu 2: 7
Câu 3: Lê Hùng
Câu 4: 
    - git diff: Hiển thị những thay đổi chưa được đưa vào Staging Area (chưa git add)
    - git diff --staged: Hiển thị những thay đổi đã được đưa vào Staging Area (đã git add), nhưng chưa git commit
    - Vì file .env thường chứa thông tin nhạy cảm như:
        + Mật khẩu database.
        + API Key, Secret Key.
        + JWT Secret.
        + Thông tin tài khoản và cấu hình riêng của môi trường.
        Nếu đưa lên Git, người khác có thể truy cập và lợi dụng những thông tin này
Câu 5: 
    - 3.1, main không có commit nào mới nên commit nằm thẳng ở dưới main và git dời con trỏ main lên fast forward
    - 3.2, main và feature/giao-dien-moi ở 2 hướng khác nhau nên phải merge commit
Câu 6: 
    - feature/giao-dien-moi chỉ sửa những dòng mà main không đụng tới, nên Git tự ghép được
    - feature/tieu-de sửa đúng dòng <h1> trong index.html, trong khi nhánh của Hùng (đã gộp vào main) cũng đã đổi dòng đó thành nội dung khác. Cùng một dòng, hai nội dung khác nhau thì Git không biết chọn bên nào, nên báo xung đột
Câu 7:
    - git revert tạo một commit mới đảo ngược thay đổi của commit cũ, không viết lại lịch sử, nên an toàn với nhánh chung mà đồng đội đã kéo về: họ chỉ cần pull là nhận được bản sửa
    - git reset thì xóa commit khỏi lịch sử; nếu commit đã được push, phải force push, khiến lịch sử trên máy đồng đội bị lệch so với remote và dễ gây xung đột hoặc mất công việc của họ
Câu 8: 
    - reset --soft: chỉ dời con trỏ nhánh. Vùng chờ (staging) và thư mục làm việc giữ nguyên, các thay đổi của commit bị bỏ vẫn nằm trong staging, sẵn sàng commit lại.
    - reset --mixed (mặc định): dời con trỏ và làm trống staging. Thay đổi vẫn còn trong thư mục làm việc nhưng ở trạng thái chưa add.
    - reset --hard: dời con trỏ, làm trống staging và ghi đè thư mục làm việc. Mọi thay đổi chưa commit bị xóa. Chỉ cứu được các commit đã mất bằng git reflog, còn thay đổi chưa commit thì mất hẳn.
Câu 9: 
    