Câu 1: feature/giao-dien-moi, feature/tieu-de, feature/xuat-csv, hotfix/sua-loi-cong
Câu 2: 7
Câu 3: Lê Hùng
Câu 4: 
    git diff: Hiển thị những thay đổi chưa được đưa vào Staging Area (chưa git add)
    git diff --staged: Hiển thị những thay đổi đã được đưa vào Staging Area (đã git add), nhưng chưa git commit
    Vì file .env thường chứa thông tin nhạy cảm như:
    - Mật khẩu database.
    - API Key, Secret Key.
    - JWT Secret.
    - Thông tin tài khoản và cấu hình riêng của môi trường.
    Nếu đưa lên Git, người khác có thể truy cập và lợi dụng những thông tin này
Câu 5: 
    3.1, main không có commit nào mới nên commit nằm thẳng ở dưới main và git dời con trỏ main lên fast forward
    3.2, main và feature/giao-dien-moi ở 2 hướng khác nhau nên phải merge commit
Câu 6: 
    feature/giao-dien-moi chỉ sửa những dòng mà main không đụng tới, nên Git tự ghép được. feature/tieu-de sửa đúng dòng <h1> trong index.html, trong khi nhánh của Hùng (đã gộp vào main) cũng đã đổi dòng đó thành nội dung khác. Cùng một dòng, hai nội dung khác nhau thì Git không biết chọn bên nào, nên báo xung đột
Câu 7