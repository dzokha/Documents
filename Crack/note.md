# Key Management Service (KMS) Activator Office

## Thực hiện CMD trong đường dẫn sau với quyền Administrator:

- C:\Program Files (x86)\Microsoft Office\Office14\
- C:\Program Files\Microsoft Office\Office14\
## Kiểm tra trạng thái bản quyền Office
```
cscript //nologo ospp.vbs /dstatus
```
## Gỡ 5 ký tự cuối của các product key đã cài
```
cscript //nologo ospp.vbs /unpkey:B9HB6
```
## Lệnh CMD làm sạch dấu vết KMS trái phép
```
cscript //nologo ospp.vbs /remhst
```
## Kích hoạt Server bên ngoài
```
cscript //nologo ospp.vbs /inpkey:2KKDC-67TT9-4XT2F-2MG99-B9HB6
cscript //nologo ospp.vbs /sethst:kms8.MSGuides.com
cscript //nologo ospp.vbs /act
```
## Các Server tham khảo
Lưu ý là có thể nguy hiểm, có thể dính Malware

- kms.digiboy.ir
- kms8.MSGuides.com
- kms.chinancce.com
