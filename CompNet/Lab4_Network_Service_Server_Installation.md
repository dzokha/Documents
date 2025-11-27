# Laboratory 4 - NETWORK SERVICE SERVER INSTALLATION
## 1. Hệ điều hành
Hệ điều hành là phần mềm cho phép người dùng chạy các ứng dụng khác trên thiết bị máy tính và điện thoại thông minh. Hệ điều hành quản lý tài nguyên phần cứng và phần mềm của máy tính. Các Hệ điều hành, gồm: Android, iOS, MacOS, Windows và Linux.

Hệ điều hành Ubuntu Server là một phiên bản của Hệ điều hành Ubuntu được thiết kế và chế tạo làm xương sống cho Internet. Ubuntu Server mang lại khả năng mở rộng kinh tế và kỹ thuật cho trung tâm dữ liệu của bạn, công khai hoặc riêng tư. Cho dù bạn muốn triển khai đám mây OpenStack, cụm Kubernetes hay cụm kết xuất 50.000 nút, Ubuntu Server đều mang lại hiệu suất mở rộng quy mô có giá trị tốt nhất hiện có.

Download Ubuntu Server :https://ubuntu.com/download/server

Cài đặt giao diện đồ hoạ người dùng (GUI) trên Ubuntu Server
```
$sudo apt-get update && sudo apt upgrade
$sudo apt-get install slim
$sudo apt-get install ubuntu-desktop
$sudo reboot
```
## 2. Máy chủ Web 
Máy chủ web là phần mềm máy tính và phần cứng cơ bản chấp nhận các yêu cầu (Request) qua HTTP/HTTPS. Tác nhân người dùng, thường là trình duyệt web hoặc trình thu thập dữ liệu web , bắt đầu giao tiếp bằng cách đưa ra Request về một trang web hoặc tài nguyên khác bằng HTTP và máy chủ sẽ phản hồi (Response) bằng nội dung của tài nguyên đó hoặc thông báo lỗi . Máy chủ web cũng có thể chấp nhận và lưu trữ tài nguyên được gửi từ tác nhân người dùng nếu được định cấu hình. 

Có nhiều Web Server khác nhau như: Apache, Nginx, IIS, GWS, OpenResty, Cloudflare Server. Apache HTTP Server ("httpd") được ra mắt vào năm 1995 và nó là máy chủ web phổ biến nhất trên Internet kể từ tháng 4 năm 1996. Nó đã kỷ niệm sinh nhật lần thứ 25 với tư cách là một dự án vào tháng 2 năm 2020. Apache HTTP Server là phần mềm Web Server đa nền tảng miễn phí và mã nguồn mở, được phát hành theo các điều khoản của Giấy phép Apache 2.0. Nó được phát triển và duy trì bởi một cộng đồng các nhà phát triển dưới sự bảo trợ của Quỹ phần mềm Apache.

Để cài ứng dụng Web trên Web Server, chúng ta cần cài các Web Server tương ứng. Để cài Web Server phục vụ ngôn ngữ PHP, chúng ta cần cài các ứng dụng sau: Apache, MySQL, PHP. Tuy nhiên, các ứng dụng này đã được tích hợp trong WAMP (Windows), MAMP (MacOS), LAMP(Linux) và XAMPP(đa nền tảng) giúp cài đặt trở nên dễ dàng hơn.

Download XAMPP: https://www.apachefriends.org/download.html





