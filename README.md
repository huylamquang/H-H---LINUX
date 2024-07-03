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
#### Các lệnh nâng cao thao tác với văn bản
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
- Byobu là 1 tiện ích để tạo ra các phiên làm việc. Với các tiện ích có thể cần như tạo, sửa xóa, chia đôi màn hình,...
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
### RAID và các vấn đề liên quan
- Các khái niệm về RAID:
- Các lệnh và phần mềm mdadm để quản lý RAID mềm
### Log và Logrotate và các vấn đề liên quan
### Cấu hình IP tĩnh IP động 
### Cron, at và các công cụ tự đông hóa
### Các dịch vụ DNS và DHCP
### SSH và các lệnh sao chép SCP và đồng bộ hóa Rsync
