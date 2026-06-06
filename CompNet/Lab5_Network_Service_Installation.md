# Laboratory 5 - Network Service Installation
## 1. Framework ứng dụng Web
Framework ứng dụng web là Framework phần mềm được thiết kế để hỗ trợ phát triển các ứng dụng web bao gồm dịch vụ web, tài nguyên web và API web. Các khung web cung cấp một cách tiêu chuẩn để xây dựng và triển khai các ứng dụng web trên World Wide Web. Các Framework phổ biến:
- Django mã nguồn mở và miễn phí được viết bằng Python.
- Laravel mã nguồn mở và miễn phí được viết bằng PHP.
- Spring Boot là một khung Java mã nguồn mở được sử dụng để lập trình các ứng dụng dựa trên Spring. Spring Boot là một tiện ích mở rộng cấu hình theo quy ước dành cho nền tảng Spring Java nhằm giúp giảm thiểu những lo ngại về cấu hình trong khi tạo các ứng dụng dựa trên Spring.

### a) Tạo ứng dụng web cơ bản với 3 framework
- Django: https://www.djangoproject.com/
- Laravel: https://laravel.com/
- Spring Boot: https://spring.io/
### b) Kích hoạt giao thức HTTPS với Apache 2
```
$sudo a2enmod ssl
$sudo systemctl restart apache2

$sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/server.yourdomain.com.key -out /etc/ssl/certs/server.yourdomain.com.crt

$sudo cp -a /etc/apache2/sites-available/yourdomain.com{.conf,-ssl.conf}
$sudo nano /etc/apache2/sites-available/yourdomain.com-ssl.conf

<VirtualHost *:80> 
<VirtualHost *:443>
SSLEngine on
SSLCertificateKeyFile /etc/ssl/private/server.yourdomain.com.key
SSLCertificateFile /etc/ssl/certs/server.yourdomain.com.crt

$sudo a2ensite yourdomain.com-ssl.conf
$sudo apache2ctl -t
$sudo systemctl restart apache2
```
## 2. FTP server
Vsftpd là FTP Server được cấp phép GPL cho các hệ thống UNIX, bao gồm cả Linux. Nó an toàn và cực kỳ nhanh chóng. Nó ổn định là một giải pháp hoàn thiện và đáng tin cậy.
Cài đặt vsftpd trên Ubuntu Server
```
$sudo apt-get update
$sudo apt-get install vsftpd
```
Cho phép Ftp giao tiếp qua tường lửa
```
$sudo ufw allow 20/tcp
$sudo ufw allow 21/tcp
$sudo ufw allow 990/tcp
$sudo ufw allow 40000:50000/tcp
$sudo ufw status
```
Tạo thư mục người dùng
```
$sudo adduser alex
$sudo mkdir /home/alex/ftp
$sudo chown nobody:nogroup /home/alex/ftp
$sudo chmod a-w /home/alex/ftp
$sudo ls -la /home/alex/ftp
$sudo mkdir /home/alex/ftp/files
$sudo chown alex:alex /home/alex/ftp/files
```
Cấu hình vsftpd
```
$sudo nano /etc/vsftpd.conf

anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES

user_sub_token=$USER
local_root=/home/$USER/ftp

pasv_min_port=40000
pasv_max_port=50000

userlist_enable=YES
userlist_file=/etc/vsftpd.userlist

userlist_deny=NO

$echo "alex" | sudo tee -a /etc/vsftpd.userlist
$cat /etc/vsftpd.userlist
$sudo systemctl restart vsftpd
```
Bảo mật Ftp
```
$sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem

$sudo nano /etc/vsftpd.conf

## rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
## rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem

ssl_enable=YES

allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

require_ssl_reuse=NO
ssl_ciphers=HIGH

$sudo systemctl restart vsftpd
```
### Kiểm tra FTP Server và thực hành gửi/nhận tệp

#### a) Kiểm tra trạng thái dịch vụ FTP

Kiểm tra dịch vụ vsftpd đang hoạt động:

```bash
$sudo systemctl status vsftpd
```

Kiểm tra cổng FTP đang lắng nghe:

```bash
$sudo ss -tulnp | grep vsftpd
```

Kết quả mong đợi hiển thị các cổng:

```text
21/tcp
40000-50000/tcp
```

#### b) Kiểm tra kết nối FTP từ máy khách

Từ máy khách (Client) hoặc chính máy chủ:

```bash
$ftp 192.168.250.7
```

Hoặc:

```bash
$ftp localhost
```

Đăng nhập bằng tài khoản đã tạo:

```text
Name: alex
Password: ********
```

Sau khi đăng nhập thành công:

```text
230 Login successful.
ftp>
```

#### c) Thực hành tải tệp lên máy chủ FTP

Trên máy khách tạo tệp kiểm tra:

```bash
$echo "FTP Test File" > test.txt
```

Trong phiên làm việc FTP:

```bash
ftp> cd files
ftp> put test.txt
ftp> ls
```

Kết quả mong đợi:

```text
test.txt
```

Kiểm tra trên máy chủ:

```bash
$ls -la /home/alex/ftp/files
```

#### d) Thực hành tải tệp từ máy chủ FTP về máy khách

Tạo tệp trên máy chủ:

```bash
$echo "Download Test" > /home/alex/ftp/files/download.txt
```

Từ máy khách:

```bash
ftp> cd files
ftp> get download.txt
ftp> bye
```

Kiểm tra tệp đã được tải về:

```bash
$cat download.txt
```

Kết quả:

```text
Download Test
```

#### e) Kiểm tra FTP bảo mật (FTPS)

Cài đặt ứng dụng FileZilla trên máy khách.

Khai báo kết nối:

```text
Host: 192.168.250.7
Protocol: FTP
Encryption: Require explicit FTP over TLS
User: alex
Password: ********
```

Kết nối thành công sẽ xuất hiện thông báo:

```text
TLS connection established
Directory listing successful
```

Thực hiện kéo/thả một tệp bất kỳ từ máy khách lên thư mục:

```text
/home/alex/ftp/files
```

và tải ngược lại từ máy chủ về máy khách.

#### f) Kiểm tra nhật ký hoạt động FTP

Theo dõi các phiên đăng nhập và truyền tệp:

```bash
$sudo tail -f /var/log/vsftpd.log
```

Hoặc:

```bash
$sudo journalctl -u vsftpd -f
```

Các thông tin cần quan sát:

* Đăng nhập thành công/thất bại.
* Tải tệp lên máy chủ (UPLOAD).
* Tải tệp từ máy chủ (DOWNLOAD).
* Ngắt kết nối người dùng.

#### g) Yêu cầu thực hành

1. Đăng nhập FTP bằng tài khoản `alex`.
2. Tạo tệp `lab5.txt` trên máy khách.
3. Tải tệp `lab5.txt` lên thư mục `/home/alex/ftp/files`.
4. Tạo tệp `report.txt` trên máy chủ.
5. Tải tệp `report.txt` từ máy chủ về máy khách.
6. Chụp màn hình quá trình đăng nhập FTP và truyền tệp.
7. Nộp báo cáo gồm các lệnh đã thực hiện và kết quả kiểm tra.


## 3. Mail Server
Postfix là một máy chủ email được viết bằng C. Tính năng chính của nó là tốc độ thực thi và tính chất nguồn mở.
Định cấu hình Máy chủ DNS cho Máy chủ Thư Ubuntu:
```
$sudo apt-get update
$sudo apt install bind9
$sudo nano /var/cache/bind/db.test

$ORIGIN test.com.
$TTL 1D
@       IN SOA     ns1 root(
                1 ;serial
                1D ;refresh
                2H ;retry
                2W ;expire
                5H ;minimum
);
@       IN        NS ns1
ns1     IN        A 192.168.250.7
mail    IN        A 192.168.250.7
@       IN        MX 5 mail

$sudo named-checkzone test.com. /var/cache/bind/db.test
$sudo nano /etc/bind/named.conf.default-zones

zone "test.com." {
       type master;
       file "db.test";
};

$sudo nano /etc/bind/named.conf.options
$sudo systemctl reload bind9
```
Cài đặt máy chủ Email Postfix
```
$sudo apt install postfix
$sudo usermod -aG mail $(whoami)
$sudo useradd -m -G mail -s /bin/bash/ gabriel
$sudo passwd gabriel
```
Kiểm tra mail
```
$sudo apt install mailutils
$mail gabriel@test.com
$mail angelo@test.com
```

