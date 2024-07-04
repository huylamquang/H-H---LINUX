 # HỆ ĐIỀU HÀNH LINUX 
## Các khái niệm và thao tác được sử dụng trong Linux
### 1. Các lệnh được sử dụng để thao tác với văn bản
#### Các lệnh cơ bản thao tác với văn bản
- pwd: Chuyển hướng thư mục làm việc
- history: Lệnh sử dụng để xem các lệnh đã được sử dụng trong quá khứ
  - `Ctrl + R`: Tìm lệnh đã từng sử dụng trong quá khứ
  - `Ctrl + S`: Stop công việc đang làm, hiểu như là treo máy và không làm gì cả. Ctrl + Q: để thoát ra khỏi chế độ stop công việc
- cd: Chuyển hướng thư mục làm việc
  - Đường dẫn tuyệt đối: Đường dẫn đầy đủ địa chỉ đến 1 thư mục, 1 cách chính xác.
  - Đường dẫn tương đối: Không bao gồm đường dẫn đầy đủ của 1 thư mục.
  - Cú pháp
    ```
    cd [path]
    ```
    - Ví dụ:
      ```
      cd /home/huylq -> Chuyển đến thư mục huylq
      ```
- cat: sử dụng để đọc file, nối file, tạo file, ...
  - Cú pháp:
    ```
    cat [option] [name_file]
    ```
    - Ví dụ:
      ```
      cat file1 -> đọc nd của file1.
      cat file1 file2 -> đoc nội dung của file2.
      cat > file1 -> Tạo file1 với nội dung tự thêm vào.
      cat file1 > file2 -> Ghi đè file1 lên file2.
      cat file1 >> file1 -> Nối file1 vào cuối file2.
      ``` 
- sort: Là lệnh được sử dụng để sắp xếp cùng với các option sử dụng( mặc định là sắp xếp số trước, sau đó là sắp xếp theo ký tự từ A-Z - Sắp xếp theo cột đầu tiên).
  - Cú pháp:
    ```
    sort [option] [name_file]
    ``` 
    - Các option được sử dụng là:
      - `-n`: sắp xếp theo số thực tế.
      - `-r`: sắp xếp ngược theo thực tế.
      - `-u`: sắp xếp loại bỏ các trùng lặp.
    - Ví dụ:
      ```
      sort -n file1
      sort -r file1
      sort -u file1
      
- uniq: Lệnh được sử dụng để loại bỏ các trùng lặp và chỉ loại bỏ các trùng lặp liên tiếp vì thế thường được sử dụng với `sort` để có thể loại bỏ hoàn toàn trùng lặp.
  - Cú pháp:
    ```
    uniq [option] [name_file]
    ```
    - Các option được sử dụng là:
      - `-c`: Xuất ra danh sách các dòng trùng lặp trước số lần xuất hiện của dòng đó.
      - `-d`: Xuất ra các dòn bị trùng.
      - `-u`: Xuất ra các dòng duy nhất.
    - Ví dụ:
      ```
      Uniq -c file1
      Uniq -d file1
      Uniq -u file1
      Sort -nr file1 | uniq  -> sử dụng sort để sắp xếp ngược theo số sau đó dùng uniq để loại bỏ các dòng bị trùng.
      ```
- wc: Là lệnh được sử dụng để in ra thông tin về số từ, số byte, số dòng và namefile
  - Cú pháp:
    ```
    wc [option] [name_file]
    ```
    - Các option được sử dụng là:
      - `-c`: Hiển thị số byte của tệp
      - `-L`: Hiển thị dòng dài nhất của tệp
      - `-l`: Hiển thị số dòng
      - `-m`: Hiển thị số ký tự của tệp
      - `-w`: Hiển thị số từ của tệp
    - Ví dụ:
      ```
      wc -c file1
      wc -L file1
      wc -mw file1
      ```
- split: sử dụng để quản lý các tệp lớn có chức năng chia file thành các file nhỏ hơn và truyền tệp qua mạng có băng thông hạn chế, sử dụng với các công cụ khác.
  - Cú pháp:
    ```
    Split [option] [name_file]
    ```
    - Các option được sử dụng là:
      - `-l`: Sử dụng để chia file thành các file nhỏ hơn dựa trên tham số sau -l.
      - `-b`: Sử dụng để chia file thành các file nhỏ hơn dựa trên kích thước cụ thể cho mỗi tệp đầu ra
      - `-C`: Sử dụng để chia file thành các file nhỏ hơn dựa trên kích thuớc tối đa của 1 file
    - Ví dụ:
      ```
      split -l 3 file1 file1.chia
      split -b 1000 file1 file1.chia
      split -C 1024 file1 file1.chia
      ``` 
- cut: Sử dụng để trích xuất các cột và các trường, thay thế ký tự cần thiết trong văn bản và có khả năng kết hợp tệp văn bản
  - Cú pháp:
    ```
    cut [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-c`: In ra cột cụ thể của mỗi dòng
    - `-d`: Trích xuât trường cụ thể của mỗi dòng trong file và các trường phân cách nhau bởi ký tự cụ thể.
    - `-f`: Sử dụng cùng các option `-c`, `-d` để chọn các cột cần trích xuất.
  - Ví dụ:
    ```
    cut -c1-5 file1
    cut -d':' -f3 file1
    cut -d':' -f1 file1 | cut -d'/' -f2 file2 -> Kết hợp cột 1 của file1 và cột 2 của file2 in ra màn hình.
    ```
- head: Sử dụng để hiển thị nội dung của 10 dòng đầu tiên trong văn bản
  - Cú pháp:
    ```
    head [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-n`: in ra số dòng cụ thể
    - `-c`: Hiển thị số byte đầu tiên được chỉ định từ tệp
  - Ví dụ:
    ```
    head -n 5 file1
    head -c 100 file1 
    ```
- tail: Lệnh sử dụng để hiển thị nội dung của các dòng cuối trong văn bản
  - Cú pháp:
    ```
    tail [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-n`: Hiển thị số dòng cuối cùng cần hiển thị
    - `-c`: Hiển thị số lượng byte cuối cùng được chỉ định
    - `-f': Hiển thị các dòng mới được thêm vào tệp theo thời gian thực -> Được sử dụng trong việc kiểm tra các file log.
  - Ví dụ:
    tail -n 20 file1
    tail -c 50 file1
    tail -f /var/log/syslog 
- less: Dùng để đọc các file lớn, có thể cụôn trang lên hoặc cuộn trang xuống. Tìm kiếm trên, tìm kiếm dưới và được sử dụng để đọc các file log
  - Cú pháp:
    ```
    less [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-N`: Hiển thị số dòng có trong tệp
    - `-F`: Sử dụng để xem các file log vì nó theo dõi, tự động cập nhật nội dung.
  - Ví dụ:
    ```
    less -N file1
    less -F file1
    ```
- tac: Là lệnh sử dụng để đọc file nhưng được sắp xếp từ dưới lên
  - Cú pháp:
    ```
    tac [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-n`: Hiển thị số dòng trước mỗi dòng đầu ra được đảo ngược
    - `-s`: Loại bỏ số dòng khỏi đầu ra
  - Ví dụ:
    ```
    tac -n file1
    tac -s file1
    ```
#### 2. Các lệnh nâng cao thao tác với văn bản
- grep: Là lệnh được sử dụng để tìm kiếm chuỗi trong văn bản. Thường kết hợp với biểu thức chính quy để tìm kiếm sđt, ngày tháng năm, địa chỉ ip, ... có tỏng văn bản.
  - Cú pháp:
    ```
    grep [option] [pattern] [name_file]
    ```
  - Các option được sử dụng là:
    - `-i`: Không phân biệt chữ hoa chữ thường
    - `-v`: in ra các dòng không chứa kết quả
    - `-c`: In ra số lượng kết quả khớp.
    - `-n`: in ra kết quả khớp + số dòng
    - `-F`: **grep -F accounts.txt /etc/passwd** -> được hiểu là đọc các mẫu có trong file accounts.txt mỗi dòng trong tệp này sẽ là 1 mẫu riêng biệt sau đó mẫu này sẽ được so sánh với các dòng có trong tệp /etc/passwd nếu khớp thì nó sẽ in ra màn hình.
  - Ví dụ:
    - Các ví dụ cơ bản:
   ```
   grep -i quanghuy file1
   grep -v quanghuy file1
   grep -c quanghuy file1
   grep -n quanghuy file1
   ```
   - Ví dụ về việc kết hợp biểu thức chính quy:
     - Tìm kiếm số điện thoại:
       ```
       grep -E '[0-9]{10}' file
       ```
     - Tìm kiếm ngày tháng năm:
       ```
       grep -E '[0-9]{1,2}/[0-9]{1,2}/[0-9]{4}' file1
       ```
     - Tìm kiếm địa chỉ IP:
       ```
       grep -E '([0-9]{1,3}\.){3}[0-9]{1,3}' file1
       ```
- sed: Là trình chỉnh sửa luồng để lọc, được sử dụng để lọc và thực hiện các thao tác nâng cao bao gồm thay thế, thêm, sửa, xóa văn bản.
  - Cú pháp:
    ```
    sed [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-i`: Thay thế trực tiếp trên file gốc
    - `-n`: chỉ định các dòng cần thao tác
  - Ví dụ:
    - Thay đổi cả dòng tệp:
      ```
      sed 's/pattern/replace/g' file1
      ```
      Thực hiện viêc thay thế pattern thành replace trên file1 với 's' là tuỳ chọn được sử dụng để thay thế, 'g' là cờ toàn cục, tức nó sẽ thay đổi tất cả mẫu có trong 1 phạm vi nếu không có 'g' thì nó chỉ thay đổi các mẫu ở cột đầu tiên. Nếu mẫu rỗng thì nó sẽ không làm gì cả -> Chỉ có tác dụng với mẫu chỉ định.
    - In ra từ dòng 1 đến dòng 5:
      ```
      sed -n '1,5p' file1
      ```
      Thực hiện in ra man hình 5 dòng đầu tiên với 'p' là Print
    - Lặp lại 3 lần lệnh sed in ra dòng 1.3.5 sau đó lưu trực tiếp vào cuối file3:
      ```
      for i in {1..3}; do sed -n '1p;3p;5p' file3; done >> file3
      ```
      Lệnh sed đươc thực hiện 3 lần với nội dung in ra dòng 1,3,5 và đầu ra của nó được lưu trực tiếp vào cuối file3.
    - Xóa các dòng trống:
      ```
      sed -i '/^$/d' file2
      ```
      Với tùy chọn `-i` là lưu trực tiếp vào file2. `d` xóa các dòng với nội dung `^$`, `^$` biểu thị cho đầu dòng và cuối dòng không chứa nội dung( chứa khoảng trắng or tab).
    - Thêm text:
      ```
      sed '1s/^/toilamlab/' file1
      ```
      Thêm text toilamlab vào dòng 1 của file1
      ```
      sed -i '1i\toilamlab' file1
      ```
      Thêm text toilamlab vào trước dòng 1 của file1 và lưu trực tiếp vào file1.
      ```
      sed -i '1a\toilamlab' file1
      ```
      Thêm text toilamlab vào sau dòng 1 của file1 và lưu trực tiếp vào file1.
- awk: Là 1 ngôn ngữ giúp chúng ta thao tác dễ dàng với kiểu dữ liệu có cấu trúc và tạo ra những kết quả được định dạng. Được sử dụng để tìm kiếm và xử lý file text.
  - Cú pháp:
    ```
    awk pattern actions file
    ```
    - Với:
      - pattern là những biểu thức chính quy
      - actions là những câu lệnh cần thực hiện
      - file là file cần thực hiện awk
    - Ví dụ:
      - Sử dung để in các dòng trong file
        ```
        awk '{print}' file1
        ```
      - Xử lý trường:
        Tách các trường nhất định:
        + $0: Chứa toàn bộ văn bản
        + $1: Chứa văn bản trường đầu tiên
        + $2: chứa văn bản trường thứ hai
        + $(2+3): Kết quả của các biểu thức được sử dụng, đưa ra trường thứ năm
        + NF: là một biến tích hợp có chứa số lượng các trường trong bản ghi hiện tại. Vì vậy $NF đưa ra trường cuối cùng.
        ```
        awk '{print $1}' file1
        awk '{print $4}' file1
        ```
        In ra 3 ký tự đầu tiên của mỗi dòng:
        ```
        awk '{print substr($0,1,3)}' file1
        ```
      - Lọc các kí tự: Các kí tự được lọc được đặt trong '//'
        ```
        awk '/quanghuy/' file1
        awk '/quanghuy/{print $NF}' file1
        ```
        Lọc dựa trên số dòng:
        ```
        awk 'NR==2' file1
        ```
      - Tìm kiếm:
        ```
        awk '/pattern/ {print NR,$0}' file1
        ``` 
#### Công cụ vim và byobu
##### Vim - Thao tác với văn bản
- Các chế độ: Có 4 chế độ bao gồm
  - Chế độ thường( command line): Được sử dụng để thực hiện các thao tác cơ bản với văn bản chẳng hạn như:
    - `gg`: Di chuyển trỏ đến đầu tệp
    - `G`: Di chuyển trỏ đến cuối tệp
    - `Ctrl + B,F,U,D,Y,E`: Thực hiện các thao tác đến cuộn trang lên xuống
    - `dd`: Xóa dòng hiện tại
    - `dw`: Xóa từ hiện tại
    - `yw`: sao chép từ
    - `yy`: sao chép dòng
    - `u`: Hoàn tác | `Ctrl + r`: Tiến tới hành động đã hoàn tác
    - `i và o`: Bước vào chế độ Insert 
  - Chế độ chèn( insert): Là chế độ để ta có thể thực hiện các thao tác nhập từ bàn phím làm việc với văn bản.
  - Chế độ Ex: Là các lệnh được đặt sau dấu "**:**" như:
    - `:q!`: thoát và không lưu các thao tác
    - `:w`: lưu các thao tác đã thực hiện
    - `:wq`: thoát và lưu các thao tác thực hiện
    - ...
  - Chế độ Visual: Là chế độ được sử dụng để sao chép, xóa, dán văn bản.
    - Cách thực diễn ra như sau: Để bước vào chế độ vim ta nhấn `v`. Từ vị trí nhấn `v` ta có thể sử dụng các phím điều hướng để bôi đen đoạn văn bản or sử dụng tổ hợp v + số dòng( tính từ vị trí con trỏ + số dòng). Sau đó nhấn `y` để copy đoạn vừa bôi đen or nhấn `d` để xóa.
    - Ta hoàn toàn có thể thay thế chuỗi bằng lệnh sed sau khi đã bôi đen với cú pháp như sau: `sed 's/pattern/replace/g' file1`
    
##### Byobu - Duy trì trạng thái làm việc
- **Byobu** là 1 tiện ích để tạo ra các phiên làm việc. Với các tiện ích có thể cần như tạo, sửa xóa, chia đôi màn hình,...
- Việc sử dụng byobu cho Sys Adm là cần thiết bởi vì nó có thể làm việc với nhiều server cùng lúc và khi thực hiện điều đó ta cần SSH vào nhiều server. Trong quá trình làm việc nếu xảy ra các sự cố như mất điện, hay mất mạng phiên làm việc bị dừng lại thì các kết nối SSH sẽ bị mất nhưng nếu chúng ta sử dụng byobu thì chúng sẽ lưu tất cả bao gồm trạng thái đang làm việc các với các phiên làm việc kết nối với ssh đến server.
- Các thao tác cơ bản với byobu:
  - Xem hướng dẫn: `Shift + F1`
  - Tạo 1 cửa sổ mới theo chiều ngang: `Shift + F2`
  - Tạo 1 cửa số mới theo chiều dọc: `Ctrl + F2`
  - Tạo 1 phiên làm việc mới: `Ctrl-Shift + F2` 
  - Đổi tên: sử dụng `F8`
  - Chuyển đổi qua lại: sử dụng `Ctrl + F3,F4` or `Shift + F3,F4`
  - Đóng 1 cửa số hay tab: Sử dụng lệnh `exit`
  - Tách phiên và không thoát: `Shift + F6` Sẽ tách phiên byobu hiện tại ra khỏi cửa sổ terminal. Điều này cho phép tiếp tục các tác vụ đang chạy trong phiên đó ở chế độ nền, ngay cả khi đóng terminal. Và có thể khôi phục bằng lệnh `byobu attach`.
  - Tách tất cả các máy khách trừ bạn: `Alt + F6` phù hợp cho việc sử dụng byobu trên máy chủ từ xa. Nó cho phép tách tất cả các kết nối( máy khách) với phiên byobu hiện tại, chỉ giữ lại kết nối của mình.
  - Kill attach được chọn: `Ctrl + F6` sử dụng để đóng 1 phân vùng cụ thể trong cửa sổ byobu hiện tại.
  - Xem lịch sử: `F7` và lưu lịch sử thành ảnh chụp màn hình `Shift + F7`và ảnh được lưu tại $BYOBU_RUN_DIR/printscreen.(~/.byobu/sessions/<session_name>).
  - Mở của số cấu hình byobu-config: `F9` và `Ctrl + F9` sẽ cho chép bạn nhập 1 lệnh và lệnh này sẽ được chạy đồng thời trên tất cả các cửa sổ còn lại và `Shift + F9` Chạy lệnh trong tất cả phân vùng của cửa số Byobu hiện tại.
### Tiến trình và các vấn đề liên quan đến tiến trình
- Tiến trình là 1 quá trình tiến hành 1 công việc và cần tài nguyên hỗ trợ, tính toán từ CPU
- Load average: Tải trung bình là số lượng tiến trình cần tài nguyên tính toán từ CPU.
- Chỉ số tận dụng CPU là việc sử dụng tiến trình nhiều hay ít. Ứng với mỗi core sẽ có 1 tiến trình sử dụng và tiến trình đó sử dụng khả năng của CPU làm sao mà tối ưu nhất.
- Các lệnh sử dụng để quản lý và giám sát tiến trình: top, htop, ps
  - top: Hiển thị tổng quan các thông tin về RAM, CPU, PID, Load average, các thông số liên quan 1 cách chi tiết và cụ thể của từng tiến trình.
    - Các option hiển thị thông tin:
      + Với CPU: Nhấn `P` để xem tiến trình chiếm nhiều CPU nhất.
      + Với Mem: Nhấn `M` để xem tiến trình chiếm nhiều RAM nhất.
      + Với ID: Nhấn `N` để sắp xếp theo ID
      + Với Time: Nhấn `T` để sắp xếp theo thời gian sử dụng tiến trình
    - Các tham số có trong lệnh top:
      + Dòng 1:

         ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/0fc0271e-d3f0-488d-b5ab-4e676829d1e8)

        - Hiển thị về thời gian hiện tại - Thời gian đã sử dụngg.
        - Số lượng user sử dụng
        - Load Average: Tải trung bình là 1 tham số cần chú ý. Là số lượng tiến trình cần tài nguyên tính tóa từ CPU trong khoảng thời gian(5p, 10p, 15p). Lượng tiến trình cần duy trì trong khoảng từ 0 đến số lượng CPU có thể có, tức là nếu CPU có 6 core thì lượng tiến trình ở mức cho phép là 1-6 tiến trình. Nếu vượt quá thì sẽ có 1 số vấn đề xảy ra:
          - Hiệu suất hệ thống giảm vì có quá nhiều tiến trình phải đợi CPU xử lý, mỗi tiến trình sẽ được chia nhỏ thời gian xử lý.
          - Tăng thời gian phản hồi: Các yêu cầu của người dùng chờ được phản hồi sẽ tăng lên đáng kể vì CPU đang bận xử lý các tiến trình.
          - Tăng nhiệt độ CPU vì CPU hoạt động ở công suất tối đa.
          - Swap khi RAM không đủ là việc sử dụng bộ nhớ Swap để lưu trữ tất cả các tiến trình đang chạy, lưu trữ tạm thời 1 phần dữ liệu của các tiến trình, giảm hiệu suất vì bộ nhớ Swap chậm hơn nhiều so với RAM. Nó được lấy từ ổ cứng hoặc từ SSD.
          - Khả năng treo máy: Quá tải hệ thống.
        - Những yếu tố ảnh hướng đến load average:
          - Cpu Utilization( tận dụng CPU): Nếu lượng CPU lớn hơn 100% và load average vượt quá số CPU đang có thì ta có thể kết luận rằng loadaveg cao bởi lượng lơn các tiến trình đang running hoặc đang đợi CPU xử lý.
          - Với disk I/O, Network Traffic: Nếu lượng CPU sử dụng vẫn bình thường( tức không quá cao) nhưng loadavg vẫn cao hơn số CPU đang có. Ta có thể kết luận có thể disk I/O or Network Traffic hoặc cả 2 yếu tố chính gây ra tải cao cho hệ thống.
          - Tiến trình đi vào CPU để xử lý. CPU sẽ truy cập vào disk để lấy thông tin các rows. Tại thời điểm này CPU sẽ Idle và chờ disk phản hồi, đây chính là thời điểm waiting on disk.
        - Tổng quát lại : nếu phần trăm I/O wait lớn (1/số lượng cpu) * 100% thì đây là lúc bạn cần phải xem xét lại disk I/O hệ thống của mình. High I/O wait phụ thuộc vào số lượng CPU server đang có. 50% iowait của server 2 cpu chỉ tương đương với 12.5% iowait trên server có 8 cpu. Tỉ lệ nghịch với số lượng cpu của server. Số lượng CPU càng cao thì iowait càng thấp.
      + Dòng 2:
     
        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/dee05ee7-e72a-4fe7-8e29-4e2c07c3d330)

        - Tổng số lượng tiến trình
        - Số tiến trình đang chạy
        - Số tiến trình trong trạng thái nghỉ ngơi
        - Số tiến trình bị dừng
        - Số tiến trình đã hoàn thành công việc nhưng chưa được tiến trình mẹ xóa nó khỏi bảng tiến trình.
      + Dòng 3:

        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/91808b1a-175c-493e-a741-d06d06a6cd3b)

        - %CPU do User sử dụng
        - %CPU do hệ thống sử dụng
        - Giá trị chuẩn - Biểu thức mức độ ưu tiên: Các tiến trình có giá trị càng chuẩn mức độ ưu tiên càng thấp.
        - Thời gian mà CPU nhàn rỗi
        - Thao tác I/O: Là quá trình CPU truy cập vào disk và chờ disk phản hồi
        - Tiến trình phục vụ ngắt phần cứng
        - Tiến trinh phục vụ ngắt phần mềm: Là các tiến trình cần chờ đợi các thành phần khác như hardware, software để tiếp tục thực thi tiến trình.
        - Các tiến trình phục vụ các tác vụ ngắt của máy ảo khác trong môi trường ảo.
      + Dòng 4:
     
        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/c4212cb9-a8b4-421a-a7b9-766d9f37c651)

        - Tổng dung lượng Mem có
        - Số Mem chưa được sử dụng
        - Số Mem đã đang được sử dụng
        - Bộ nhớ đệm và được đệm và lưu vào bộ nhớ đệm
      + Dòng 5:
     
        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/d772fae9-6d8f-4944-a546-c8f7535b6a90)

        - Tổng dung lượng hoán đổi
        - Số dung lượng đổi chưa được sử dụng
        - Số dung lượng hoán đổi đã sử dụng
        - Số lượng Mem có sẵn.
      + Dòng 6:
     
        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/bec5826d-d2a4-4cb2-b338-269425e8ef5b)

        - PID: ID của tiến trình
        - USER: Tên của user sử dujg tiến trình
        - PR: Là mức độ ưu tiên của tiến trình. Tính toán dựa trên nice value và các yếu tố khác. Thay đổi theo thời gian, giá trị từ 0 -> 39( 0 là ưu tiên cao nhất).
        - NI: Nice value là giá trị sử dụng để điều chỉnh mức độ ưu tiên của tiến trình. Giá trị sử dụng để cố định và không đổi theo thời gian, giá trị từ -20 -> 19( 0 là giá trị mặc định).
        - VIRT: Tổng dung lượng bộ nhớ được sử dụng bởi tiến trình(bao gồm cả bộ nhớ Swap).
        - SHR: Bộ nhớ dùng chung của tiến trình với các tiến trình khác.
        - S(State): Trạng thái của tiến trình:
          - S - Sleep( ngủ, chờ 1 sự kiện kết thúc)
          - R - Run( Đang thực thi or đang chờ để thực thi)
          - I - Edle( Nhàn rỗi - Không làm gì).
          - Z - Zombie( Các tiens tình con bị kết thúc có CTDL chưa được xóa khỏi bảng tiến trình).
   - Lệnh htop: Là 1 lệnh được sử dụng để giám sát tiến trình, hiển thị các thông số về cpu, ram, loadavg, ... tương tự như top nhưng được hiển thị bằng các mầu sắc 1 cách trực quan hơn.
     - Trong htop có thể sử dụng phím F1 để xme các hướng dẫn cụ thể hơn
 
       ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/afbf9e4f-d2c0-4c5b-afcc-b9dc604d907a)

     - Các màu sắc được biểu thị trong htop:
       - Với CPU:
         - Xanh lam: Các tiến trình với độ ưu tiên thấp
         - Xanh lục: Các tiến trình người dùng
         - Đỏ: Các tiến trình hạt nhân
         - Vàng: Thời gian IRQ( ngắt phần cứng)
         - Đỏ tươi:Thời gian Soft IRQ( Ngắt phần mềm)
         - Xám: Thời gian chờ IO
       - Với Mem:
         - Xanh lục: Bộ nhớ đã dùng
         - Xanh dương: Bộ nhớ buffers
         - Vàng: Bộ nhớ cache
       - Với Swap:
         - Đỏ: Bộ nhớ swap đã sử dụng
         - Vàng: Bộ nhớ cache đã sử dụng
         - Xám:
   - Lệnh kill và kill -9 cùng các loại tín hiệu:
     - Lệnh kill và kill -9
       - `kill [PID]` là kiểu thường, kiểu tín hiệu là sigterm, cho phép tiến trình hoàn thành và giải phóng tài nguyên, có khả năng lựa chọn xử lý tín hiệu.
       - `kill -9 [PID]` Là kiểu dứt điểm, kiểu tín hiệu là sigkill, bắt buộc chấm dứt ngay lập tức, không cho cơ hội làm thêm gì cả.
     - Các loại tín hiệu phổ biến:
       - Tín hiệu KILL: Các tín hiệu khác có thể chọn xử lý tín hiệu được đưa đến, có thể bỏ qua các tín hiệu đó còn tín hiệu kill là chấm dứt hoàn toàn. Tức là Kernel sẽ ngay lập tức chấm dứt tiến trình.
       - Tín hiệu CONT: Khôi phục tiến trình sau khi sử dụng STOP và TSTP, sử dụng lệnh fg và bg để gửi.
       - Tín hiệu TSTP: Đây là tín hiệu được gửi bởi thiết bị đầu cuối khi nhấn `Ctrl + Z`. Không giống như STOP, tín hiệu TSTP được chương trình nhận nhưng chương trình có thể chọn bỏ qua nó
   - Lệnh ps: Hiển thị các thông tin về tiến trình nhưng tại 1 thời điểm cố định
     - Các tùy chọn:
       - ps x: hiển thị các tiến trình hiện có
       - ps aux: Hiển thị tất cả các tiến trình đang chạy với những thông in chi tiết:
         - User: User sử dụng tiến trình
         - Pid: ID của tiến trình
         - %Mem: % Mem mà tiến trình sử dụng
         - %CPU: % CPU mà tiến trình sử dụng
         - VSZ: Kích thước ảo của tiến trình(byte)
         - RSS: Kích thước bộ nhớ thực mà tiến trình sử dụng(byte)
         - TTY: "?" thể hiện việc không có 1 thiết bị đầu cuối nào điều khiển
         - STAT: R - Running  ; S - Sleeping ; D - Ngủ kh gián đoạn ; T - Đã dừng lại ; Z - tiến trình k tồn tại or hoặc là zombie ; “<” - tiến trình có mức độ ưu tiên cao ; N - Tiến trình có mức độ ưu tiên thấp ; I - Trạng thái nhàn rỗi.
         - START: Thời gian bắt đầu chạy
         - TIME: Thời gian đã chạy
         - COMMAND: Lệnh sử dụng
### Phần mềm và các vấn đề liên quan đến phần mềm
- Package là 1 dạng tệp tin chứa các thành phần để cài đặt 1 phần mềm: Tệp thực thi, tệp cấu hình, tệp thư viện, tệp hướng dẫn.
- Depend là sự phụ thuộc của 1 phần mềm đang được cài đặt vào 1 phần mềm khác.
  vd: `sudo apt-cache depends firefox`
- Binary Package là 1 dạng package. Nó được biên dịch sẵn mà không cần tới mã nguồn khi muốn cài đặt phần mềm, là những tệp dạng `*.deb`
  vd: `cd /var/cache/apt/archives` -> Nơi lưu trữ file `*.deb` do người dùng tải về.
- Repo là nơi lưu trữ thông tin về vị trí của package, khi cài đặt phần mềm nó sẽ trỏ đến các vị trí đó.
  vd: `cat /etc/apt/sources.list` -> mỗi dòng đại diện cho 1 kho lưu trữ phần mềm bao gồm các thông tin:
  ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/106e2fab-4194-424c-971c-726971a27878)
  - Loại kho lưu trữ: ppa, deb
  - Vị trí của kho lưu trữ: URL
  - Tên Repo: jammy,...
  - Vesion Repo: multiverse
- Tùy thuộc vào bản HĐH được phân phối thì sẽ có những cách cài đặt phần mềm riêng:
  - Sử dụng APT: `sudo apt install [name_pm]`
  - Sử dụng từ tệp `*.deb`: `dpkg -i *.deb` (download các file .deb về).
  - Cài đặt từ mã nguồn:
    - B1: Tải xuống mã nguồn của phần mềm cần tải
    - B2: Giải nén mã nguồn
    - B3: Cài đặt các phụ thuộc mà phần mềm đó cần để có thể hoạt động được.
- Các trình quản lý package của Debian(dpkg, apt)
  - dpkg: Trình quản lý phần mềm được sử dụng để cài đặt, gỡ bỏ phần mềm
  - Cách sử dụng:
    - `dpkg -l`: Liệt kê danh sách phần mềm đã cài đặt
    - `dpkg -i [*.deb]`: Cài đặt phần mềm với tệp *.deb
    - `dpkg -r [*.deb]`: Gỡ bỏ phần mềm với tệp *.deb
    - `dpkg -s firefox`: Kiểm tra gói tin đã được cài đặt. Hiển thị về thông tin phần mềm firefox đã được cài đặt.
  - apt: Trình quản lý package nâng cao hơn so với dpkg, sử dụng để cài đặt, gỡ bỏ phần mềm.
  - Cách sử dụng:
    - `sudo apt install [name]`: cài đặt 1 phần mềm với tên của nó
    - `sudo apt remove [name]` : gỡ bỏ 1 phần mềm với tên của nó
    - `sudo apt list --installed | grep [name_sw]`: đưa ra danh sách phần mềm đã cài đặt và tìm 1 phần mềm đã cài đặt cụ thể.
  - Sự khác biệt giữa `apt update và apt upgrade`:
    - `apt update`: Cập nhật danh sách các package mới từ repo, sử dụng danh sách mới này để cài đặt phần mềm. Lưu ý, dùng thường xuyên và trước khi cài đặt phần mềm vì sẽ sử dụng danh sách các package mới.
    - `apt upgrade`: Nâng cấp các package lên phiên bản mới nhất và được sử dụng trước khi cài đặt 1 phần mềm để sử dụng package với phiên bản mới nhất.
### StartUp Scripts và các cách để chạy scripts mỗi khi mà server khởi động lại
- Sử dụng StartUp Scripts: Tự động hóa các tác vụ sau khi hệ thống khởi động
  - Sử dụng Systemd:
    - B1: Viết Scripts
      ```
      #!/bin/bash
      #Cập nhật kho lưu trữ và cài đặt Nginx:
      sudo apt update && sudo apt install nginx
      #Khởi động dịch vụ Nginx:
      sudo systemctl start nginx
      #Kích hoạt dịch vụ Nginx để tự động khởi động khi khởi động máy chủ:
      sudo systemctl enable nginx
      ```
    - B2: Lưu Scripts vào 1 file với tên gọi `install-nginx.sh` ở thư mục `/etc/systemd/system/` và cấp quyền `sudo chmod +x /etc/systemd/system/install-nginx.sh`
    - B3: Tạo tệp đơn vị systemd:
      - **[Unit]**
      `Description=Install and configure Nginx web server After=network.target`   -> #đảm bảo script được thực thi sau khi dv mạng khởi động
      - **[Service]**
      `Type=oneshot` -> #Script này chỉ được chạy 1 lần sau khi khởi động `ExecStart=/etc/systemd/system/install-nginx.sh`  -> #xác định vị trí của scripts
      - **[Install]**
      `WantedBy=multi-user.target` -> #đảm bảo scripts vẫn được kích hoạt khi hệ thống khởi động ở chế độ đa người dùng.
      - Sau đó, Lưu tệp này với tên gọi `nstall-nginx.service` vào thư mục `/etc/systemd/system/`
    - B4: Kích hoạt Script: `sudo systemctl enable install-nginx.service`
  - Sử dụng Cron:
    - @reboot /path/to/your/script.sh -> chạy 1 script ở 1 đường dẫn cụ thể sau khi hệ thống khởi động.
  - Sử dụng tệp cấu hình khởi động: rc.local
    - B1: tạo 1 script và lưu vào `/home/huylq/myscript.sh`
    - B2: Cấp quyên thực thi cho nó: `sudo chmod +x /home/huylq/myscript.sh`
    - B3: mở tệp /etc/rc.local sau đó thêm dòng chứa đường dẫn của tệp script vào cuối: `/home/huylq/myscript.sh`.
    - B4: Khởi động lại máy chủ: `sudo reboot`
### FS, Partition, Mount và các vấn đề liên quan
#### FileSystem
- FS (hệ thống tệp tin): là 1 dạng cấu trúc dữ liệu dược sử dụng bởi hệ điều hành để tổ chức và quản lý các tệp tin trên 1 thiết bị lưu trữ như ổ cứng, ổ đĩa, thẻ nhớ. Bao gồm các chức năng:
  - Lưu trữ dữ liệu: Lưu trữ dữ liệu dưới dạng tệp và thư mục
  - Tổ chức dữ liệu: Được tổ chức theo cấu trúc phân cấp, giúp dễ dàng tìm kiếm và quản lý tệp
  - Quản lý quyền truy cập: Kiểm soát quyền truy cập vào tệp tin, đảm bảo rằng chỉ người dùng được ủy quyền mới có thể truy cập và sửa đổi.
  - Bảo vệ dữ liệu: Bao gồm các tính năng sao lưu và phục hồi để bảo vệ dữ liệu khỏi mất or hỏng.
  - Các loạt hệ thống tệp tin được sử dụng phổ biến cho server Linux:
    - Ext4: Là 1 dạng FS có khả năng journaling, tương thích phần cứng, dung lượng cao, hiệu suất cao,... Không giới hạn về thư mục con trong 1 thư mục, có kích thước cố định. Sử dụng kĩ thuật phân bố trễ tức là nó sẽ trì hoãn phân bố các block trước khi dữ liệu được đưa vào để có thể tối ưu hóa không gian lưu trữ và chống phân mảnh dữ liệu. Phù hợp với những tệp nhỏ, bảo vệ hệ thống tệp và thư mục mở rộng. Phù hợp với máy chủ tệp trung tâm để chia sẻ nhóm. 
    - XFS: Là 1 FS có khả năng journaling, và vô số tính năng tiên tiến như Snapshots, Quotas, ACLs, ... Phù hợp với các hệ thống tệp tin lưu trữ dữ liệu dung lượng lớn or có nhiều tập tin nhỏ, hiệu suất truy cập dữ liệu cao. Phù hợp với Khoa học dữ liệu(ML, DL, …). Phù hợp với việc truy xuất các tệp lớn mà không ảnh hưởng đến hiệu suất.
  - Khả năng journaling và phân bố trễ trên Ext4:
    - Tính năng journaling: Là quá trình ghi nhật ký các thay đổi diễn ra. Cụ thể nó hoạt động như sau: Giả sử trong quá trình làm việc mà bị mất điện đột ngột hay xảy ra lỗi phần mềm. Thì nó sẽ hoạt động bằng cách ghi chép các thay đổi được thực hiện với hệ thống tệp trước khi chúng được ghi chép vào đĩa thực tế.
      - Ghi nhật ký các thay đổi: Khi đang thực hiện thao tác ghi or xóa dữ liệu, ext4 sẽ ghi chép các thay đổi này vào 1 nhật ký trước. Sau đó ghi vào bộ nhớ đệm tạm thời trong RAM. Khi hệ thống ổn định, ext4 sẽ ghi dữ liệu từ bộ nhớ đệm vào 1 hệ thống tệp trên ổ cứng.
      - Khôi phục hệ thống tệp: Trong trường hợp xảy ra sự cố hệ thống, Ext4 sẽ sử dụng nhật ký để khôi phục lại hệ thống tệp về trạng thái nhất quán trước khi xảy ra sự cố.
    - Phân bố trễ trong Ext4: Đầu tiên là quá trình ghi dữ liệu - dữ liệu ban đầu sẽ được ghi vào bộ nhớ đệm. Thay vì phân bổ khối luôn thì ext4 sẽ tạo ra 1 bảng mô tả tạm thời( bảng này chứa thông tin về vị trí của đoạn dữ liệu đó và cho biết đoạn dữ liệu đó đang được lưu ở bộ nhớ đệm). Sau đó là việc hoãn phân bổ khối cho đến khi bộ nhớ đệm bị đầy hoặc là hệ thống cần ghi dữ liệu vào từ bộ nhớ đệm và ổ cứng. Lúc này nó sẽ chọn ra các khối chưa được sử dụng để sử dụng cho việc ghi dữ liệu vào ổ dựa trên thuật toán tối ưu hóa nhằm giảm phân mảnh ổ cứng( phân mảnh ổ cứng tức là dữ liệu không được lưu trữ 1 cách liền mạch trên các khối trong ổ, mà nó lưu 1 cách rải rác). Sau khi ghi dữ liệu vào khối đã chọn, ext4 sẽ cập nhật bản mô tả tạm thời để cho biết chính xác vị trí mới của dữ liueej trên ổ cứng.
#### Partition
- Partition là phân vùng. Là việc chia ổ đĩa thành nhiều phân vùng khác nhau để đảm nhiệm các vai trò khác nhau, chẳng hạn như phân vùng dành cho HĐH, hệ thống, phân vùng dành cho dữ liệu cá nhân. Có 3 loại phân vùng( phân vùng chính, phân vùng mở rộng, phân vùng logic):
  - Phân vùng chính: Tối đa 4 pv chính trên 1 ổ MBR. Có chức năng lưu trữ HĐH, ứng dụng, dữ liệu, ...
  - Phân vùng mở rộng: Tối đa 1 pv trên 1 ổ MBR. Chức năng chứa các phân vùng logic và không thể lưu trữ dữ liệu trực tiếp.
  - Phân vùng logic: Nằm trong phân vùng mở rộng, được tạo thoải mái và lưu trữ dữ liệu giống như phân vùng chính. Yêu cầu bắt buộc là phải nằm trong phân vùng mở rộng.
- Mục đích của việc sử dụng Partition là cải thiện hiệu suất đọc ghi, nâng cao khả năng quản lý dữ liệu , tối ưu hóa việc sử dụng dung lượng ổ 1 cách tối ưu nhất. Với mỗi 1 partition ta có thể sử dụng 1 FS riêng để phù hợp với mục đích sử dụng. Có thể hiểu rằng những dữ liệu quan trọng hoặc những dữ liệu cần được đảm bảo an toàn sẽ được sử dụng 1 FS có khả năng an toàn cao. Các loại dữ liệu sẽ được chia ra các phân vùng để dễ dàng quản lý và khi xảy ra sự cố tại phân vùng nào thì cso thể dễ dàng kiểm tra và xử lý.
#### Các lệnh được sử dụng trong việc quản lý FS và Partition.
- Lệnh Fdisk: Được sử dụng để tạo phân vùng trên ổ đĩa
- Lệnh lsblk: Sử dụng để hiển thị các phân vùng cùng với mount thư mục nào. Sử dụng thêm tùy chọn -f để xem các phân vùng sử dụng FS nào. Thường được dùng trước khi tạo phân vùng.
  - Cú pháp:
    ```
    sudo fdisk /dev/sda   -> Sau khi sử dụng lsblk để xem các pv được tạo trên ổ
    ```
  - Các option được sử dụng:
    - `m`: hiển thị các option có thể chọn
    - `p`: in ra bảng phân vùng
    - `d`: xóa 1 phân vùng
    - `n`: thêm 1 phân vùng mới
    - `w`: lưu sau khi hoàn tất
    - `q`: thoát khỏi fdisk
 - Lệnh mkfs: Được sử dụng để tạo FS sau khi tạo phân vùng
   - Cú pháp:
     ```
     mkfs -t [FS] -L [Label_name] /dev/sda1
     ```
   - Option:
     - `-t`: type fs được sử dụng
     - `L [name]`: gắn nhãn [name]
     - `-f`: Bỏ qua bất kỳ lỗi nào xảy ra trong quá trình tạo FS
 - Lệnh Mount và Umount: Sử dụng để gán 1 pv vào 1 thư mục được chỉ định.
   - Cú pháp:
     ```
     mount -t [FS] /dev/sda1 [path_to_folder]
     ```
   - Mục đích sử dụng: Dễ dàng truy cập, sử dụng. Thực hiện các thao tác 1 cách dễ dàng và nhanh chóng. Có khả năng gắn kết các phân vùng vào thư mục với các kiểu định dạng FS khác nhau để phù hợp với mục đích sử dụng.
   - Umount: Sử dụng để bảo vệ dữ liệu, giải phóng thiết bị lưu trữ, giải quyết sự cố khi gặp lỗi
   - Cú pháp: `umount /dev/sda1`
- Lệnh fsck: Được sử dụng để sửa lỗi FS
  - Cú pháp:
    ```
    fsck -t [FS] /dev/sda1
    ```
  - Ví dụ:

     ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/ba6eeaf2-6ca8-43ed-91f3-e997ef806f2a)
    - Các thông số được hiển thị bao gồm: Số file/Tổng số file, Số lượng block/Tổng số blocks:
    - Tác dụng của Fsck là:
      - Kiểm tra tính nhất quán của tệp: Fsck sẽ quét hệ thống tệp để xác định và sửa chữa các lỗi logic nếu thấy có lỗi về inode hoặc bản ghi metadata bị sai thì nó sẽ fix trực tiếp.
      - Sửa chữa lỗi hệ thống của tệp: Dựa vào các lỗi phát hiện được thì fsck hoàn toàn có thể sửa chữa được các lỗi hệ thống tệp phổ biến. Đối với các loại lỗi nghiêm trọng thì fsck sẽ đề xuất cho các user sữa chữa thủ công or là sao lưu dữ liệu trước khi sửa chữa.
      - Phục hồi dữ liệu: Tùy thuộc vào mức độ nghiêm trọng của lỗi và mức độ hỏng của hệ thống tệp, khả năng khôi phục dữ liệ của fsck được sử dụng trong 1 số trường hợp.
      - Sử dụng thường xuyên để kiểm tra và sữa chữa hệ thống tệp. Đặc biệt là sau khi xảy ra các sự cố đột ngột như cúp điện, ... Trước khi định dạng hệ thống tệp cũng nên sử dụng fsck để kiểm tra và sửa lỗi.
- Lệnh df và du sử dụng để xem dung lượng file, block, inode được sử dụng
  - Lệnh df: sử dụng để hiển thị tổng quan về dung lượng của toàn bộ hệ thống(mặc định hiển thị dưới dạng block)
    
    ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/4170783e-bfef-41f1-b5b0-78f2c20426cb)
    - Cú pháp:
      ```
      df
      ```
    - Các option được sử dụng:
      - `-a`: Hiển thị tất cả bao gồm file ẩn
      - `-h`: Hiển thị dưới dạng dễ đọc(KB, MB)
      - `-i`: Hiển thị dưới dạng inode
      - `-t[fs]`: hiển thị thông tin về pv sử dụng vd: `df -t ext4`
      - `-T`: thêm thông tin về fs sử dụng
    - Thông tin về block và inode:
      - Block: là 1 đơn vị lưu trữ dữ liệu trên ổ. Kích thước thông thường là 4Kb, 8Kb, 16Kb. Kích thước càng lớn tốc độ càng nhanh nhưng ảnh hưởng đến việc tối ưu hóa dung lượng. 1 file có thể chứa nhiều blocks. Việc sử dụng block cho 1 file phụ thuộc vào kích thuớc của file.
      - Inode: là 1 dạng cấu trúc dữ liệu lưu trữ thông tin về metadata bao gồm: quyền, kích thước, số lượng blocks, đường dẫn đến các dữ liệu của file, ...
  - Lệnh du: Sử dụng để hiển thị chi tiết dung lượng từng file, thư mục tại vị trí sử dụng.
 ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/6348ade8-03c7-42e1-8922-3d465ec8dc60)

    - Cú pháp:
      ```
      du
      ```
    - Các option được sử dụng:
      - `-a`: Hiển thị tất cả bao gồm file ẩn
      - `-h`: Hiển thi dưới dạng dễ đọc(KB, MB)
### Cấu trúc về 1 FS và các thư mục cùng chức năng của từng thư mục
- Cấu trúc về 1 FS và chức năng của từng thư mục:
  - `/`: Thư mục root chứa tất cả thông tin và người dùng root mới có quyền ghi ở trong thư mục này.
  - `/bin`: Thư mục chứa các lệnh thực thi của hệ thống. Hoạt động để có thể sử dụng các lệnh thường dùng trong Terminal: ls, ll, top, ... - Chứa các file thông tin về các lệnh tail, tac, cat, sort, ...
  - `/dev`: Thư mục chứa các thông tin về các thiết bị sử dụng. Hoạt động như 1 giao diện thiết bị. Là nơi đại diện cho các thiết bị.
  - `/etc`: Thư mục chứa các tệp tin cấu hình của HĐH. Chứa các thông tin về file cấu hình log, phần cứng, phần mềm, mạng, các dịch vụ có thể được sử dụng, ... vd: logrotate.d, resolv.conf, fstab, ...
  - `/boot`: Thư mục liên quan đến việc khởi động hệ thống. Chứa những thông tin về quá trình khởi động hệ thống, các tệp tin khởi động, ...
  - `/proc`: Thư mục chứa các thông tin về các tiến trình đang được sử dụng(ID của tiến trình) và các file liên quan đến tiến trình(uptime, version, loadavg).
  - `/lib`: Là thư viện phục vụ cho hoạt động của kernel và việc cài đặt phần mềm. Các công việc cơ bản được tải tự động từ kernel.
  - `/opt`: Optical là thư mục dành cho các phần mềm không có sẵn trên hệ thống được cài đặt từ người dùng.
  - `/sbin`: Thư mục chứa các lệnh thực thi, nếu các lệnh thực thi không có trong bin thì nó sẽ xuất hiện và được lưu trữ tại đây. Thư mục này có quyền cao hơn thư mục `/bin` và là nơi lưu trữ các chương trình quản trị hệ thống. Được sử dụng bởi admin để quản trị hệ thống.
  - `/usr`: Thư mục chứa các file binary, libary, tài liệu, source-code cho các chương trình. Gồm các file binary cho `/bin`, `/sbin` chứa các file thư viện cho `/lib`.
  - `/var`: Thư mục biến đổi. Là thư mục chứa những gì có thể biến đổi trong hệ điều hành đều được lưu trữ ở đây. Bao gồm các file log nhật ký về hệ thống, phần cứng, phần mềm, khởi động, .. của HĐH.
  - `/sys`: Thư mục chứa các thông tin về hệ thống ảo: Phần cứng, phần mềm, ... . Cung cấp giao diện để truy cập và quản lý các thiết bị và hệ thống con của kernel Linux.
  - `/snapd`: Thư mục chứa các thành phần của hệ thống quản lý gói Snap. Snap là 1 cách đóng gói phần mềm mới trong linux, cho phép cài đặt và gỡ bỏ cài đặt phần mềm dễ dàng hơn.
  - `/mnt`: Thư mục chứa các thư mục được mount và những gì liên quan đến mount.
  - `/run`: Chứa các tệp và thư mục đang chạy với các processes. sẽ được xóa khi hệ thống reboot.
  - `/srv`: Thư mục chứa dữ liệu phục vụ cho các dịch vụ mạng.
  - `/tmp`: Thư mục tạm thời để lưu trữ những tệp tạm thời của hệ thống.
  - `/root`: Thư mục của root(dành riêng cho quản trị hệ thống)
  - `/lost + found`: Là 1 thư mục được sử dụng để khôi phục hệ thống tệp ext2,3,4. Nếu 1 tệp nằm trên hệ thống thông tin này không được đóng đúng cách và xảy ra lỗi phần mềm, sự cố hệ thống thì tệp đó sẽ được lưu trong thư lục `lost + found`.
### Các lệnh được sử dụng để tìm kiếm file: which, whereis, locate, find và các lệnh sử dụng để quản lý file: ls, ll, rm, cp, mv, touch, ln
#### Các lệnh được sử dụng để tìm kiếm file
  - Lệnh which: Lệnh sử dụng để tìm kiếm đường dẫn đến 1 thư mục, file
    - Cú pháp:
      ```
      which [command]
      ```
    - Ví dụ:
   
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/a7876b0b-fe21-41fe-82c6-cf261e04cc3a)

      ```
      which ls
      which ln
      which ll
      ```
  - Lệnh Whereis: Tượng tư như which nhưng có thêm đường dẫn đến thư mục man của lệnh đó
    - Cú pháp:
      ```
      whereis [command]
      ```
    - Ví dụ:
   
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/e9833923-38e9-41f0-b3a4-b2b34eb0bf30)

      ```
      whereis ls
      whereis cat
      whereis cut
      ```
  - Lệnh locate: Lệnh tìm kiếm, thường được sử dụng cùng grep. Lệnh này tìm kiếm được dựa trên csdl có sẵn vì vậy trước khi tìm kiếm nên sử dụng lênh `updatedb` để có thể làm mới CSDL để có thể tìm kiếm dễ dàng và chính xác hơn. Sử dụng CSDL mlocate được tạo và cập nhật định kỳ để tìm kiếm file và thư mục.
    - Cú pháp:
      ```
      locate [pattern]
      ```
    - Các option được sử dụng:
      - `-count`: Đếm số lượng được tìm thấy
      - `-r`: Tìm kiếm đệ quy trong thư mục
      - `-k`: Hiển thị thêm thông tin về file được tìm thấy
      - `-i`: Bỏ qua phân biệt chữ hoa chữ thường
    - Ví dụ:
   
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/21e34780-34db-426d-9e0c-3e100f9b8e51)

      ```
      locate zip | grep bin -> tìm kiếm các file nén với mẫu tìm kiếm "bin"
      ```
 - Lệnh Find: Lệnh tìm kiếm file hoặc thư mục trực tiếp trong hệ thống tệp tin. Có thể sử dụng được nhiều tiêu chí khác nhau để tìm kiếm bao gồm:
   - `-name`: Tìm kiếm theo tê
   - `-type f or d`: tìm kiếm theo file or directory
   - `-size +N`: tìm kiếm theo size
   - `-mtime +N`: tìm kiếm file dựa theo sửa đổi cách đây N ngày
   - `-atime +N`: tìm kiếm file dựa theo truy cập cách đây N ngày
   - `-perm  777`: Tìm kiếm file dựa trên phân quyền.
   - Cú pháp:
     ```
     find [location] [option] [pattern]
     ```
   - Ví dụ:

     ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/14e19e28-5464-481b-839e-6638b8aaa1c5)
     ```
     find /home/huylq -name file3
     find / -perm 777
     ```
#### Các lệnh sử dụng để quản lý file và link
- Lệnh ls: Là lệnh sử dụng để xem thông tin các file và thư mục có trong thư mục đang làm việc
  - Cú pháp:
  ```
  ls [option]
  ```
  - Các option được sử dụng:
    -  `-l`: Hiển thị chi tiết về file, thư mục(quyền, chủ sỡ hữu user, gr, thời gian tạo file, sửa đổi file, kích thước file ở dạng dễ đọc, tên của từng file dir, ...).
    -  `-a`: Hiển thị tất cả các file và thư mục gồm cả file ẩn
    - Ví dụ:

![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/44f0ab48-ab98-4382-9ef7-60d7428341c1)
  ```
      ls -l
      ls -a
      ls -al
  ```
- Lệnh touch: Tạo file đơn giản
  - Cú pháp:
    ```
    touch [name_file]
    ```
- Lệnh cp: Lệnh copy nd của 1 file vào thư mục hoặc của 1 thư mục vào 1 thư mục.
  - Cú pháp:
    ```
    cp [option] [path_source] [path_destination]
    ```
  - Các option đươc sử dụng là:
    - `-r`: sao chép đệ quy tất cả các file và thư mục con trong 1 thư mục sang 1 thư mục đích
    - `-p`: sao chép giữ lại tất cả bao gồm quyền truy cập, chủ sỡ hữu user, gr, thời gian sửa đỏi,...
    - `-v`: Hiển thị thông tin chi tiết về quá trình sao chép
  - Ví dụ:
    ```
    cp -r DATA1 DATA2
    cp -p file1 DATA1
    cp -pv file1 DATA2
    ```
- Lệnh mv: Di chuyển file or thư mục đến nơi khác và có thể đổi tên.
  - Cú pháp:
    ```
    mv [option] [path_source] [path_destination]
    ```
  - Các option được sử dụng là:
    - `-f`: Buộc ghi đè lên tệp hoặc thư mục hiện có mà không cần xác nhận
    - `-n`: Bỏ qua thao tác nếu tệp hoặc thư mục đã tồn tại
    - `-v`: In thông tin chi tiết về quá trình di chuyển
    - `-r`: Di chuyển thư mục đệ quy gồm cả file và thư mục con bên trong
  - Ví dụ:
    ```
    mv -rf DATA1 DATA2
    mv -vr file1 DATA1
    ```
- Lệnh rm: Lệnh được sử dụng để xóa file, thư mục trong thẩm quyền của nó khỏi thư mục đang làm việc
  - Cú pháp:
    ```
    rm [option] [name_file]
  - Các option được sử dụng:
    - `-f`: buộc xóa tệp hoặc thư mục ngay mà không phải hỏi
    - `-v`: hiển thị thông tin chi tiết các tệp bị xóa
    - `-r`: xóa đệ quy, xóa toàn bộ file or thư mục con có trong thư mục cần xóa
  - Ví dụ:
    ```
    rm -f DATA1
    rm -vr DATA2
    rm -rvf DATA3
    ```
- Lệnh ln: Lệnh đực sử dụng để gắn syslink vào thư mục or file
  - Liên kết cứng(hard link): Tạo ra 1 biệt danh cho tập tin đã tồn tại. Nó trỏ trực tiếp đến inode( chứa thông tin về dữ liệu tập tin) của tập tin gốc, chia sẻ chung dữ liệu với tập tin gốc. Thay đổi nội dung của 1 tệp được liên kết cứng sẽ ảnh hưởng đến tất cả tệp khác được liên kết cùng dữ liệu.
  - Liên kết mềm( Symbolic link): Giống như một phím tắt trỏ đến 1 tập tin hoặc thư mục khác. Nó lưu trữ đường dẫn đến tập tin gốc, không chia sẻ dữ liệu với tập tin gốc. Thay đổi vị trí or tên của tệp nguồn sẽ ảnh hướng đến liên kết mềm.
  - Cú pháp:
    ```
    ln [option] [source] [destination]
    ```
  - Các option được sử dụng:
    - `-s`: Tạo liên kết mềm( mặc định là LK cứng)
    - `-f`: Buộc tạo liên kết ngay cả khi tệp đích đã tồn tại
    - `-v`: In thông tin chi tiết về các liên kết được tạo ra.
    - `-r`: Tạo liên kết đệ quy cho thư mục, bao gồm tất cả tệp và thư mục con bên trong.
  - Ví dụ:
    ```
    ln file1 file2
    ln -s /home/huylq/DATA1 /home/huylq/Documents
    ```
    
### RAID và các vấn đề liên quan
- RAID: Là việc lưu trữ dữ liệu trên nhiều ổ với mục đích tăng hiệu suất đọc ghi, tối ưu hóa việc sử dụng dung lượng lưu trữ. Đặc biệt là cơ chế dự phòng.
- Các loại RAID phổ biến:
  - RAID 0: Được hình thành từ 2 ổ trở lên và lưu trữ đều trên 2 ổ
    - VD: Với 8 đoạn dữ liệu 1 -> 8 thì RAID 0 sẽ lưu trữ các đoạn dữ liệu 1 cách xen kẽ trên 2 ổ, tức là các đoạn dữ liệu 1,3,5,7 sẽ được lưu tại ổ 1 và đoạn dữ liệu 2,4,6,8 sẽ được lưu tại ổ 2. Điều này giúp tận dụng tối đa sức mạnh của tất cả các ổ.
    - Ưu điểm: Hiệu suất đọc ghi tốt, tận dụng được tối đa khả năng của 2 ổ.
    - Nhược điểm: Khả năng về an toàn dữ liệu là chưa có bởi vì khi xảy ra sự cố trên 1 trong 2 ổ thì khả năng mất mát dữ liệu sẽ rất cao.
    - Phù hợp: Vì những ưu nhược điểm trên nên RAID 0 chỉ phù hợp với các ứng dụng cụ thể như Livestream, Video trực tuyến, ...
    - So sánh với ổ thường: RAID 0 đạt mức tốt trên các phương diện hiệu suất, tốc độ đọc ghi, ... Vấn đề tồn tại ở RAID 0 là về an toàn dữ liệu
  - RAID 1: Được cấu thành từ ít nhất 2 ổ. Các đoạn dữ liệu đuọc lưu trữ song song trên cả 2 ổ
    - VD: Có 4 đoạn dữ liệu. 4 đoạn dữ liệu này sẽ được lưu trữ song song trên cả 2 ổ. Tức là 1 ổ sẽ lưu trữ và 1 ổ sẽ backup lại dữ liệu từ ổ đã lưu trữ.
    - Ưu điểm: Ngược lại với RAID 0 thì RAID 1 có độ an toàn về dữ liệu ở mức tốt khi mà dữ liệu được lưu trữ song song trên 2 ổ, trong trường hợp 1 ổ xảy ra sự cố thì vẫn còn ổ còn lại lưu trữ dữ liệu.
    - Nhược điểm: Hiệu suất không cao. Khả năng ghi chậm hơn ổ thường vì phải ghi đồng thời lên 2 ổ riêng biệt.
    - Phù hợp: Dựa vào ưu nhược điểm thì cho thấy RAID 1 phù hợp với các dịch vụ yêu cầu về an toàn dữ liệu.
    - So sánh với ổ thường: Khả năng đọc ngang ngửa nhưng khả năng ghi chậm hơn nhiều vì phải ghi trên cả 2 ổ.
  - RAID 5: Cần tối thiểu 3 ổ để cấu thành. Cả 3 ổ sẽ trực tiếp lưu trữ dữ liệu khác nhau cùng với đó là quá trình tính toán giá trị chẵn lẽ dựa trên dữ liệu cũng được thực hiện sau đó được lưu vào từng ổ để có khả năng backup cho dũ liệu từng ổ.
    - VD: Có 6 đoạn dữ liệu 1,2,3,4,5,6 được sắp xếp ghi vào 3 ổ:
      -  Ổ 1: Lưu đoạn dữ liệu 1,2 và giá trị chẵn lẻ của đoạn dữ liệu này sẽ được lưu vào ổ 2
      -  Ổ 2: Lưu đoạn dữ liệu 3,4 và giá trị chẵn lẽ của đoạn dữ liệu này sẽ được lưu vào ổ 3
      -  Ổ 3: Lưu đoạn dữ liệ 5,6 và giá trị chẵn lẽ của đoạn dữ liệu này sẽ được lưu vào ổ 1
    - Tính chẵn lẻ: Các bước tính chẵn lẽ diễn ra như sau:
      - B1: Dữ liệu được chia thành các block
      - B2: Có 1 hàm toán học XOR được sử dụng để khi đưa các block(1 block thường 4KB - 512KB và tồn tai dưới dạng nhị phân) vào thì nó sẽ thực hiện tính toán. VD: `Dữ liệu ổ 1: 1110 0010` và `Dữ liệu ổ 2: 1000 1010` thì sau khi đưa vào hàm XOR sẽ cho ra đoạn dữ liệu sau `0110 1000` và được lưu vào ổ 3.
    - Ưu điểm: Cải thiện được các nhược điểm có ở RAID 0 và RAID 1. Nâng cao hiệu suất, đảm bảo khả năng về an toàn dữ liệu.
    - Nhược điểm: Dữ liệu chỉ đảm bảo khi có lỗi với 1 ổ nếu xảy ra lỗi trên 2 ổ đồng thời thì dữ liệu hoàn toàn có thể bị mất. Tải trọng cao cho bộ điều khiển RAID vì phải tính chẵn lẽ. Hiệu suất ghi khá chậm vì phải vừa tính chẵn lẽ vừa ghi dữ liệu.
    - Phù hợp: Với các ứng dụng lưu trữ, chia sẻ dữ liệu. Phù hợp với Server tập tin, Server web, Cloud Storage, ...
    - So sánh với ổ thường: Hiệu suất và dung lượng lưu trữ cao hơn so với sử dụng 1 ổ cứng duy nhất. Khả năng chịu lỗi tốt hơn, tiết kiệm chi phí khi so với sử dụng nhiều ổ riêng biệt có cùng dung lượng. Tuy nhiên việc triển khai RAID 5 khá khó khăn vì độ phức tạp. Khả năng mất mát dữ liệu vẫn có thể xảy ra nếu 2 ổ đồng thời bị lỗi.
- RAID cứng và RAID mềm:
  - RAID cứng là việc sử dụng bộ điều khiển chuyên dụng dể quản lý mảng RAID
  - RAID mềm là sử dụng phần mềm trên HĐH để quản lý mảng RAID.
  - Sự khác nhau giữa chúng dự trên: hiệu suất, độ tin cậy, chi phí, mức độ an toàn, khả năng mở rộng, khả năng tương thích.
- Sử dụng RAID để tăng hiệu suất đọc ghi của hệ thống, bảo vệ dữ liệu, tăng dung lượng, tăng mức độ tin cậy khi sử dụng, ... các yếu tố đánh giá để phù hợp với mục đích sử dụng.
#### Phần mềm mdadm: giúp tạo, quản lý và giám sát RAID
- **mdadm** là 1 tiện ích dòng lệnh mạnh mẽ được sử dụng để quản lý các thiết bị RAID bao gồm việc tạo, cấu hình, giám sát, sữa chữa các mảng RAID.
-  Tạo: Hỗ trợ nhiều cấp độ RAID 0 1 5 ...
  - Cú pháp:
        ```
        sudo mdadm --create --verbose /dev/md[*] --level=[*] --raid-devices=[*]  [Device1] [Device2] ...
        ```
    - Với:
      - `--create`: Biểu thị cho `mdadm` thực hiện thao tác tạo mảng RAID
      -  `--verbose`: Hiển thị thông tin chi tiết về quá trình tạo RAID
      -  `/dev/md[*]`: Xác định tên của thiết bị cho mảng RAID.
      -  `--level=[*]`: Các loại RAID 0,1,5, ...
      -  `--raid-devices=[*]`: Số lượng thiết bị tham gia vào RAID
      - `[Device1] [Device2]`: Danh sách các thiết bị tham gia vào RAID
      - Ngoài ra còn có các option khác: `--chuck`, `--metadata`, `--spare-devices`, `--name`, ...
  
        -> hiển thị chi tiết về mảng RAID bao gồm cấu hình RAID, trạng thái thiết bị, thông tin partie, tốc độ truyền dữ liệu, ...
       
    - Dừng mảng RAID và xóa 1 ổ khỏi mảng:
      - Cú pháp:
        ```
        sudo mdadm --stop /dev/md[*]
        ```
        -> Dừng mảng RAID, không cho nó hoạt động nữa.
        ```
        sudo mdadm --assemble /dev/md[*]
        ```
        -> Khởi động lại mảng RAID sau khi STOP
        ```
        sudo mdadm --remove /dev/md[*] [Device*]
        ```
        -> Xóa 1 thiết bị khỏi mảng RAID
#### Công cụ sysbench - Đánh giá hiệu suất của hệ thống
- **Sysbench**: Là 1 công cụ benchmark mã nguồn mở được sử dụng để kiểm tra và đánh giá hiệu suất trên hệ thống linux và các hệ điều hành khác. `sysbench` hỗ trợ các bài kiểm tra gồm cpu, I/O, bộ nhớ, ...
- Cài đặt `sysbench` trên Ubuntu:
  - B1: `sudo apt update`
  - B2: `sudo apt install sysbench`
- Các tính năng của `sysbench` để đánh giá hiệu suất
  - Kiểm tra CPU:
    - `sysbench --test=cpu run` hiển thị báo cáo hiệu suất tổng quan về cpu của hệ thống.
      
    ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/ef29de5c-359a-46ce-ab8e-bd5cb4d96b35)
    - Các thông số được thể hiện:
      - `events per second: 1359.61`: Hiển thị tốc độ xử lý của CPU được đo bằng số sự kiên( phép toán tìm số nguyên tố) mà CPU thực hiện trong mỗi giây. 1359,61/1s
      - `General statistics`:
        - `total time: 10.0001s`: Tổng thời gian thực hiện bài kiểm tra, khoảng 10 giây
        - `total number of events: 13598`: Tổng số sự kiện (phép toán tìm số nguyên tố) đã được thực hiện trong suốt bài kiểm tra. Giá trị này là 13598 sự kiện.
      - Latency (ms): 
        - `min: 0.73`: Độ trễ nhỏ nhất cho mỗi sự kiện là 0.73 mili giây.
        - `avg: 0.74`: Độ trễ trung bình cho mỗi sự kiện là 0.74 mili giây. Đây là giá trị trung bình của thời gian xử lý mỗi sự kiện.
        - `max: 1.10`: Độ trễ lớn nhất cho mỗi sự kiện là 1.10 mili giây.
        - `95th percentile: 0.77`: 95% của các sự kiện có độ trễ nhỏ hơn hoặc bằng 0.77 mili giây. Đây là một giá trị thống kê cho thấy mức độ phân phối của độ trễ.
        - `sum: 9997.09`: Tổng độ trễ của tất cả các sự kiện, tính bằng mili giây.
      - Threads fairness:
        - `events (avg/stddev): 13598.0000/0.00`: Giá trị trung bình và độ lệch chuẩn của số sự kiện mỗi luồng. Ở đây, giá trị trung bình là 13598 sự kiện mỗi luồng và độ lệch chuẩn là 0.00, cho thấy không có sự khác biệt giữa các luồng.
        - `execution time (avg/stddev): 9.9971/0.00`: Giá trị trung bình và độ lệch chuẩn của thời gian thực hiện mỗi luồng. Ở đây, giá trị trung bình là 9.9971 giây mỗi luồng và độ lệch chuẩn là 0.00, cho thấy tất cả các luồng thực hiện bài kiểm tra với thời gian gần như bằng nhau.
  - Kiêm tra bộ nhớ:
    - `sysbench --test=memory run` Hiển thị các số liệu thống kê về lượng bộ nhớ còn trống và đang được sử dụng.
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/2039d102-d5c5-475e-96ae-4b54d2e35021)
      - Các thông số được thể hiện:
        - `Total operations: 73212396 (7320234.85 per second)`: Tổng số thao tác (operations) đã được thực hiện trong suốt bài kiểm tra là 73212396. Tốc độ thực hiện thao tác là 7320234.85 thao tác mỗi giây.
        - `71496.48 MiB transferred (7148.67 MiB/sec)`: Tổng số dữ liệu đã được chuyển là 71496.48 MiB (MebiBytes). Tốc độ chuyển dữ liệu là 7148.67 MiB mỗi giây.
        - Thống Kê Chung (General statistics):
          - `total time: 10.0001s`: Tổng thời gian thực hiện bài kiểm tra là 10.0001 giây.
          - `total number of events: 73212396`: Tổng số sự kiện (events) đã được thực hiện trong suốt bài kiểm tra là 73212396.
        - Độ Trễ (Latency):
          - `min: 0.00`: Độ trễ nhỏ nhất cho mỗi sự kiện là 0.00 mili giây.
          - `avg: 0.00`: Độ trễ trung bình cho mỗi sự kiện là 0.00 mili giây.
          - `max: 0.03`: Độ trễ lớn nhất cho mỗi sự kiện là 0.03 mili giây.
          - `95th percentile: 0.00`: 95% của các sự kiện có độ trễ nhỏ hơn hoặc bằng 0.00 mili giây.
          - sum: 4658.10: Tổng độ trễ của tất cả các sự kiện, tính bằng mili giây.
        - Threads fairness:
          - `events (avg/stddev): 73212396.0000/0.00`: Giá trị trung bình và độ lệch chuẩn của số sự kiện mỗi luồng. Ở đây, giá trị trung bình là 73212396 sự kiện mỗi luồng và độ lệch chuẩn là 0.00, cho thấy không có sự khác biệt giữa các luồng.
          - `execution time (avg/stddev): 4.6581/0.00`: Giá trị trung bình và độ lệch chuẩn của thời gian thực hiện mỗi luồng. Ở đây, giá trị trung bình là 4.6581 giây mỗi luồng và độ lệch chuẩn là 0.00, cho thấy tất cả các luồng thực hiện bài kiểm tra với thời gian gần như bằng nhau.


  - Kiểm tra I/O: Các bước tiến hành:
    - B1: Tạo 1 file `sysbench fileio --file-total-size=5G --file-num=5 prepare` với tổng dung lượng là 5G và có 5 file được tạo ra. Ở đây chúng ta sẽ nhìn thấy tốc độ ghi:
     ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/66a62f2b-dcf7-4a04-9e1a-7d6dc8b09dbd)

    - B2: Ta kiểm tra tốc độ đọc bằng lệnh 'sysbench fileio --file-total-size=1G --file-num=1 --file-block-size=16M --file-test-mode=seqrd --time=300 run` với tổng dung lượng của file sử dụng để kiểm tra là 1Gb, số lượng tập tin được tạo và sử dụng trong bài kiểm tra là 1, Kích thước mỗi khối là 16M, Chế độ kiểm tra là đọc tuần tự (ngoài ra còn có chế độ `rndrd`: ngãu nhiên , ) với thời gian thực hiện 300s(5p).
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/4aa3db55-e534-46af-b0af-ee6bb9d8a325)

    - B3: Sau khi test xong , xóa 5GB đã tạo `sysbench --test=fileio --file-total-size=5G cleanup`
- Ứng dụng của `sysbench`:
  - Đánh giá hiệu suất: Kiểm tra và so sánh hiệu suất của các thành phần phần cứng và phần mềm trên máy tính or máy chủ
  - Kiểm tra sức mạnh của hệ thống: Đo lường khả năng xử lý của hệ thống trong các tình huống tải cao
  - Phát hiện nút thắt: Xác định các yếu tố giới hạn hiệu suất của hệ thống
#### Thực hiện bài LAB dựa trên những lý thuyết tìm hiểu ở trên và có những kết luận như sau:
- So sánh RAID 0 và RAID 1:
  - Khả năng write:
    - RAID 0: Tốc độ tốt nhất
      
       ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/6d4188c7-517b-4a09-af71-6b7127aa55b2)


    - RAID 1: Tốc độ trung bình khá
      
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/85cd3b42-26a2-4195-b9db-81b9863d61b7)

  - Khả năng read: 
    - RAID 0: 
    
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/0f8e68f1-723d-44ed-bcda-8ccec0f3f0ab)


    - RAID 1: 
      
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/21946cec-f6ba-4e5b-a5d5-571c7bc98d0b)


- So sánh RAID 0 với ổ thường:
  - Khả năng write:
    - RAID 0: 

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/5903a10a-74c8-4da0-a773-d790d93cbe2e)


    - Ổ thường: 

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/0aba0026-84c3-434d-a061-c92b992b2e1c)

  - Khả năng read:
    - RAID 0: 

       ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/a6806d26-ada6-4e79-9655-15ccb6fc473b)


    - Ổ thường:
      
      

- So sánh RAID 1 với ổ thường
  - Khả năng write
    - RAID 1:
      
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/68b619ef-4d6f-4a76-b0b5-eb8a3d966fd9)

    - Ổ thường:

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/cfd0e789-f997-4fb2-b847-c6f6ba2b96c3)
 

  - Khả năng read
    - RAID 1:
      
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/70fc31cc-a335-4145-846f-ed225c87dac9)
      
    - Ổ thường:


    ###### Kết luận
  - Khả năng đọc và ghi tốt nhất là RAID 0 khi so với ổ thường và RAID 1
  - Khả năng ghi của RAID 1 chậm hơn ổ thường 1 chút. Khả năng đọc của RAID 1 tốt hơn ổ thường  
### Log và Logrotate và các vấn đề liên quan

### Cấu hình IP tĩnh IP động 
### Cron, at và các công cụ tự đông hóa
### Các dịch vụ DNS và DHCP
### SSH và các lệnh sao chép SCP và đồng bộ hóa Rsync
