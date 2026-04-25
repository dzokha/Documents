# Laboratory 2 - LAN CONNECTION AND DATA SHARING
## 1. Thiết lập IP cho VPCS trong GNS3
Câu lệnh thiết lập đị chỉ ip
```
#ip 192.168.1.2/24 192.168.1.1
/* Hoặc */
#ip dhcp
```
Câu lệnh thiết lập DNS
```
#ip dns 8.8.8.8
```
Các lệnh cơ bản khác
```
#show ip
#save
#clear ip
```
## 2. Thiết lập Interface  Router
Sử dụng Router C7200 để kết nối mạng LAN với nhau. Cách thiết lập:
1. Tải c7200-adventerprisek9-mz.124-24.T5.image
2. Vào GNS3 -> Edit -> Reference... -> Dynamips -> IOS Router
3. Vào chọn New và chọn đường dẫn dến file image vừa tải  thực hiện các lệnh tiếp theo 
```
R1#configure terminal
R1(config)#interface FastEthernet 0/0
R1(config-if)#ip add 192.168.1.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config-)#end
R1#write memory
```
## 3. Cấu hình định tuyến giữa 2 Router
```
/* Router 1 */
R1#configure terminal
R1(config)#ip route 192.168.2.0 255.255.255.0 192.168.1.254
/* Router 2 */
R2#configure terminal
R2(config)#ip route 192.168.1.0 255.255.255.0 192.168.1.1
```
## 4. Câu lệnh kiểm tra IP trên Router 
```
R1#show ip interface brief
R1#show ip router
```
