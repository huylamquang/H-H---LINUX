# NETWORK
## Mô hình OSI và TCP/IP
### Mô hình OSI
- Mô hình OSI là 1 khung khái niệ chia các chức năng truyền thông mạng thành 7 lớp giữ các chức năng khác nhau
- Mục đích của việc sử dụng mô hình OSI: Cho chép 2 hệ thống độc lập giao tiếp với nhau thông qua các giao diện or giao thức được chuẩn hóa dựa trên lớp hoạt động hiện tại. Có thể sử dụng mô hình OSI để tổ chức và mô hình hóa các kiến trúc hệ thống kết nối phức tạp.
- Mô hình OSI gồm 7 lớp và các chức năng của các lớp:
  - Lớp vật lý: Là phương tiện truyền dẫn vật lý và các công nghệ để truyền dữ liệu qua phương tiện đó.
  - Lớp liên kết dữ liệu: Là các công nghệ được sử dụng để kết nối 2 máy trên 1 mạng nơi lớp vật lý đã tồn tại. Lớp này quản lý khung dữ liệu - Là các tín hiệu kỹ thuật số được gói gọn trong các gói dữ liệu. Kiểm soát lưu lượng và kiểm soát lỗi dữ liệu thường là trọng tâm chính của lớp liên kết dữ liệu. Gồm kiểm soát phương tiện MAC và điều khiên liên kết logic LLC.
  - Lớp mạng: Liên quan đến các khái niệm định tuyến chuyển tiếp và xác định địa chỉ trên 1 mạng phân tán hoặc nhiều mạng kết nối của nút hoặc máy. Tại đây cũng có thể kiểm soát lưu lượng. Ipv4 và Ipv6 đuọc sử dụng làm giao thức lớp mạng chính.
  - Lớp truyền tải: Đảm bảo rằng các gói dữ liệu đến đúng thứ tự, không bị mất mát, bị lỗi hoặc có thể phục hồi. 2 giao thức được sử dụng là TCP và UDP
  - Lớp phiên: Điều phối mạng giữa 2 ứng dụng riêng biệt trong 1 phiên. Tạo ra phiên quản lý kết nối ứng dụng 1-1 từ khi bắt đầu đến khi kết thúc và xung đột đồng bộ hóa. NFS và SMB là các giao thức được sử dụng. Cho phép người sử dụng trên các máy khác thiết lập, duy trì và đồng bộ phiên truyền thong giữa họ với nhau. Thiết lập "các giao dịch" giữa các thực thể đầu cuối.
  - Lớp ứng dụng: Liên quan đến loại ứng dụng cụ thể và các phương thức giao tiếp chuẩn hóa của nó. HTTPS và SMTP.
- Xác định giao diện giữa người sử dụng và môi trường OSI. Gồm nhiều giao thức cung cấp các phương tiện cho người sử dụng truy cập vào môi trường mạng và cung cấp các dịch vụ phân tán. Cần có sự liên kết tất cả các lớp và giao thức này lại với nhau, thông tin liên lạc dữ liệu phức tạp có thể được gửi từ ứng dụng cấp cao này sang ứng dụng cấp cao khác. Quy trình:
  - B1: Lớp ứng dụng của người gửi hoạt động truyền dữ liệu xuống tầng bên dưới
  - B2: Mỗi lớp đều thêm các tiêu đề và địa chỉ riêng của nó vào dữ liệu xuống tầng bên dưới
  - B3: Hoạt động truyền dữ liệu di chuyển xuống các lớp cho đến khi cuối cùng dữ liệu được truyền qua phuơng tiện vật lý
  - B4: Ở đầu kia của phương tiện, mỗi lớp xử lý dữ liệu theo các tiêu đề có liên quan ở cấp độ đó.
  - B5: Ở thiết bị nhận, dữ liệu di chuyển lên từng lớp và dần dần được giải nén cho đến khi ứng dụng ở đầu kia nhận được dữ liệu.
### Mô hình TCP/IP
- Mô hình TCP/IP là bộ các giao thức truyền thông được dùng để kết nối các thiết bị mạng trên internet với nhau. TCP/IP cũng có thể được dùng như 1 giao thức truyền thông trong mạng máy tính nội bộ. Với TCP và IP là 2 giao thức chính. Áp dụng mô hình Client/Server.
- Giao thức TCP: Có vai trò kiểm tra và đảm bảo an toàn cho từng gói tin khi chúng đi qua mỗi trạm. Khi giao thức TCP nhận thấy gói tin bị lỗi trong quá trình vận chuyển, 1 tín hiệu sẽ được phát ra và yêu cầu hệ thống máy chủ gửi lại 1 gói tin khác. TCP xác định cách các ứng dụng có thể tạo ra các kênh truyền dẫn thông qua mạng. TCP quản lý cách 1 tin nhắn được chia thành các packet nhỏ hơn trước khi truyền qua internet.
- Giao thức IP: Đảm bảo các gói được đi đến đúng địa chỉ đích. Mỗi gateway trên mạng sẽ kiểm tra địa chỉ IP này để xác định nơi chuyển tiếp. Các giao thức phổ biến của giao thức TCP/IP là HTTP, HTTPS, FTP, ...
- Mô hình TCP/IP gồm 4 tâng:
  - Tầng application(gồm tầng 7,6,5 của mô hinh OSI): Cung cấp cho các ứng dụng những trao đổi dữ liệu chuẩn hóa, giao tiếp dữ liệu giữa 2 máy khác nhau thông qua các dịch vụ mạng khác nhau. Gồm các giao thức trao đổi dữ liệu và hỗ trợ truyền tệp tin: HTTP, FRP, POP3, SMTP, SNMP, ... Dữ liệu trong tầng này là dữ liệu thực tế.
  - Tầng transport: Đảm bảo duy trì thông tin liên quan từ đầu cuối trên toàn mạng. Gồm giao thức TCP và UDP.
  - Tầng Network: Tầng này có nhiệm vụ xử lý các gói tin mạng và kết nối các mạng độc lập, giúp vận chuyển các gói tin qua mạng
  - Tầng vậy lý(gồm tầng 1 và 2 của mô hình OSI): Bao gồm các giao thức hoạt động trên 1 liên kết duy nhất - thành phần mạng kết nối các nút hoặc máy chủ trong mạng. Chịu trách nhiệm truyền dữ liệu giữa 2 thiết bị trong cùng 1 mạng. Giao thức truyền dữ liệu( Ethernet cho LAN) và ARP.
### So sánh mô hình OSI và TCP/IP
### Giao thức TCP và UDP
#### Giao thức TCP
- Là giao thức hướng kết nối tức là khi muốn truyền dữ liệu thì phải thiết lập kết nối trước
- Hỗ trợ cơ chế full-duplex( truyền và nhận dữ liệu cùng lúc)
- Cung cấp cơ chế đánh số thứ tự gói tin cho các đơn vị dữ liệu được truyền, sử dụng để sắp xếp các gói tin chính xác ở điểm nhận và loại bỏ gói tin trùng lặp.
- Phục hồi cơ chế báo nhận( ACK): Khi A gửi dữ liệu cho B, B nhận được thì gửi gói tin cho A xác nhận là đã nhận. Nếu không nhận được tin xác nhận thì A sẽ gửi cho đến khi B nhận được thì thôi.
- Phục hồi dữ liệu bị mất trên đường truyên( A gửi B mà không thấy xác nhận sẽ gửi lại)
- Có các cơ chế điều khiển luồng thích hợp( flow control) để tránh nghẽn xảy ra.
- Quá trình thiết lập kết nối( Bắt tay 3 bước):
  
  ![image](https://github.com/user-attachments/assets/1ce242ba-ffc4-41ef-bb71-1b3bfd398d52)
  
  - Server đang ở trạng thái lắng nghe và nó sẽ đợi 1 kết nối TCP từ 1 cổng kết nối từ xa.
  - B1: Máy A khởi tạo kết nối bằng cách gửi gói TCP SYN đến máy chủ. Gói chứa só thứ tự ngẫu nhiên đánh dấu sự bắt đầu của số thứ tự cho dữ liệu mà máy chủ A sẽ truyền. (Số X = ISN của client)
  - B2: Máy chủ nhận gối và phản hồi bằng số thứ tự của chính nó. Phản hồi cũng bao gồm số nhận( số thứ tự của máy chủ = Số ISN của server), là số thứ tự của máy A được tăng thêm 1.(ISN = Y, ACK = X +1)
  - B3: Máy A xác nhận phản hồi máy chủ bằng cách gửi số xác nhận, là số thứ tự của máy chủ và số thứ tự của máy chủ tăng thêm 1( ACK = Y +1)
  - Sau khi quá trình truyền dữ liệu hoàn thành, TCP sẽ ngắt kết nối giữa 2 máy chủ. Tức là 1 quá trình từ khi TCP được khởi tạo đến khi kết thúc sẽ có 4 bước:

    ![image](https://github.com/user-attachments/assets/f37ac5cf-ee78-4c88-a25c-927e25fc622a)

  - B1: Ứng dụng từ máy khách muốn đóng kết nối sẽ gửi segment TCP có cờ FIN(Finish) được đặt thành 1
  - B2: Máy chủ nhận được segment TCP và xác nhận nó bằng segment ACK. Tại thời điểm này thì chỉ ngắt kết nối tồn tại ở 1 chiều tại máy A( Tức là server vẫn có thể được gửi dữ liệu còn lại cho máy A).
  - B3: sau khi gửi hết tất cả dữ liệu máy chủ segment TCP của riêng nó với cờ FIN được đặt thành 1 cho máy khách để chấm dứt kết nối.
  - B4: Máy khách xác nhận segment FIN của máy chủ và gửi lại 1 gói tin ACK để xác nhận rằng kết nối hoàn toàn được ngắt - Lúc này cả 2 đều đóng kết nối.
#### Giao thức UDP
- Là giao thức truyền thông không kết nối( tức là không có quá trình thiết lập và duy trì kết nối giữa 2 thiết bị gửi và nhận dữ liệu).
- Được sử dụng để gửi các gói dữ liệu từ 1 thiết bị này đến 1 thiết bị khác qua mạng IP mà không cần thiết lập kết nối trước.
- Không đảm bảo tính toàn vẹn( Không cung cấp cơ chế kiểm tra và sửa lỗi nên các gói dữ liệu có thể bị mất, trùng lặp  hoặc không theo thứ tự)
- Không kiếm soát lưu lượng( Không có cơ chế kiểm soát lưu lượng giữa 2 thiết bị liên lạc).
- Đơn giản và nhanh
### Ipv4 và Ipv6, cách phân loại Ipv4
#### Cấu trúc và cách phân loại Ipv4
- Cấu trúc ipv4:
![image](https://github.com/user-attachments/assets/cd57e6f2-0c77-4b93-b396-551b41c45138)
  - Gồm 32 bit nhị phân được chia thành 4 cụm(octet). Gồm 2 phần: phần host và phần mạng
  - Địa chỉ ipv4 thành 5 lớp:
    - Lớp A: Dùng octet đầu tiên làm phần net, 3 octet sau làm phần host. Bit đầu tiên của octet đầu luôn là bit 0. Địa chỉ mạng lớp A: 1.0.0.0 -> 126.0.0.0 Mỗi mạng trong lớp A có 2^24 -2 host 
    - Lớp B: Dùng 2 octet đầu làm phần net, 2 octet sau làm phần host. 2 bit đầu tiên của octet đầu luôn là 1 và 0 nên phần mạng lớp B gồm 128.0.0.0 -> 192.255.0.0 Mỗi mạng trong lớp B có 2^16 -2 host
    - Lớp C: DÙng 3 octet đầu làm phần net, 1 octet sau làm phần host. 3 bit đầu tiên của octet đàu luôn là 110 nên phần mạng lớp C 192.0.0.0 -> 223.255.255.0 Mỗi mạng trong lớp C sẽ có 2^8 -2 host. 
    - Lớp D: Bao gồm các dải từ 224.0.0.0 -> 239.255.255.255 
    - Lớp E: Từ 240.0.0.0 trở đi -> sử dụng cho mục đích dự phòng
- Phân loại địa chỉ Ipv4:
  - Private: Sử dụng trong mạng nội bộ LAN. Không định tuyến trên môi trường internet. Sử dụng lặp đi lặp lại trong các mạng LAN khác nhau.
  - Public: Là địa chỉ IP sử dụng cho các gói tin đ trên môi trường Internet, được định tuyến trên môi trường internet, không sử dụng trong mạng LAN
  - Địa chỉ loopback: Được sử dụng để kiêm tra và quản lý mạng trên máy tính cục bộ. Địa chỉ loopback cho Ipv4 là 127.0.0.1 với mục đích là cho phép các ứng dung trên máy tính giao tiếp với nhau mà không cần kết nối mạng thực tế.
  - Địa chỉ quảng bá( broadcast address): Được sử dụng để gửi dữ liệu đến tất cả các thiết bị trong một mạng con. Khi 1 gói tin được gửi tới địa chỉ broadcast, nó sẽ được truyền đến mọi thiết bị trong mạng đó.
  - Địa chỉ nhóm( Multicast address): Được sử dụng để gửi dữ liệu đến 1 nhóm các thiết bị trong mạng, nhưng không gửi tới toàn bộ thiết bị như broadcast. Các thiết bị trong mạng có thể tham gia hoặc rời khởi 1 nhóm multicast tùy ý.
- Cách chia địa chỉ Ipv4:
#### Cấu trúc và phân loại Ipv6
- Cấu trúc Ipv6: Ipv6 dài 127 bit, được viết dưới dạng hexa. Cứ 4 bit nhị phân đổi thành 1 số hexa nên 1 địa chỉ Ipv6 sẽ gồm 32 số hexa. 32 số này được viết thành 8 cụm, mỗi cụm 4 số hexa, gọi là các trường.

  ![image](https://github.com/user-attachments/assets/3f4d233e-4f55-4693-94f8-6f8b43cc7708)

- Quy tắc:
  - Cho phép bỏ các số 0  nằm trước trong mỗi nhóm
  - Trong nhóm toàn số 0 ta có thể chỉ thay 1 số
  - Trong các nhóm liên tiếp có toàn số 0 có thể thay bằng dấu ::
  - Dấu :: chỉ được xuất hiện 1 lần
- Phân loại: Hiện nay địa chỉ Ipv6 được phân ra làm 3 loại:
  - Địa chỉ Unicast: Mỗi địa chỉ unicast xác định duy nhất 1 interface của 1 node Ipv6
  - Địa chỉ Multicast: Mỗi địa chỉ Multicast xác định nhiều interface của 1 node Ipv6
  - Địa chỉ Anycast: tương tự như Multicast nhưng khác về đích đến
## Switching
### Bonding
- Bonding là 1 kỹ thuật trong mạng máy tính cho phép kết hợp nhiều giao diện mạng thành 1 giao diện logic duy nhất để cải thiện hiệu suất và tăng cường khả năng dự phòng. Kỹ thuật này còn được gọi là NIC bonding hoặc link aggregation. Khi bonding được cấu hình, dữ liệu có thể truyền qua tất cả các giao diện mạng đã được kết hợp, giúp tăng băng thông và cung cấp khả năng chịu lỗi nếu 1 trong các giao diện gặp sự cố
- Việc sử dụng bonding là cần thiết vì:
  - Tăng băng thông: Bonding cho phép bạn kết hợp băng thông của nhiều cổng mạng, giúp tăng tốc độ truyền tải dữ liệu. Điều này hữu ích trong các hệ thống yêu cầu lưu lượng mạng lớn như máy chủ CSDL, hệ thống lưu trữ mạng NAS, hoặc các dịch vụ cần hiệu suất cao.
  - Dự phòng: Nếu 1 trong các giao diện mạng bị lỗi, giao diện khác trong nhóm bonding vẫn có thể duy trì kết nối mạng. Điều này giúp hệ thống tránh bị gián đoạn do sự cố với phần cứng mạng.
  - Tối ưu hóa tải: Bonding có thể được cấu hình để phân phối lưu lượng mạng qua nhiều cổng mạng, tối ưu hóa hiệu suất bằng cách tận dụng tài nguyên của nhiều đường truyền.
- Các chế độ bonding phổ biến:
  - Mode 0 : Balancep-rr : Áp dụng cơ chế Round-robin. Nó truyền các gói tin theo thứ tự tuần tự từ slave đầu tiên đến cuối cùng. Nếu có 2 interface thật và 2 gói tin đến, thì gối tin đầu tiên sẽ đi vào interface1 và gói tin thứ 2 sẽ đi vào interface2 : Có khả năng chịu lỗi : có khả năng cân bằng tải :
  - Mode 1 : active-backup : Áp dụng cơ chế Active-backup. Chế độ này đặt 1 trong các interface vào trạng thái backup và sẽ chỉ hoạt động nếu interface đang hoạt động bị lỗi. Chỉ có 1 slave hoạt động trong 1 thời điểm. Một slave khác nhau sẽ được kích hoạt chỉ khi slave đang hoạt động bị lỗi : Có khả năng chịu lỗi : Khoog có khả năng cân bằng tải :
  - Mode 2 : balance-xor  : Áp dụng phép XOR, thực hiện XOR giữa source MAC nguồn với source MAC đích. Nó sẽ lựa chọn cùng 1 slave cho 1 địa chỉ MAC : Có khả năng chịu lỗi : Có khả năng cân bằng tải :
  - Mode 3 : broadcast : Toàn bộ gói tin sẽ được truyền trên tất cả các slave interface : Có khả năng chịu lỗi : Có khả năng cân bằng tải :
  - Mode 4 : 802.3ad : Tạo nhóm tập hợp các interfacce chia sẻ chung tốc độ và duplex : Có thể truyền và nhận gói tin trên các cổng đang hoạt động. Yêu cầu cần phải có switch tương thích với chuẩn 802.3ad : Có khả năng chịu lỗi : Có khả năng cân bằng tải :
  - Mode 5 : balance-tlb : Cân bằng tải thích ứng với quá trình truyền tin. Lưu lượng đi ra ngoài (outgoing) phân tán dựa trên tải hiện tại trên mỗi slave( tính toán liên quan đến tốc độ). Lưu lượng tới( Incomming) nhận bởi slave active hiện tại, nếu slave này bị lỗi khi nhận gói tin, các slave khác sẽ thay thế, MAC address của đường bond sẽ chuyển sang 1 trong các slave còn lại : Có khả năng chịu lỗi : Có khả năng cân bằng tải :
  - Mode 6 : balance-alb : Cân bằng tải thích ứng. Là sự kết hợp giữa balance-tlb và receive load balancing(rlb) cho lưu lượng của ipv4. Cân bằng tài nhận đạt được nhờ kết hợp với ARP. Bondin driver sẽ chặn các bản tin phản hồi ARP gửi bởi hệ thống cục bộ trên đường ra và ghi đè địa chỉ MAC nguồn bằng địa chỉ MAC của 1 trong các slaves trên đường bond : Có khả năng chịu lỗi : Có khả năng cân bằng tải :
### Thực hành bonding
## Routing
### Các giao thức định tuyến - Định tuyến tĩnh
### Routing talbe, cấu hình định tuyến trên linux
## Firewall
### Iptables và cơ chế hoạt động của nó
### Cách cấu hình iptables và thực hành
## DHCP, DNS Xây dựng LAB 
## Keepalived 
### Cơ chế hoạt động và các khái niệm liên quan Keepalived
### Cấu hình Keepalived
## Tool debug, config network
