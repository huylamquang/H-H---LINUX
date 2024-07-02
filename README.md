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
- Các khái niệm cơ bản
- Các lệnh sử dụng để quản lý và giám sát tiến trình: top, htop, ps
### Phần mềm và các vấn đề liên quan đến phần mềm
- Các khái niệm cơ bản liên quan đến phần mềm
- Các trình quản lý phần mềm 
### FS, Partition, Mount và các vấn đề liên quan
- Các khái niệm về FS Partition và Mount
- Các lệnh được sử dụng và chức năng cách sử dụng chúng
### RAID và các vấn đề liên quan
- Các khái niệm về RAID:
- Các lệnh và phần mềm mdadm để quản lý RAID mềm
### Log và Logrotate và các vấn đề liên quan
### Cấu hình IP tĩnh IP động 
### Cron, at và các công cụ tự đông hóa
### Các dịch vụ DNS và DHCP
### SSH và các lệnh sao chép SCP và đồng bộ hóa Rsync
