# Laboratory 1 - INTRODUCTION TO NETWORK DEVICES
## 1. Cáp dây xoắn đôi (Twisted-pair)
Cáp xoắn đôi có hai loại: loại có vỏ bọc STP (Shielded Twisted Pair) hoặc loại  không được che chắn UTP (Unshielded Twisted  Pair).
### 1.1. STP
![Model](Images/STP.png)
### 1.2. UTP
![Model](Images/UTP.png)
### 1.3. RJ-45 và RJ-11
![Model](Images/RJ-45.png)
### 1.4.  Tiêu chuẩn cáp xoắn đôi

| Tiêu chuẩn (Category) | Tần số tối đa (MHz) | Tốc độ truyền dẫn tối đa (Mbps/Gbps) | Ứng dụng phổ biến | Lưu ý quan trọng |
| :--- | :--- | :--- | :--- | :--- |
| **CAT 5** | 100 MHz | 100 Mbps | Mạng Ethernet 100BASE-TX (Fast Ethernet) | Đã lỗi thời, ít được sử dụng trong các hệ thống mới. |
| **CAT 5e** | 100 MHz | 1 Gbps (1000 Mbps) | Mạng Gigabit Ethernet 1000BASE-T | Tiêu chuẩn tối thiểu phổ biến nhất hiện nay cho mạng gia đình và văn phòng nhỏ. |
| **CAT 6** | 250 MHz | 1 Gbps (ở 100m); **10 Gbps** (ở 37-55m) | Mạng Gigabit Ethernet và 10 Gigabit Ethernet (10GBASE-T) ở khoảng cách ngắn. | Dùng lõi chữ thập (spline) để giảm nhiễu xuyên âm (crosstalk). |
| **CAT 6a** | 500 MHz | **10 Gbps** (ở 100m) | Mạng 10 Gigabit Ethernet (10GBASE-T) trên toàn bộ khoảng cách (100m). | Chữ 'a' (Augmented) nghĩa là "nâng cao", giảm đáng kể nhiễu xuyên âm. |
| **CAT 7** | 600 MHz | 10 Gbps; Hỗ trợ lên đến 40 Gbps/100 Gbps (ở khoảng cách rất ngắn) | Trung tâm dữ liệu (Data Center), cáp bảo vệ (Shielded - STP) cao cấp. | Thường yêu cầu đầu nối không phải RJ45 tiêu chuẩn. |
| **CAT 8** | 2000 MHz | **25 Gbps hoặc 40 Gbps** (ở 30m) | Trung tâm dữ liệu, kết nối máy chủ/thiết bị chuyển mạch hiệu suất cực cao. | Chỉ dành cho kết nối khoảng cách ngắn; là cáp được bảo vệ (Shielded). |

### 1.5. Tiêu chuẩn đấu nối cáp mạng Ethernet

Trong hệ thống mạng Ethernet sử dụng đầu nối RJ45, hai tiêu chuẩn đấu nối phổ biến hiện nay là T568A và T568B.
- Tiêu chuẩn T568A: Được sử dụng trong một số hệ thống mạng theo tiêu chuẩn Bắc Mỹ hoặc các hệ thống được triển khai từ trước.
- Tiêu chuẩn T568B: Là tiêu chuẩn được sử dụng phổ biến trong các hệ thống mạng dân dụng, văn phòng và doanh nghiệp tại Việt Nam hiện nay.
  
![Model](Images/rj45.png)

#### Cáp thẳng (Straight-through Cable)

Cáp thẳng được tạo bằng cách đấu nối hai đầu cáp theo cùng một tiêu chuẩn (T568A – T568A hoặc T568B – T568B).

#### Ứng dụng:

Kết nối máy tính với switch.
Kết nối switch với router.
Kết nối máy tính, máy in mạng, camera IP với thiết bị mạng trung tâm.
Kết nối các thiết bị mạng khác loại với nhau.
Cáp chéo (Crossover Cable)

#### Cáp chéo được tạo bằng cách đấu nối một đầu theo chuẩn T568A và đầu còn lại theo chuẩn T568B.

#### Ứng dụng:

Kết nối trực tiếp giữa hai máy tính.
Kết nối switch với switch (đối với các thiết bị không hỗ trợ Auto MDI/MDIX).
Kết nối router với router hoặc các thiết bị mạng cùng loại.

Lưu ý: Các thiết bị mạng hiện đại hầu hết đã hỗ trợ công nghệ Auto MDI/MDIX, cho phép tự động nhận dạng kiểu kết nối, do đó trong nhiều trường hợp cáp thẳng có thể thay thế cáp chéo.
### 1.6. Kiềm bấm mạng 
Kìm bấm mạng là dụng cụ chuyên dụng dùng để:

Cắt dây cáp mạng.
Tuốt vỏ cáp.
Ép đầu nối RJ45 vào dây mạng theo đúng tiêu chuẩn kỹ thuật.

Việc sử dụng kìm bấm chuyên dụng giúp đảm bảo chất lượng tiếp xúc giữa các chân tiếp điểm và lõi dây, hạn chế suy hao tín hiệu trong quá trình truyền dẫn.

![Model](Images/kiem.png)

### 1.7. Tiêu chuẩn hoàn thiện hệ thống cáp mạng

Sau khi thi công, hệ thống cáp mạng cần đáp ứng các yêu cầu sau:

Đầu nối RJ45 được bấm đúng tiêu chuẩn T568A hoặc T568B.
Các dây dẫn được sắp xếp gọn gàng, cố định chắc chắn.
Cáp mạng được đi trong máng cáp, ống luồn hoặc nẹp bảo vệ phù hợp.
Có nhãn nhận dạng tại các điểm đấu nối để thuận tiện cho công tác quản lý và bảo trì.
Kiểm tra thông mạch và chất lượng tín hiệu bằng thiết bị test cáp trước khi đưa vào sử dụng.

![Model](Images/stand.jpg)
## 2. Công nghệ không dây

Công nghệ mạng không dây cho phép các thiết bị kết nối và trao đổi dữ liệu thông qua sóng vô tuyến mà không cần sử dụng cáp mạng vật lý. Hiện nay, công nghệ Wi-Fi là giải pháp mạng không dây được sử dụng phổ biến trong gia đình, cơ quan và doanh nghiệp.
