# Laboratory 4 - NETWORK SERVICE SERVER INSTALLATION
## 1. Hệ điều hành
Hệ điều hành là phần mềm cho phép người dùng chạy các ứng dụng khác trên thiết bị máy tính và điện thoại thông minh. Hệ điều hành quản lý tài nguyên phần cứng và phần mềm của máy tính. Các Hệ điều hành, gồm: Android, iOS, MacOS, Windows và Linux.

Hệ điều hành Ubuntu Server là một phiên bản của Hệ điều hành Ubuntu được thiết kế và chế tạo làm xương sống cho Internet. Ubuntu Server mang lại khả năng mở rộng kinh tế và kỹ thuật cho trung tâm dữ liệu của bạn, công khai hoặc riêng tư. Cho dù bạn muốn triển khai đám mây OpenStack, cụm Kubernetes hay cụm kết xuất 50.000 nút, Ubuntu Server đều mang lại hiệu suất mở rộng quy mô có giá trị tốt nhất hiện có.

Download Ubuntu Server :https://ubuntu.com/download/server
### 1.1. Sử dụng VMware tạo máy ảo và cài Ubuntu Server
- Chọn File/Mew Virtual Machine
- Chọn Typical, Next
- Chọn I will install the operating system later
- Chọn Microsoft Windows, Chọn Version: Windows Server 2022, Next
- Đặt tên Virtual machine, nên đặt tên dễ nhớ để buổi sau thực hành, Chọn đường dẫn đến ổ D để lưu trữ, vì khi lưu vào ổ C máy khởi động sẻ mất, Next
- Chọn Maximum disk size 60GB, Chọn Split virtual disk into multipe files, Next
- Finish
- Click chuột phải vào tên Virtual Machine vừa đặt bên cửa sổ tay trái, Chọn Settings …
- Click vào CD/DVD (SATA), chọn Use ISO image file và click Brower… để dẫn đến file Ubuntu_Server.ISO vừa tải về, Nhấp vào Ok
- Click chuột phải vào tên Virtual Machine vừa tạo và bấm Powrer/Power On Hoặc có thể thực hiện bằng cách click vào nút tam giác màu xanh

LƯU Ý: 
- Nếu máy không báo lỗi thì qua B12. 
- Nếu máy tính báo lỗi “This host supports Intel VT-x, but Intel VT-x is disabled”. 
+ Khởi động lại máy tính,
+ Khi máy tính tắt, và bắt đầu bật màn hình đen thực hiện nhấp F2 liên tục để vào BIOS setting (hoặc phím khác theo hướng dẫn trên màn hình)
+ Sau khi vào BIOS Setting thực hiện các bước sau:
+ Vào Advanced Model/Advanced/CPU Configuration/Intel Virtualization Technology, thay đổi từ “Disabled” thành “Enabled” trong listbox bên tay phải.
+ Sau đó bấm F10 để lưu kết quả thiết lập
+ Bấm Ok để lưu và khởi động Windows
+ Mở VMware và khởi động lại Máy ảo vừa tạo ở B11.
khi vào màn hình đen, có hiển thị hàng chữ bấm phím bất kỳ để vào Setup, 
Lưu ý: nếu quên bấm phím bất kỳ thì sẻ vào màn hình màu xanh chọn “EFI VMware virtual CDROM”
Trog giao diện màn hình Setup bấm Next
Nhấp chuột vào Install now
Giao diện hiển thì 4 tuỳ chọn Windows Server các bạn chọn Windows Server 2022 Datacenter Evaluation (Desktop Experience), chọn Next
Chọn vào Checkbox “I accept the Microsoft….”, Next
Màn hình Which type of installation do you want?, chọn Custom: Install Micorsoft Server ….
Lưu ý: Bước này nếu chọn Upgrade thì khi cài máy thật có thể mất dữ liệu 
tại nước này chon New để tạo ổ đỉa mới, Chọn Apply, Chọn Ok, Chọn Next.
Lưu ý: Bước này nếu cài máy thật, đã có các phân vùng thì không thực hiện chọn New mà click vào phần vùng chứa hệ điều hành đã cài trước để cài đè lên hoặc xoá dữ liệu trước khi cài lên.
Đặt mật khẩu phải có ký tự hoa, ký tự thường, ký tự số và ký tự đặc biệt.
Trên thanh công cụ VMware vào VM/Send Ctrl + Alt + Del

```
### 1.2. Cài đặt giao diện đồ hoạ người dùng (GUI) trên Ubuntu Server
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





