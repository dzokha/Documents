# Laboratory 2 - LAN CONNECTION AND DATA SHARING
## 1. Thiết lập IP cho VPC trong GNS3
```
# show ip
# ip 192.168.1.1/24 192.168.1.1
```
## 2. Thiết lập Interface  Router
```
R1# configure terminal
R1(config)# interface FastEthernet 0/0
R1(config-if)# ip add 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# exit
R1(config-)#end
R1#write memory
```
### 3. Cấu hình định tuyến giữa 2 router
```
/* Router 1 */
R1#configure terminal
R1(config)# ip route 192.168.2.0 255.255.255.0 192.168.1.254
/* Router 2 */
R2#configure terminal
R2(config)# ip route 192.168.1.0 255.255.255.0 192.168.1.1
```
