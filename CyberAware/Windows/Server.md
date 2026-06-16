# regedit
Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

# Office
Key Management Service (KMS) Activator Office

1. Thực hiện CMD trong đường dẫn sau với quyền Administrator:

- C:\Program Files (x86)\Microsoft Office\Office14\
- C:\Program Files\Microsoft Office\Office14\

2. Các lệnh cơ bản
```
cscript //nologo ospp.vbs /dstatus        REM Kiểm tra trạng thái bản quyền Office
cscript //nologo ospp.vbs /remhst         REM Lệnh CMD làm sạch dấu vết KMS trái phép
cscript //nologo ospp.vbs /unpkey:B9HB6   REM Gỡ 5 ký tự cuối của các product key đã cài
```
3. Kích hoạt Server bên ngoài

**Lưu ý:** 
- Key sưu tầm trên Internet: 2KKDC-67TT9-4XT2F-2MG99-B9HB6
- Server kms8.MSGuides.com chưa kiểm chứng, có nguy cơ đính kèm Malware
```
cscript //nologo ospp.vbs /inpkey:2KKDC-67TT9-4XT2F-2MG99-B9HB6
cscript //nologo ospp.vbs /sethst:kms8.MSGuides.com
cscript //nologo ospp.vbs /act
```
# Windows
1. Các câu lệnh cơ bản
```
slmgr /dli     REM Hiển thị thông tin cơ bản
slmgr /dlv     REM Hiển thị chi tiết đầy đủ
slmgr /xpr     REM Kiểm tra: Windows đã kích hoạt
slmgr /ckms    REM Xóa cấu hình KMS server
slmgr /cpky    REM Xóa product key khỏi Windows Registry
slmgr /upk     REM Gỡ product key khỏi hệ thống
slmgr /rearm   REM Reset thời gian đánh giá (grace period) của Windows
```
2. Yêu cầu Windows kích hoạt theo cấu hình

**Lưu ý:** 
- Key sưu tầm trên Internet: W269N-WFGWX-YVC9B-4J6C9-T83GX
- Server kms8.MSGuides.com chưa kiểm chứng, có nguy cơ đính kèm Malware
```
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX    REM Cài product key
slmgr /skms kms8.MSGuides.com               REM Trỏ đến KMS server
slmgr /ato                                  REM Yêu cầu Windows kích hoạt
```
3. Cài license từ file
```
slmgr /ilc <license_file>   REM file .xrm-ms
```
4. Các câu lệnh liên quan dịch vụ Windows
```
sc config LicenseManager start= auto & net start LicenseManager
sc config wuauserv start= auto & net start wuauserv
```
5. Thay đổi product key
```
changepk.exe /productkey VK7JG-NPHTM-C97JM-9MPGT-3V66T 
exit
```
6. Chuyển edition
```
Dism /Online /Get-TargetEditions
```
7. Thư mục chứa License token
```
C:\Windows\System32\spp\tokens\skus
```
8. Lấy key OEM channel
```
(Get-CimInstance -ClassName SoftwareLicensingService).OA3xOriginalProductKey
hoặc
Get-WmiObject -Class SoftwareLicensingService | Select-Object -ExpandProperty OA3xOriginalProductKey
```


# Các Server công khai
**LƯU Ý:** Chưa kiểm chứng, có nguy cơ nguy hiểm
1. kms8.msguides.com
2. kms.xspace.in
3. kms.digiboy.ir
4. kms.chinancce.com

## Key Windows 11
```
- Pro
    X3W8N-3WQCV-2MXDF-K77MK-7XMP6
- Education
    NW6C2-QMPVW-D7KKK-3GKT6-VCFB2
    YNMGQ-8RYV3-4PGQ3-C8XTP-7CFBY
- Enterprise
    NPPR9-FWDCX-D2C8J-H872K-2YT43
    XGVPP-NMH47-7TTHJ-W3FW7-8HV2C
- Home
    YTMG3-N6DKC-DKB77-7M9GH-8HVX7
- Home SL
    BT79Q-G7N6G-PGBYW-4YWX6-6F4BT
- Pro Edu
    8PTT6-RNW4C-6V7J2-C2D3X-MHBPB
```




User Windows
net user

net user name /add

net localgroup administrators name /add

net user dzokh /delete
