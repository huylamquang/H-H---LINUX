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
## Switching
### Bonding
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
