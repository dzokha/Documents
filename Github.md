# Github.com
## Đăng ký tài khoản với Github.com
- Đăng ký tài khoản GitHub: [https://github.com/signup](https://github.com/signup)
- Tạo Token này dùng để thay thế mật khẩu khi bạn muốn đẩy (push) mã nguồn từ máy tính lên GitHub: [https://github.com/settings/tokens/new](https://github.com/settings/tokens/new)
- Lưu token lại để dùng nhiều lần: Sau khi tạo xong, hãy sao chép và lưu token vào nơi an toàn, vì GitHub sẽ không hiển thị lại token sau khi đóng trang.
## Tải và cài đặt Git
- Step 1: Tải và cài đặt Git: [https://git-scm.com/downloads](https://git-scm.com/downloads)
- Step 2: Gửi địa chỉ mail đăng ký github.com cho giảng viên để được mời làm cộng tác viên trên Repository
- Step 3: Truy cập kho Repository để theo dõi nộp bài thực hành
## Sao chép và đẩy mã nguồn lên kho lưu trữ
- Step 1: Mở Command Prompt hoặc CMD trên Windows
- Step 2: Thực hiện câu lệnh clone Repository: `git clone https://github.com/dzokha/<name_repository>.git`
- Step 3: Di chuyển vào thư mục Repository: `cd <name_repository>`
- Step 4: Chuyển nhánh: `git checkout student`
- Step 5: Tạo tập tin Word đặt tên là MSSV lưu trong thư mục <name_repository>, tập tin này sẻ lưu trữ kết quả mỗi buổi thực hành.
- Step 6: Chụp hình kết quả thực hành từng bài tập và dán vào tập tin Word
- Step 7: Nộp tập tin Word sau buổi thực hành lên kho <name_repository> bằng các câu lệnh
  ```
  git add .  
  git commit -m "<ghi chú>"  
  git push
  ```
## Các câu lệnh khác trong Github
- Đồng bộ từ Github về máy tính: `git pull`
- Liên kết thư mục với repo muốn đưa Source Code lên: `git remote add origin https://github.com/dzokha/<name_repository>.git`
- Liệt kê các liên kết đang sử dung: `git remote -v`
- Liệt kê thiết lập: `git config -l`
- Thiết lập tài khoản Github: `git config user.name <user_github>`
- Thiết lập email đã đăng ký trên Github: `git config user.email <mail_user_github>`
- Lựa chọn trình soạn thảo mặc định: `git config --global core.editor vi`
- Đổi tên nhánh hiện tại thành <name_branch>: `git branch -M <name_branch>`
- Chuyển sang nhánh <name_branch>: `git checkout <name_branch>`
- Giữ bản ở nhánh hiện tại  `git checkout --ours <file_conflict> `
- Giữ bản ở nhánh merge  `git checkout --theirs <file_conflict> `
- Tăng giới hạn kích thước buffer khi đẩy (push) dữ liệu qua HTTP lên GitHub: `git config http.postBuffer 52428800`
