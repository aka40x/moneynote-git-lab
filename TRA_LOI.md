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