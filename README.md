 # HỆ ĐIỀU HÀNH LINUX 
## Các khái niệm và thao tác được sử dụng trong Linux
### 1. Các lệnh được sử dụng để thao tác với văn bản
#### Các lệnh cơ bản thao tác với văn bản
- `pwd`: Chuyển hướng thư mục làm việc
- history: Lệnh sử dụng để xem các lệnh đã được sử dụng trong quá khứ
  - `Ctrl + R`: Tìm lệnh đã từng sử dụng trong quá khứ
  - `Ctrl + S`: Stop công việc đang làm, hiểu như là treo máy và không làm gì cả. Ctrl + Q: để thoát ra khỏi chế độ stop công việc
- `cd`: Chuyển hướng thư mục làm việc
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
- `cat`: sử dụng để đọc file, nối file, tạo file, ...
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
- `sort`: Là lệnh được sử dụng để sắp xếp cùng với các option sử dụng( mặc định là sắp xếp số trước, sau đó là sắp xếp theo ký tự từ A-Z - Sắp xếp theo cột đầu tiên).
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
      
- `uniq`: Lệnh được sử dụng để loại bỏ các trùng lặp và chỉ loại bỏ các trùng lặp liên tiếp vì thế thường được sử dụng với `sort` để có thể loại bỏ hoàn toàn trùng lặp.
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
- `wc`: Là lệnh được sử dụng để in ra thông tin về số từ, số byte, số dòng và namefile
  - Cú pháp:
    ```
    wc [option] [name_file]
    ```
    - Các option được sử dụng là:
      - `-c`: Hiển thị số byte của tệp
      - `-L`: Hiển thị dòng dài nhất của tệp
      - `-l`: Hiển thị số dòng
      - `-m`: Hiển thị số ký tự của tệp
      - `-w`: Đếm số từ và hiển thị số từ của tệp, phân tách nhau bằng khoảng trắng
    - Ví dụ:
      ```
      wc -c file1
      wc -L file1
      wc -mw file1
      ```
- `split`: sử dụng để quản lý các tệp lớn có chức năng chia file thành các file nhỏ hơn và truyền tệp qua mạng có băng thông hạn chế, sử dụng với các công cụ khác.
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
- `cut`: Sử dụng để trích xuất các cột và các trường, thay thế ký tự cần thiết trong văn bản và có khả năng kết hợp tệp văn bản
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
    cut -d':' -f1 file1
    paste <(cut -d' ' -f1 file3) <(cut -d' ' -f3 file4) --> In ra cột thứ 1 của file 3 và cột thứ 3 của file1
    ```
- `head`: Sử dụng để hiển thị nội dung của 10 dòng đầu tiên trong văn bản
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
- `tail`: Lệnh sử dụng để hiển thị nội dung của các dòng cuối trong văn bản
  - Cú pháp:
    ```
    tail [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-n`: Hiển thị số dòng cuối cùng cần hiển thị
    - `-c`: Hiển thị số lượng byte cuối cùng được chỉ định
    - `-f`: Hiển thị các dòng mới được thêm vào tệp theo thời gian thực -> Được sử dụng trong việc kiểm tra các file log.
  - Ví dụ:
    tail -n 20 file1
    tail -c 50 file1
    tail -f /var/log/syslog 
- `less`: Dùng để đọc các file lớn, có thể cụôn trang lên hoặc cuộn trang xuống. Tìm kiếm trên, tìm kiếm dưới và được sử dụng để đọc các file log
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
- `tac`: Là lệnh sử dụng để đọc file nhưng được sắp xếp từ dưới lên
  - Cú pháp:
    ```
    tac [option] [name_file]
    ```
  - Các option được sử dụng là:
    - `-n`: Hiển thị số dòng trước mỗi dòng đầu ra được đảo ngược
  - Ví dụ:
    ```
    tac -n file1
    ```
#### 2. Các lệnh nâng cao thao tác với văn bản
- `grep`: Là lệnh được sử dụng để tìm kiếm chuỗi trong văn bản. Thường kết hợp với biểu thức chính quy để tìm kiếm sđt, ngày tháng năm, địa chỉ ip, ... có tỏng văn bản.
  - Cú pháp:
    ```
    grep [option] [pattern] [name_file]
    ```
  - Các option được sử dụng là:
    - `-i`: Không phân biệt chữ hoa chữ thường
    - `-v`: In ra các dòng không chứa kết quả
    - `-c`: In ra số lượng kết quả khớp.
    - `-n`: In ra kết quả khớp + số dòng
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
- `sed`: Là trình chỉnh sửa luồng để lọc, được sử dụng để lọc và thực hiện các thao tác nâng cao bao gồm thay thế, thêm, sửa, xóa văn bản.
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
      Thực hiện viêc thay thế pattern thành replace trên file1 với 's' là tuỳ chọn được sử dụng để thay thế, 'g' là cờ toàn cục, tức nó sẽ thay đổi tất cả mẫu có trong 1 phạm vi nếu không có 'g' thì nó chỉ thay đổi các mẫu ở cột đầu tiên của mỗi dòng. Nếu mẫu rỗng thì nó sẽ không làm gì cả -> Chỉ có tác dụng với mẫu chỉ định.
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
- `awk`: Là 1 ngôn ngữ giúp chúng ta thao tác dễ dàng với kiểu dữ liệu có cấu trúc và tạo ra những kết quả được định dạng. Được sử dụng để tìm kiếm và xử lý file text.
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
        + $2: Chứa văn bản trường thứ hai
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
    - Cách thực diễn ra như sau: Để bước vào chế độ vim ta nhấn `v`. Từ vị trí nhấn `v` ta có thể sử dụng các phím điều hướng để bôi đen đoạn văn bản or sử dụng tổ hợp v + số dòng( tính từ vị trí con trỏ + số dòng). Sau đó nhấn `y` để copy đoạn vừa bôi đen or nhấn `d` để xóa. Có thể dán đoạn vừa copy bằng cách sử dụng `p` tại vị trí cần dán.
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
   - Lệnh `htop`: Là 1 lệnh được sử dụng để giám sát tiến trình, hiển thị các thông số về cpu, ram, loadavg, ... tương tự như top nhưng được hiển thị bằng các mầu sắc 1 cách trực quan hơn.
     - Trong htop có thể sử dụng phím F1 để xme các hướng dẫn cụ thể hơn
 
       ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/afbf9e4f-d2c0-4c5b-afcc-b9dc604d907a)

     - Các màu sắc được biểu thị trong htop:
       - Với CPU:
         - Xanh lam: Các tiến trình với độ ưu tiên thấp
         - Xanh lục: Các tiến trình người dùng
         - Đỏ: Các tiến trình hạt nhân
         - Xám: Thời gian chờ IO
       - Với Mem:
         - Xanh lục: Bộ nhớ đã dùng
         - Xanh dương: Bộ nhớ buffers( sử dụng để tạm thời lưu trữ dữ liệu di chuyển giữa các thiết bị phần cứng và bộ nhớ chính).
         - Vàng: Bộ nhớ cache( sử dụng để lưu trữ các bản sao của dữ liệu từ bộ nhớ chính để truy cập nhanh hơn). 
       - Với Swap:
         - Đỏ: Bộ nhớ swap đã sử dụng
         - Vàng: Bộ nhớ cache đã sử dụng
   - Lệnh `kill` và `kill -9` cùng các loại tín hiệu:
     - Lệnh `kill` và `kill -9`
       - `kill [PID]` là kiểu thường, kiểu tín hiệu là sigterm, cho phép tiến trình hoàn thành và giải phóng tài nguyên và tiến trình có khả năng xử lý or chặn tín hiệu này tức là bỏ qua yêu cầu này nếu cần thiết.( Cho phép tiến trình dọn dẹp, lưu trạng thái làm việc, thực hiện các hành động dọn dẹp trước khi kết thúc).
       - `kill -9 [PID]` Là kiểu dứt điểm, kiểu tín hiệu là sigkill, bắt buộc chấm dứt ngay lập tức, không cho cơ hội làm thêm gì cả.
     - Các loại tín hiệu phổ biến:
       - Tín hiệu KILL: Các tín hiệu khác có thể chọn xử lý tín hiệu được đưa đến, có thể bỏ qua các tín hiệu đó còn tín hiệu kill là chấm dứt hoàn toàn. Tức là Kernel sẽ ngay lập tức chấm dứt tiến trình.
       - Tín hiệu SIGHUP (1): Tín hiệu này thường được dùng để thông báo cho tiến trình rằng kết nối terminal đã bị ngắt. Nó cũng được dùng để yêu cầu tiến trình đọc lại các tệp cấu hình.
       - Tín hiệu SIGINT (2): Tín hiệu này gửi từ bàn phím khi người dùng nhấn `Ctrl+C`. Nó yêu cầu tiến trình kết thúc.
       - Tín hiệu SIGSTOP (19): Tín hiệu này tạm dừng tiến trình ngay lập tức.
       - Tín hiệu SIGCONT (18): Tín hiệu này tiếp tục tiến trình đã bị tạm dừng bởi `SIGSTOP`
   - Lệnh ps: Hiển thị các thông tin về tiến trình nhưng tại 1 thời điểm cố định
     - Các tùy chọn:
       - `ps x`: hiển thị các tiến trình hiện có
       - `ps aux`: Hiển thị tất cả các tiến trình đang chạy với những thông in chi tiết:
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
  - `dpkg`: Trình quản lý phần mềm được sử dụng để cài đặt, gỡ bỏ phần mềm
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
- Sử dụng `StartUp Scripts`: Tự động hóa các tác vụ sau khi hệ thống khởi động
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
    - **Ext4**: Là 1 dạng FS có khả năng journaling, tương thích phần cứng, dung lượng cao, hiệu suất cao,... Không giới hạn về thư mục con trong 1 thư mục, có kích thước cố định. Sử dụng kĩ thuật phân bố trễ tức là nó sẽ trì hoãn phân bố các block trước khi dữ liệu được đưa vào để có thể tối ưu hóa không gian lưu trữ và chống phân mảnh dữ liệu. Phù hợp với những tệp nhỏ, bảo vệ hệ thống tệp và thư mục mở rộng. Phù hợp với máy chủ tệp trung tâm để chia sẻ nhóm. 
    - **XFS**: Là 1 FS có khả năng journaling, và vô số tính năng tiên tiến như Snapshots, Quotas, ACLs, ... Phù hợp với các hệ thống tệp tin lưu trữ dữ liệu dung lượng lớn or có nhiều tập tin nhỏ, hiệu suất truy cập dữ liệu cao. Phù hợp với Khoa học dữ liệu(ML, DL, …). Phù hợp với việc truy xuất các tệp lớn mà không ảnh hưởng đến hiệu suất.
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
- Lệnh `Fdisk`: Được sử dụng để tạo phân vùng trên ổ đĩa
- Lệnh `lsblk`: Sử dụng để hiển thị các phân vùng cùng với mount thư mục nào. Sử dụng thêm tùy chọn -f để xem các phân vùng sử dụng FS nào. Thường được dùng trước khi tạo phân vùng.
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
 - Lệnh `mkfs`: Được sử dụng để tạo FS sau khi tạo phân vùng
   - Cú pháp:
     ```
     mkfs -t [FS] -L [Label_name] /dev/sda1
     ```
   - Option:
     - `-t`: type fs được sử dụng
     - `L [name]`: gắn nhãn [name]
     - `-f`: Bỏ qua bất kỳ lỗi nào xảy ra trong quá trình tạo FS
 - Lệnh `Mount` và `Umount`: Sử dụng để gán 1 pv vào 1 thư mục được chỉ định.
   - Cú pháp:
     ```
     mount -t [FS] /dev/sda1 [path_to_folder]
     ```
   - Mục đích sử dụng: Dễ dàng truy cập, sử dụng. Thực hiện các thao tác 1 cách dễ dàng và nhanh chóng. Có khả năng gắn kết các phân vùng vào thư mục với các kiểu định dạng FS khác nhau để phù hợp với mục đích sử dụng.
   - `Umount`: Sử dụng để bảo vệ dữ liệu, giải phóng thiết bị lưu trữ, giải quyết sự cố khi gặp lỗi
   - Cú pháp: `umount /dev/sda1`
- Lệnh `fsck`: Được sử dụng để sửa lỗi FS. fsck là giao diện chung cho các công cụ check và sửa các loại fs khác nhau. Ứng với mỗi loại công cụ là 1 loại fs.
  - Cú pháp:
    ```
    fsck -t [FS] /dev/sda1
    ```
  - Ví dụ:

     ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/ba6eeaf2-6ca8-43ed-91f3-e997ef806f2a)
    - Các thông số được hiển thị bao gồm: Số file/Tổng số file, Số lượng block/Tổng số blocks:
    - Tác dụng của `Fsck` là:
      - Kiểm tra tính nhất quán của tệp: Fsck sẽ quét hệ thống tệp để xác định và sửa chữa các lỗi logic nếu thấy có lỗi về inode hoặc bản ghi metadata bị sai thì nó sẽ fix trực tiếp.
      - Sửa chữa lỗi hệ thống của tệp: Dựa vào các lỗi phát hiện được thì fsck hoàn toàn có thể sửa chữa được các lỗi hệ thống tệp phổ biến. Đối với các loại lỗi nghiêm trọng thì fsck sẽ đề xuất cho các user sữa chữa thủ công or là sao lưu dữ liệu trước khi sửa chữa.
      - Phục hồi dữ liệu: Tùy thuộc vào mức độ nghiêm trọng của lỗi và mức độ hỏng của hệ thống tệp, khả năng khôi phục dữ liệ của fsck được sử dụng trong 1 số trường hợp.
      - Sử dụng thường xuyên để kiểm tra và sữa chữa hệ thống tệp. Đặc biệt là sau khi xảy ra các sự cố đột ngột như cúp điện, ... Trước khi định dạng hệ thống tệp cũng nên sử dụng fsck để kiểm tra và sửa lỗi.
- Lệnh `df` và `du` sử dụng để xem dung lượng file, block, inode được sử dụng
  - Lệnh `df`: sử dụng để hiển thị tổng quan về dung lượng của toàn bộ hệ thống(mặc định hiển thị dưới dạng block)
    
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
      - **Block**: là 1 đơn vị lưu trữ dữ liệu trên ổ. Kích thước thông thường là 4Kb, 8Kb, 16Kb. Kích thước càng lớn tốc độ càng nhanh nhưng ảnh hưởng đến việc tối ưu hóa dung lượng. 1 file có thể chứa nhiều blocks. Việc sử dụng block cho 1 file phụ thuộc vào kích thuớc của file.
      - **Inode**: là 1 dạng cấu trúc dữ liệu lưu trữ thông tin về metadata bao gồm: quyền, kích thước, số lượng blocks, đường dẫn đến các dữ liệu của file, ...
  - Lệnh `du`: Sử dụng để hiển thị chi tiết dung lượng từng file, thư mục tại vị trí sử dụng.
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
  - Lệnh `which`: Lệnh sử dụng để tìm kiếm đường dẫn đến 1 thư mục, file
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
  - Lệnh `whereis`: Tượng tư như which nhưng có thêm đường dẫn đến thư mục man của lệnh đó
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
  - Lệnh `locate`: Lệnh tìm kiếm, thường được sử dụng cùng grep. Lệnh này tìm kiếm được dựa trên csdl có sẵn vì vậy trước khi tìm kiếm nên sử dụng lênh `updatedb` để có thể làm mới CSDL để có thể tìm kiếm dễ dàng và chính xác hơn. Sử dụng CSDL mlocate được tạo và cập nhật định kỳ để tìm kiếm file và thư mục.
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
 - Lệnh `find`: Lệnh tìm kiếm file hoặc thư mục trực tiếp trong hệ thống tệp tin. Có thể sử dụng được nhiều tiêu chí khác nhau để tìm kiếm bao gồm:
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
- Lệnh `ls`: Là lệnh sử dụng để xem thông tin các file và thư mục có trong thư mục đang làm việc
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
- Lệnh `touch`: Tạo file đơn giản
  - Cú pháp:
    ```
    touch [name_file]
    ```
- Lệnh `cp`: Lệnh copy nd của 1 file vào thư mục hoặc của 1 thư mục vào 1 thư mục.
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
- Lệnh `mv`: Di chuyển file or thư mục đến nơi khác và có thể đổi tên.
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
- Lệnh `rm`: Lệnh được sử dụng để xóa file, thư mục trong thẩm quyền của nó khỏi thư mục đang làm việc
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
- Lệnh `ln`: Lệnh đực sử dụng để gắn syslink vào thư mục or file
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
     ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/0c784ec8-bbf2-482f-9ad3-78cd1e3b01aa)


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

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/6de46a4d-3c58-45fa-91a9-37db74b372a1)

      

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
 
      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/b5024d36-601e-41eb-92f5-b13b626177b8)



    ###### Kết luận
  - Khả năng đọc và ghi tốt nhất là RAID 0 khi so với ổ thường và RAID 1
  - Khả năng ghi của RAID 1 chậm hơn ổ thường 1 chút. Khả năng đọc của RAID 1 tốt hơn ổ thường  
### Log và Logrotate và các vấn đề liên quan
- Logfile là những file liên quan đến nhật ký hoạt động của HĐH, nó chứa tất cả các thông tin quan trọng trong quá trình sử dụng HĐH: Tất cả các lỗi(phần cứng, phần mềm), quá trình khởi động hệ thống, quá trình đăng nhập, quá trình đăng nhập, ... Là nơi lưu trữ các thông tin, sự kiện quan trọng cùng những cảnh báo cụ thể.
- Nội dung của file log thông thường gồm: Log về thông tin hệ thống( boot.log, kern.log, dmesg.log, syslog, ...), Log về thông tin bảo mật(auth.log, wtmp, btmp, ...), Log thông tin về các ứng dụng( apache2, nginx, ...), Log về thông tin mạng(syslog, kernlog, dmesg.log, ...).
- Vị trí: Filelog nằm trong /var/log
- Các file :
  - **wtmp**: Chứa các bản ghi đăng nhập. Được sử dụng để tìm ra ai đã đăng nhập vào hệ thống( lệnh `who` được sử dụng trong filelog này để hiện thị thông tin).
  - **btmp**: Các thông tin đăng nhập không thành công
  - **vnetlib**: Là 1 thư viện mã nguồn mở cung cấp các chức năng mạng cho ứng dụng Python. Được sử dụng phổ biến trong các ứng dụng web và mạng để thực hiện các tác vụ như: gửi và nhận yêu cầu HTTP, quản lý kết nối TCP/IP, ...
- Các thư mục chính trong /var/log:
  - **Apache2**: Liên quan đến máy chủ web, lưu lại các yêu cầu truy cập vào máy chủ web và các lỗi xảy ra trên máy chủ web( lỗi ứng dụng, cấu hình, phần cứng, ...). Ghi lại địa chỉ IP và ID người dùng của tất cả máy khách thực hiện yêu cầu đến máy chủ. Lưu trữ thông tin về trạng thái của các yêu cầu truy cập cho dù phản hồi đã được gửi thành công hay yêu cầu dẫn đến lõi. Chứ các filelog:
    - **Error**: Ghi lại những thông tin lỗi gặp phải của httpd
    - **Access.log**: Ghi lại những thông tin về các yêu cầu nhận xác thực qua HTTP.
  => Được sử dụng khi gặp bất kỳ sự cố nào liên quan đến máy chủ Apache.
  - **Nginx**: Tương tự như apache2
  - **cups**: Liên quan đến in ấn
  - **openvpn**: : Liên quan đến kết nối VPN gồm lỗi và các sự kiện quan trọng.
  - **sysstat**: Công cụ giám sát hệ thống
  - **journal**: Chứa các tệp nhật ký được tạo bởi hệ thống systemd trong hệ điều hành Linux. Systemd là quá trình quản lý hệ thống chịu trách nhiệm khởi động và quản lý các dịch vụ hệ thống đồng thời cũng bao gồm hệ thống ghi nhật ký tích hợp.
  - **installer**: Chứa các tệp nhật ký liên quan đến quá trình cài đặt hệ thống.
  - **unattended-upgrades**: Là 1 gói tin ubuntu liên quan đến khả năng tự động cài đặt phần mềm.
-  Các filelog chính trong /var/log:
  - **boot.log**: Là nơi ghi lại các sự kiện xảy ra trong quá trình khởi động hệ thống, bao gồm tạo phần cứng tải kernel và khởi động dịch vụ. Được kiểm tra khi gặp các vấn đề liên quan đến tắt máy không đúng cách, khởi động lại hoặc khởi động lỗi hoặc là để xác định thời gian ngừng hoạt động của hệ thống do tắt máy đột ngột.
  - **kern.log**: Kern là lõi của HĐH. Chứa các thông báo do kernel tạo ra, như sự cố phần cứng, sự cố trình điều khiển và sử dụng tài nguyên hệ thống. Được kiểm tra khi có lỗi xả ra với kernel hoặc có thể sử dụng khi gỡ lỗi các vấn đề phần cứng.
  - **auth.log: Liên quan đến xác thực và ủy quyền: Các log này ghi lại các nỗ lực xác thực(đăng nhập ssh, sử dụng sudo, ...) và các sự kiện ủy quyền, bao gồm thành công và thất bại. Được sử dụng để theo dõi bảo mật, các vấn đề liên quan đến an toàn( điều tra các cuộc tấn công và các lỗ hổng liên quan đến cơ chế ủy quyền của người dùng).
  - **dpkg.log**: Là tệp ghi lại các thông tin của dpkg( trình quản lý gói của debian) cung cấp thông tin theo dõi việc cài đặt, gỡ cài đặt, cập nhật gói, theo dõi các thay đổi được thực hiện đối với phần mềm hệ thống. Được sử dujg khi muốn kiểm tra phần mềm đã được cài đặt hay gỡ bỏ chính xác hay chưa. Kiểm tra khi thấy máy chủ có những hoạt động bất thường và nghi ngờ do phần mềm.
  - **dmesg.log**: Theo dõi hoạt động hệ thống bao gồm các log liên quan đến thông báo khơi động kernel( giống kern.log) nhưng cũng có thể bao gồm thông tin động như phát hiện thiết bị phần cứng và tải trình điều khiển. Trong quá trình khởi động kernel phát hiện các thiết bị phần cứng vật lý được liên kết trong quá trình khởi động, nó sẽ ghi lại trạng thái thiết bị, lỗi phần cứng và các thông báo chung khác. Được kiểm tra khi mà có thiết bị phần cứng nào đó hoạt động không đúng hoặc không được phát hiện.
  - **apport.log**(báo cáo lỗi và lỗi): Dịch vụ này tạo ra các log báo cáo về lỗi cũng như là sự cố khi vận hành và sử dụng ứng dụng. Những thứ này sẽ được gửi tới cho nhà phát triển để họ khắc phục sự cố phù hơp với cài đặt phần mềm và gỡ bỏ phần mềm.
  - **alternatives.log**: Liên quan đến việc thay đổi các liên kết tuợng trưng của hệ thống - Sử dụng để theo dõi các thay thế liên kết tượng trưng của hệ thống, chuẩn đoán sự cố, giải quyết xung đột liên kết tượng trưng.
  - **syslog**: Là filelog đầu tiên cần kiểm tra khi mà gặp sự cố nào đó vì nó chứa tất cả dữ liệu hoạt động trên toàn bộ hệ thống: tệp nhật ký trung tâm ghi lại thông báo từ nhiều dịch vụ và ứng dụng của hệ thống. Hoạt động như 1 bộ thu thập tất cả cho nhật ký không được hướng trực tiếp đến nơi khác. Cung cấp cái nhìn rộng hơn về hoạt động của hệ thống. Tức là những cái nào không có tệp log cố định thì sẽ được lưu ở đây.
  - **ubuntu-advantage**: Là 1 dịch vụ có trả phí của ubuntu dành cho người dùng sử dụng các dịch vụ như: cập nhật phần mềm mở rộng, hỗ trợ kỹ thuật, ...
  - **lastlog**: Ghi lại những lần đăng nhập thành công gần nhất của mỗi tài khoản user trên hệ thống.
  - **faillog(có hoặc không)**: Theo dõi các nỗ lực đăng nhập thất bại, hỗ trợ theo dõi bảo mật, phát hiệ ra các cuộc tấn công. Được sử dụng để tìm ra các vi phạm bảo mật liên quan đến việc hack username và passwd.
  - **frontconfig.log**: Liên quan đến font chữ, kiểu chữ.
  - **gpu-manager.log**: Lưu trữ nhật ký hoạt động của trình quản lý GPU. Trình quản lý các GPU( card độ họa) trong hệ thống.
  - **cronlog**: Lưu trữ các thông tin liên quan đến crond ví dụ như tiến trình nền cron khởi tạo 1 công việc, các thông báo lỗi liên quan. Tức là khi cron chạy 1 công việc được lập lịch trước đó thì những thông tin liên quan về tiến trình chạy công việc đó sẽ được lưu trong tệp nhật ký này bao gồm thực thi thành công, các thông báo lỗi nếu thực thi thất bại.
- Logrotate và các tham số được sử dụng trong logrotate:
  
  ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/6e92ffed-3120-41f3-87a4-ddceb5699c44)

  - Logrotate: Là 1 tiện ích quản lý nhật ký hệ thống trong HĐH Linux. Nó được thiết kế để tự động xoay, nén, xóa các tập tin nhật ký cũ, giúp quản lý dung lượng đĩa và duy trì các tập tin nhật ký 1 cách có hệ thống.
  - Các tham số được sử dụng trong logrotate:
    - `rotate 4`: được hiểu là giữ lại 4 file với giá trị 4 có thể thay thế
    - `weekly`: Được hiểu công việc được diễn ra hàng tuần và có thể thay thế bằng `daily`, `yearly`, ...
    - `notifempty`: Không thực hiện `logrotate` trên các file log trống.
    - `missingok`: Vẫn thực hiện dù cho file không tồn tại.
    - `compress`: Nén file có thể thay thế bằng `nocompress`
    - `delaycompress`: Tức là sẽ không thực hiện nén file ngay lập tức mà chờ đến lượt sau mới nén nó.
    - `sharescripts`: Tạo ra bản sao duy nhất cho khối tập lệnh ở giữa `postrotate`( chạy lệnh sau khi logrotate) và `endscript`( chạy sau khi logrotate) - `prerotate`(chạy lệnh trước khi logrotate). (sử dụng để chạy tập lệnh cho lần rotate tiếp theo).
    - `create 0640 root adm`: cấp quyền cho fiel mới được tạo với chủ sỡ hữu là root và gr là adm với quyền 640(-rw-r-----).
    Ngoài ra còn có 1 số lệnh được sử dụng:
      - `nocreate`: Ngăn logrotate không tạo tệp log mới nếu tệp log không tồn tại.
      - `error`: Sử dung khi muốn nhận thông báo nếu tệp log không tồn tại.
      - `startsize`: sử dụng để chỉ định kích thước ban đầu cho tệp log
      - `copytruncate`: sử dụng để sao lưu tệp log trước khi logrotate. Nhưng nó sẽ cắt bớt tệp log sao cho đến kích thước của tệp log gốc.
  - Mục đích của việc sử dụng filelog là:
    - Khi có lỗi xảy ra, người quản trị có khả năng đưa ra phân tích và phương án giải quyết vấn đề 1 cách nhanh chóng khi filelog cung cấp chi tiết về các thông tin.
    - Giúp Sysadm tìm thấy những rủi ro tiềm ẩn và kịp thời đưa ra phương án giải quyết 1 cách sớm nhất.
    - Bảo mật là theo dõi các log bảo mật để tránh những truy cập trái phép.
  - Cách để đọc filelog hiệu quả:
    - Sử dụng các công cụ phù hợp với logfile:
      - Trình soạn thảo văn bản Vim:
      - Trình xem log và phân tích log chuyên dụng:  ELK stack, graylog, ...
    - Hiểu biết về các định dạng filelog: Dạng văn bản thông thường và các định dạng nâng cao như `json`, `xml`, ...
    - Tìm kiếm từ khóa và sử dụng biểu thức chính quy dựa trên các công cụ soạn thảo hoặc trình xem log.
    - Lọc dữ liệu: 1 số công cụ phân tích log cho phép lọc
    - Ghi lại các thông tin quan trọng trong quá trình kiểm tra các filelog
    - Kiên nhẫn: Quá trình tìm kiếm diễn ra khá tẻ nhạt, nhàm chán vì vậy cần có sự kiên nhẫn để tìm ra vấn đề và giải quyết vấn đề đó.
### Quản lý và phân quyền cho user, group
#### Quản lý chủ sỡ hữu và nhóm sở hữu
- Là việc thay đổi quyền sỡ hữu file và thư mục cho user, group.
- Các lệnh được sử dụng:
  - Quản lý về chủ sở hữu user, group: Chown
    - Cú pháp:
      ```
      chown [option] [user_name]:[group_name] [path_to file or dir]
      ```
    - Các option được sử dụng:
      - `-R`: thay đổi quyên sỡ hữu cho tất cả các tệp tin và thư mục con trong thư mục
      - `-v`: Hiển thị thông tin chi tiết về các thay đổi được thực hiện
      - `-c`: Hiển thị thông tin chi tiết chỉ khi có thay đổi được thực hiện
      - `-f`: Không hiển thị lỗi nếu lệnh không thể thay đổi quyền sỡ hữu của 1 tệp tin or thư mục.
    - Ví dụ:
      ```
      chown -R huylq:huylq /home/huylq/Desktop/DATA5
      chown -v huytl:huylq /home/huylq/Desktop/file1
      ```
  - Quản lý về chủ sỡ hữu group: Chgrp
    - Cú pháp:
      ```
      chgrp [option] [group_name] [path_to file or dir]
      ```
    - Các option được sử dụng:
      - `-R`: thay đổi nhóm sỡ hữu đệ quy(bao gồm thư mục con và các tệp con có trong thư mục
      - `-v`: hiển thị thông tin chi tiết về các thay đổi khi thực hiện lệnh
    - Ví dụ:
      ```
      chgrp -Rv huytl /home/huylq/Desktop/file5
      ```
#### Quản lý phân quyền cho user và group
- Là việc quản lý các quyền đọc, ghi, thực thi của file và thư mục.
  - Quyền `R`: Read - cho phép mở và đọc file. Lưu ý đối với Directory thì nếu có quyền `X` thì phải có thêm `R`
  - Quyền `W`: Wirte - Cho phép thực hiện thao tác ghi và cắt tệp nhưng không cho phép xóa và đổi tên. Xóa và đổi tên phụ thuộc vào thuộc tính của thư mục. Đối với Directory là cho phép tạo, xóa, đổi tên
  - Quyền `X`: Executive - Cho phép 1 tập tin được xử lý như một chương trình và thực thi. Các file script phải có cả quyền `R` để có thể thực thi.
- Với hệ bát phân:
  - Quyền `R`: tương đương với 4
  - Quyền `W`: tương đương với 2
  - Quyền `X`: tương đương với 1
- Các lệnh được sử dụng:
  - Lệnh chmod: sử dụng để phân quyền cho các file or thư mục với quyền `R`, `W`, `X`
    - Cú pháp:
      ```
      chmod [option] MODE [path_to file or dir]
      ```
      - Với các option: `-R`, `v`, `c`, `f` Tương tự
      - Với các mode:
        - Dạng ký hiệu:
          - `u`: chủ sỡ hữu
          - `g`: nhóm sỡ hữu
          - `o`: khác
          - `a`: tất cả
        - Các quyền:
          - `r` - quyền đọc, `w` - quyền ghi, `x` - quyền thực thi
          - Hệ bát phan: `4` - quyền đọc, `2` - quyền ghi, `1` - quyền thực thi, `0` - không có quyền
        - Các phép toán:
          - `+`: thêm quyền
          - `-`: bỏ quyền
          - `=`: đặt quyền chính xác
        - Ví dụ:
          ```
          chmod -R +rx /home/huylq/Desktop/file2
          chmod -v -rw /home/huylq/Desktop/file1
          chmod  u=rw,g=rw,o=x  /home/huylq/Desktop/file3
          chmod 444 /home/huylq/Desktop/DATA5
          ```
#### Tạo sửa xóa User,Group 
- Tạo user, group: Là việc tạo ra 1 user mới
  - Cú pháp:
    ```
    useradd [option] [new_user]
    groupadd [option] [new_group]
    ```
  - Các option được sử dụng:
    - `--create-home(-m)`: Tạo username với tên [*] và thư mục /home/[*]
    - `--uid(-u)`: Chỉ định user id
    - `--comment(-c)`: Thêm ghi chú để gợi nhớ user
    - `passwd [user_name]`: Thực hiện sau khi tạo user và đặt mk cho user vừa tạo
  - Ví dụ:
    ```
    useradd -m huytl
    useradd -u 1906 huytl
    useradd --comment "CMT" huytl
    passwd huytl
    ```
- Sửa user, group: Là việc cập nhật user với các thay đổi
  - Cú pháp:
    ```
    usermod [option] [name_user]
    groupmod [option] [name_group]
    ```
  - Các option được sử dụng là:
    - `-c`: Chỉnh sửa trường comment
    - `--home(-d)`: Chỉnh sửa thư mục home của user
    - `--expiredate(-e)`: Thay đổi thời gian hết hạn của người dùng
    - `--login(-l)`: Chỉnh sửa tên đăng nhập
    - `--lock(-L)`: Khóa user
    - `--unlock(-U)`: Bỏ khóa user
    - `-G`: Thêm user vào Gr mới nếu muốn thêm user vào nhiều gr thì  tùy chọn trở thành `-aG`
  - Ví dụ:
    ```
    usermod -c "LQH" huylq
    usermod -d /home/huylq huylq
    usermod -L huylq
    usermod -U huylq
    usermod -G huytl huylq
    usermod -e 2024-31-12 huylq
    ```
- Xóa user, Group: Thực hiện việc xóa user và group ra khỏi HĐH.
  - Cú pháp:
    ```
    userdell [option] [user_name]
    groupdel [option] [group_name]
    ```
  - Các option được sử dụng:
    - `-r`: Xóa user và cả thư mục home của user
    - `-f`: Bắt buộc xóa tài khoản user ngay cả khi đang đăng nhập or có quá trình đang chạy. Xóa các tệp tin của người dùng kể cả khi thư mục home nằm ở trên 1 FS khác.
  - Ví dụ:
    ```
    userdel -r huytl
    groupdel -r dev
    ```
#### File lưu trữ cấu hình và các thông tin quan trọng của user và group có trong HĐH
- File /etc/passwd: Chứa các thông tin cụ thể về user 
  ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/91653b5b-0366-409e-a5d2-d3d88e916446)
  - Gồm các trường thông tin sau:
    - Username: tên đăng nhập của user
    - Passwd: Mk của user đã được mã hóa Hash.
    - User ID: ID của user sử dụng để phân biệt
    - Group ID: Nhóm chính của User này
    - Comment: Mô tả về user này
    - Home Directory: Thư mục home của người dùng.
    - Shell: Môi trường shell được sử dụng
- File /etc/shadow: Những bảo mật liên quan đến passwd của các tk user

  ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/8fd8546c-9573-4db9-9acd-bb4486153f1d)

  - Gồm các trường thông tin cụ thể:
    - Tên user: huylq
    - Mk đã được mã hóa:
    - Ngày cuối cùng mk được thay đổi tính từ 1/1/1970: 19900
    - Số ngày tối thiểu giữa các lần thay đổi mật khẩu: 0
    - Số ngày tối đa mật khẩu có hiệu lực: 99999
    - Số ngày cảnh báo khi mật khẩu sắp hết hạn: 7
    - Số ngày sau khi mk hết hạn thì tk bị vô hiệu hóa: Không có giới hạn
    - Ngày tài khoản hết hạn: Không bao giờ hết hạn
    - Trường này hiện không được sử dụng
- File /etc/group: Là file lưu trữ các thông tin quan trọng về nhóm người dùng trên HĐH
  
  ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/c280cdad-ad74-478c-8f38-874c053e0209)
  - Gồm các trường thông tin:
    - Groupname: tên nhóm
    - Passwd: Chuỗi pw
    - Group ID: ID Group giúp phân biệt các nhóm
    - User: DS các user nhận Group này làm sencondary(nhóm phụ: là 1 nhóm mà 1 người dùng không phải là thành viên chính nhưng vẫn có thể là thành viên). 
### Cron, at công cụ tự đông hóa các tác vụ
- Cron, at: Là các lệnh được sử dụng để tự động hóa các tác vụ hằng ngày như: sao lưu dữ liệu, cập nhật phần mềm, gửi email, báo cáo, ...
  - Lệnh Cron: `Crontab -e`
    - Có 6 trường: **Phút** **Giờ** **Ngày** **Tháng** **Thứ** **Command**
    - Ví dụ:
      ```
      * 3 * * * /script/abc.sh --> Thực hiện tác vụ trong file abc.sh vào 3h sáng mỗi ngày
      30 17 * * * /script/abc.sh --> Thực hiện tác vụ trong file abc.sh vào 17h30 mỗi ngày
      * * * */3 * /script/abc.sh --> Thực hiện tác vụ trong file abc.sh vào 3 tháng 1 lần
      ```
    - Cron được sử dụng để thực hiện các script vào những khoảng thời gian được setup sẵn. Tức là cron sẽ giúp chúng ta chạy các tác vụ chúng ta đã lên lịch sẵn nên không cần phải thực hiện chúng 1 cách thủ công. Diễn ra 1 cách liên tục trong 1 quãng thời gian dài, ... Phù hợp với các tác vụ diễn ra thường xuyên theo ngày, tuần, tháng, năm.
  - Lệnh At: `at + [time cụ thể]
    - vd:
      ```
      at 10am tomorow backup.sh --> chạy shell backup vào 10h sáng mai
      at 1pm July 10 script.sh --> chạy script vào 1h chiều ngày 10/07 sắp tới.
      at 12am every Sunday report.sh | mail -s "baocaohangtuan" huyvt02dl@gmail -> Gửi 1 báo cáo hàng tuần vào lúc 12h trưa mỗi ngày chủ nhật.
    - Sử dụng At khi: Muốn thực hiện 1 công việc nào đó trong tương lai nhưng không có thời gian hoặc có việc bận không thể làm thì nên sử dụng At. Phù hợp với các tác vụ diễn ra trong tương lai nhưng không thường xuyên.
### Cấu hình IP tĩnh IP động 
#### Khi nào cấu hình ip tĩnh và khi nào cấu hình ip động
- Cấu hình ip tĩnh khi: Làm việc với các máy chủ cần truy cập ssh, truyền tệp và đồng bộ hóa dữ liệu giữa các server và local, sử dụng các dịch vụ yêu cầu về ip tĩnh để có thể sử dụng, cấu hình triển khai, quản lý, hạn chế tấn công bởi ip tĩnh dễ dàng theo dõi và bảo mật.
- Cấu hình ip động khi: Có vô số thiết bị cần kết nối mạng, khi sử dụng dịch vụ DHCP, muốn cấu hình 1 cách tự động để giảm thiểu công sức, thời gian. Thường xuyen ngắt kết nối, kết nối đến mạng. Ip động giúp cho khả năng truy cập liên tục và ip sẽ thay đổi trong 1 khoảng thời giân hoặc sau khi reboot máy.
#### Cấu hình IP trên Ubuntu và CenOS:
##### Trên Ubuntu
- Các bước cấu hình Ip tĩnh trên Ubuntu:
  - B1: Kiểm tra giao diện mạng: `ip a` --> eno1, ens33
  - B2: Tạo 1 tệp `*.yaml` trong thư mục /etc/plan và chỉnh sửa nó bằng vim.
  - B3: Thêm các dòng sau vài file `*.yaml` đó:
    ```
    network:
      version: 2
      ethernets:
      ens33:
        dhcp4: no
        addresses:
          - 10.10.10.100/24
        gateway4: 10.10.10.2
        nameservers:
          addresses: 
            - 8.8.8.8
            - 4.4.4.4
    ```
  - B4: sử dụng lệnh `sudo netplan apply` để tiến hành khởi động lại dịch vụ và sử dụng `ip a` để kiểm tra
- Các bước cấu hình Ip động trên Ubuntu:
  - B1: Kiểm tra giao diện mạng `ip a`
  - B2: Tạo tệp `*.yaml` trong thư mục /etc/plan và chỉnh sửa nó như sau
    ```
    network:
      version:
      ethernets:
        ens33:
          dhcp: true
    ```
  - B3: Khởi động lại dịch vụ `sudo netplan apply` và sử dụng `ip a` để kiểm tra
#### Trên CenOS
- Các bước cấu hinh Ip tĩnh trên CentOS:
  - B1:
  - B2:
  - B3:
  - B4:
- Các bước cấu hình Ip động trên CentOS:
  - B1:
  - B2:
  - B3:
  - B4:
### SSH và các lệnh sao chép SCP và đồng bộ hóa Rsync
#### Lý thuyết về SSH
- SSH là 1 giao thức bảo mật được sử dụng thiết lập kết nối an toàn giữa người quản trị đến server. Nó hoạt động bằng cách mã hóa dữ liệu trên đường truyền giữa adm và server, đảm bảo dữ liệu khỏi bị nghe lén hoặc sửa đổi bởi những kẻ xâm nhập.
- SSH được sử dụng phổ biến với nhiều mục đích khác nhau:
  + Đăng nhập từ xa
  + Truyền tệp
  + Chuyển tiếp cổng
  + Thực thi lệnh từ xa
- SSH bao gồm 2 thành phần chính: Server - Client
- Sử dụng giao thức SSH:
  - Mặc định, máy chủ SSH chạy trên máy chủ từ xa, lắng nghe các kết nối đến trên cổng 22, trong khi máy khách SSH được sử dujg trên hệ thống cục bộ để liên lạc với máy chủ từ xa. Sử dụng giao thức TCP. Ở đây, khi thiết lập kết nối từ xa thông qua SSH là 1 đường hầm mã hóa được tạo ra giữa hệ thống cục bộ và hệ thống từ xa.
  - Tại hệ thống cục bộ, các lệnh được gõ sẽ thông qua đường hầm an toàn này truyên đến hệ thống từ xa và ngược lại. Và SSH còn cho phép hầu hết các loại lưu lượng mạng được gửi qua đường hầm được mã hóa, tạo ra một loại mảng ảo riêng( VPN) giữa hệ thống cục bộ và hệ thống từ xa.
  - Gói OpenSSH có chương trình có thể sử dụng đường hầm được mã hóa SSH để sao chép các tệp trên mạng. Lệnh sao chép `SCP` an toàn, được sử dụng như chương trình `copy` quen thuộc thể sao chép tệp tin.
  - Tạo đường hầm cục bộ với -L là chuyển tiếp cổng cục bộ: `ssh -L 8080:remote-server.com:80 huylq@remote-server.com
  - Tạo kết nối SSH với 1 máy từ xa và thiết lập 1 đường hầm SSH ngược: `	ssh -R 3306:localhost:8080 huylq@remote-server.com`.
- Các bước thiết lập khóa phiên giữa client và server:
  - B1: Client yêu cầu tạo 1 kết nôi TCP đến server
  - B2: Sv chấp thuận và gửi cho Client khóa Pu của mình và server key được tái tạo theo mỗi khoảng thời gian nhất định.
  - B3: Client nhận được khóa Pu của server. Sử dụng thuật toán mã hóa khóa đối xứng để tạo ra 1 key bí mật, sau đó sử dụng Ku của server để mã hóa key bí mật đó và gửi lên server.
  - B4: Server giải mã bằng Kr của nó để xác thực rằng chính nó là server mà client đang tìm kiếm.
  - B5: Phiên làm việc của client và server được mã hóa bằng chính key bí mất được tạo giữa client và server( Key đối xứng, cả 2 bên cùng có).
- Quá trình xác thực người dùng giữa client và server
  - Xác thực bằng passwd: client gửi kèm passwd của user truy cập tới server. SSH-AUTH sẽ so sánh mã băm của passwd với mã tướng ứng của user trong file /etc/shadow. Nếu phù hợp, server sẽ thông báo tới client xác thực thành công và client có thể truy cập tới server.
  - Xác thực bằng key:

    ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/81f94820-5ea8-47a2-9553-c28eb62fea9f)

  - Quá trình diễn ra như sau:
    - B1: Client bắt đầu gửi ID Ku của mình đến server.
    - B2: Server nhận đc ID và tìm kiếm trong file authorized_keys của mình. Nếu xuất hiện 1 Ku phù hợp với ID dc tìm thấy trong file thì lúc đó, server sẽ tạo ra 1 số ngẫu nhiên N và sử dụng Pu đó làm key để mã hóa N và gửi bản tin có chứa N được mã hóa đến client.
    - B3: Client nhận được bản tin đó, sử dụng khóa Kr của mình giải mã tìm ra được số ngẫu nhiên N. Sau đó nó sẽ sử dụng key bí mật giữa client và server trước đó tạo tính ra được mã Hash MD5. Sau đó nó gửi mã Hash đó đến server nhằm xác thực client đó là client mà server muốn xác thực.
    - B4: Server sử dụng khóa chung với client đã tạo ở giai đoạn thiết lập cùng với số N tính ra mã MD5. Sau khi nhận dược Mã Hash của client gửi lên thì lấy ra so sánh. Nếu trùng nhau thì xác thực được client( xác thực thành công). Ngược lại 2 mã Hash khác nhau thì đây không phải client mà nó muốn xác thực.
- Quá trình cài đặt và thiết lập khóa giữa client và server.
  - B1: Cài đặt dịch vụ trên 2 máy:
    - Server:
      ```
      sudo apt install openssh-server openssh-client
      systemctl start sshd
      systemctl enable sshd
      ```
    - Client:
      ```
      sudo apt install openssh-client
      ```
  - B2: Thử kết nối đến server từ client sử dụng passwd:

    ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/a1b59403-2097-4e26-a238-9b04b7d7b023)

  - B3: Kết nối sử dụng khóa bất đối xứng từ client:
    - Client: Tạo cặp khóa PU và PR `ssh-keygen -t rsa --> tạo 1 cặp khóa bằng thuật toán mã hóa RSA(SHA256) --> Tạo ra 1 cặp khóa Pu và Pr của client.

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/ba913985-4434-4a6e-8f92-8e510e38dd1c)

    - Client: Copy cặp khóa Pu gửi lên client thông qua ssh bằng mật khẩu ssh hoặc sử dụng lệnh `ssh-copy-id huylq@ip_remote_server`

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/a59e2642-ef95-4803-ba5e-2ffde66439c3)
  - B4: Kết nối từ client đến server bằng cặp khóa đx Pu, Pr

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/0d354ad3-840d-4813-bab2-07416b284b28)
    - Lưu ý: Tắt chế độ logion Server bằng passwd trong `/etc/ssh/ssh_config` sau khi đã gửi khóa lên server.

      ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/b957200f-d3ea-45ef-9bfe-b70150d05580)

#### Lệnh sao chép SCP và lệnh Rsync đồng bộ hóa dữ liệu
- Lệnh SCP: Sử dụng để copy file or dir từ local lên server và ngược lại
  - Cú pháp:
    ```
    scp [option] [source] [destination]
    ```
  - Các option được sử dụng:
    - `-r`: Sao chép đệ quy các thư mục
    - `-v`: Hiển thị quá trình sao chép
    - `-p`: duy trì quyền truy cập và thời gian sửa đổi
  - Ví dụ:
    ```
    scp -vpr ~/Desktop/file3 huylq@192.168.18.166:/home/huylq/DATA1   --> copy dữ liệu file3 từ máy local lên server cho vào thư mục DATA1
    scp vpr huylq@192.168.18.166:/home/huylq/DATA1 /home/huylq/Desktop/DATA5 --> copy dữ liệu từ thư mục DATA1 trên server xuống local được lưu vào thư mục DATA5
    ```
- Lệnh Rsync: Là giao thức truy cập từ xa rsync, cho phép rsync nhanh chóng phát hiện sự khác biệt giữa 2 thư mục và thực hiện số lượng sao chép tối thiểu cần thiết để đồng bộ hóa chúng. Điều này làm cho rsync sử dụng rất nhanh và tiết kiệm so với các loại chương trình sao chép khác. Rsync đuọc gọi là thế này:
  - Cú pháp:
    ```
    Rysnc [option] [source] [destination]
    ```
  - Các option được sử dụng:
    - `-a`: Đồng bộ tất cả bao gồm thuộc tính và các quyền
    - `-v`: Hiển thị tiến trình sao chép
    - `-z`: Nén dữ liệu trước khi truyền
    - `-r`: Sao chép đê quy các thư mục
  - Ví dụ:
    ```
    rysnc -avr ~/Desktop/Bai1 huylq@192.168.18.166:/home/huylq/Desktop/Bai2  --> Đồng bộ từ Local lên Server
    rysnc -avr huylq@192.168.18.166:/home/huylq/Desktop/Bai2 /home/huylq/Desktop/Bai1 --> Đồng bộ từ Server về Local
    ```
### Các dịch vụ DNS và DHCP
#### Dịch vụ DNS
- DNS là giao thức mạng, thuộc lớp ứng dụng trong mô hình OSI và TCP với chức năng chính là phân giải tên miền, ánh xạ địa chỉ IP thành tên miền và ngược lại. Sử dụng UDP port 53.
- Các khái niệm liên quan:
  - DNS có CSDL phân tán mạnh mẽ, không gian tên miền.
  - Hoạt đông dựa trên nguyên tắc tra vấn hê thống DNS server.
  - FQDN là tên miền đủ điều kiện, bao gồm: `hostname.domain.tld --> vd trang web `http://www.google.com/index.html` với:
    - `http`: Là giao thức được sử dụng
    - `www`: subdomain
    - `google`: là domain name
    - `.com`: là top-level domain (TLD or domain )(Là cấp cao nhất trong mô hình phân cấp)
    - `index.html`: là file path
 - Mô hình phân cấp:

   ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/a6ae0916-9c66-4400-8b2e-46e10a1d9eed)
   - Root name server: Lưu trữ thông tin về các máy chủ TLD cấp cao nhất. Giúp định hướng truy vấn các máy chủ DNS khác. Gồm 13 server trên toàn thế giới với 1 máy chủ chính tại Hoa Kỳ và 12 máy chủ phụ với 9 cái ở Hoa Kỳ, 2 cái ở EU, 1 cái ở Châu Á( Nhật bản). Là máy chủ đầu tiên mà resolver có thể truy vấn, đóng vai trò như cổng vào cho mọi truy vấn tên miền. Cụ thể, khi người dùng truy cập 1 trang web bất kỳ thì browser đó sẽ gửi truy vấn đến máy chủ DNS của ISP. DNS của ISP sẽ bắt đầu quá trình truy vấn bằng cách truy vấn DNS root namserver( vì đây là nơi lưu trữ thông tin về các máy chủ TLD vd:`.com`, `.vn`, `.jp`, ...) sau đó máy chủ DNS của ISP sẽ truy vấn máy chủ TLD để tìm kiếm máy chủ được ủy quyền cho trang web mà browser đó yêu cầu, máy chủ ủy quyền đó sẽ trả về địa chỉ IP cho trang web browser yêu cầu. Sau đó DNS ISP sẽ lưu dịa chỉ IP đó vào bộ nhớ cache và trả về địa chỉ IP cho browser.
   - TLD: gTLD và ccTLD: `.com`, `.vn`, ... và `.vn`, `.uk`, `.us`, ...
   - Domain name: chứa 2 phần SLD và TLD vd: TENTEN.VN thì SLD là `TENTEN` và TLD là `.VN`
   - Hostname: Là nhãn được gán cho 1 dịch vụ mạng. Thông thường là phần đầu tiên của FQDN. VD www.quanh.com thì `www` là hostname.
   - Subdomain: Nằm bên trái của SLD VD: Help.TENTEN.vn - thì `Help` là subdomain.
 - Các loại server: Server chính, Server phụ, Server lưu đệm thường trực các ISP, máy chủ chuyển tiếp máy chủ lưu đệm, máy chủ DNS ẩn(nằm sau firewall).
 - Nguyên lý truy vấn: Trình phân giải tạo truy vấn
   - B1: Kiểm tra bộ nhớ đệm DNS của chính nó
   - B2: Quá trình phân giải:

     ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/121801f4-a735-4c26-a425-14e35ea579a5)
       1. Kiểm tra bộ nhớ đệm của máy chủ DNS và chính nó tìm `www.example.com`
       2. Nếu không tìm thấy nó sẽ bắt đầu truy vấn đệ quy của ISP - Bắt đầu quá trình truy vấn đệ quy
       3. Hỏi đến server đệ quy( server này cũng tìm kiếm bản ghi trong bộ nhớ cache nếu có thì phản hồi - không thì nó sẽ hỏi server có thâm quyền cao hơn theo mô hình phân cấp).
       4. Mô hình phân cấp(root nameserver -> TLD nameserver -> Authoritative nameserver)
       5. Root nameserver dựa trên địa chỉ đó và chuển tiếp đến server thấp hơn chứa `.com` là TLD nameserver
       6. TLD nameserver chuyển tiếp đến Authoritative nameserver chứa domain đó sau đó nó trả về cho server đệ quy.
       7. Server đệ quy trả về cho Server local
  - Có 3 loại truy vấn:
    - Truy vấn đệ quy: Vì nó là mô hình phân cấp nên khi có yêu cầu cung cấp địa chỉ DNS thì nó hỏi bắt đầu từ server local -> server đệ quy -> server có thẩm quyền( Root nameserver -> Server TLD -> Server vùng) sau đó trả về server đệ quy -> trả về cho server local.
    - Truy vấn không đệ quy: Kiểm tra máy chủ local( 1. có bản ghi về trang đó or 2. có thẩm quyền để cấp cho client)
    - Truy vấn lặp lại: Hỏi từng server một - ban đầu cũng sẽ hỏi DNS server( server kiểm tra nếu nó không biết nó sẽ gửi thông tin về các server cấp cao hơn cho server DNS) -> (Root nameserver -> Chỉ đến Server TLD -> Chỉ đến Server zone). Tức là nếu server nào không biết nó sẽ chỉ đến server có thể biết cho client để cho client truy vấn.
  - Các loại bản ghi DNS: DNS record là bản ghi nằm trong DNS servers cung cấp thông tin về CSDL DNS, cho biết các tên miền, địa chỉ IP gắn với tên miền và cách xử lý tên miền đó ... Tất cả các tên miền trên internet đều phải có 1 vài bản ghi DNS cần thiết để người dùng có thể tru cập trang web khi nhập tẻn miền và thực hiện các mục đích khác.
    - SOA: Bản ghi SOA là viết tắt của "Start of Authority", đây là 1 trong những bản ghi DNS quan trọng nhất và có trách nhiệm quản lý tên miền. Bản ghi SOA chứa thông tin quan trọng về tên miền và xác định máy chủ chính quản lý tên miền đó.
    - A: Chuyển đổi domain name thành Ipv4
      - Cú pháp:
        ```
        [Tên miền] IN A [Địa chỉ IP của máy]
        ``` 
    - AAAA: Chuyển đổi domain name thành Ipv6
      - Cú pháp: tương tự A record
    - PTR: Chuyển đổi địa chỉ ip thành domain ( ngược lại với A và AAAA). Bản ghi này giúp xác thực IP của các hostname gửi tới, giúp hạn chế bị spam mail, ...
      - Cú pháp:
        ```
        [Địa chỉ IP] IN PTR [Tên miền]
        ```
    - CNAME: Bí danh tên miền. Giúp giảm lưu lượng truy cập vào 1 bản ghi. Tức là www.blog.com.vn có bí danh là blog.com.vn thì khi truy cập chỉ cần nhập blog.com.vn. Người dùng chỉ cần truy cập 1 trong 2 địa chỉ trên để có thể đến với trang web cần.
      - Cú pháp:
        ```
        [Tên bí danh] IN CNAME [Tên miền chinh]
        ```
    - NS: Name Server xác định máy chủ tên miền chịu trách nhiệm quản lý và lưu trữ bản ghi cho tên miền đó.
      - Cú pháp:
        ```
        [Tên miền] IN NS [Tên máy chủ]
      - Ví Dụ:
        ```
        dantri.com IN NS ns1.dantri.com
        dantri.com IN NS ns2.dantri.com
        ```
        Trong ví dụ trên thì tên miền `dantri.com` sẽ được quản lý bởi 2 máy chủ tên miền là `ns1.dantri.com` và `ns2.dantri.com`. Tức là các DNS record(A, MX record, ...) của tên miền `dantri.com` sẽ được khai báo trên 2 máy chủ này.
    - MX:  Là 1 DNS record giúp xác định mail server mà email được gửi tới. Một tên miền có thể có nhiều MX record, để tránh việc không nhận đc email nếu 1 mail server ngưng hoạt động.
      - VD:
         ```
        dantri.vn  IN  MX 10 mx10.dantri.vn
        dantri.vn  IN  MX 20 mx20.dantri.vn
         ```
         Trong đó 10 là giá trị ưu tiên. Số càng nhỏ độ ưu tiên càng cao. Trong ví dụ thì các mail có cấu trúc địa chỉ là `@dantri.vn` sẽ được gửi đến mail server `mx10.dantri.com` trước sau đó nếu gặp vấn đề sẽ gửi đến `mx20.dantri.vn`.
    - TXT: Là 1 loại bản ghi giúp tổ chức các thông tin dạng text của tên miền. Một doamin có thể có nhiều bản ghi TXT và chúng chủ yếu được dùng cho các SPF(Sender Policy Framework) giúp email server xác định các thư được gửi đến có phải từ 1 nguồn đáng tin hay không. Ngoài ra nó còn dùng để xác thực máy chủ của 1 tê miền, xác minh SSL, ...
- Xây dựng DNS Server cơ bản:
  1. Các bước xây dựng
     - Cài đặt các gói phần mềm phục vụ cho việc dựng DNS server:
       ```
       sudo apt install bind9 bind9utils bind9-doc -y` --> Cài đặt 3 gói phần mềm của bind 9
       ```
     - Kiểm tra trạng thái bind9:
       ```
       systemctl status bind9
       ```
     - Bắt đầu cấu hình các file liên quan:
       - B1: Cấu hình file `named.conf`: Là tệp cấu hình chính của bind9 gồm `named.conf.options` và `named.conf.local`:
         - Với `named.conf.options`:
           - `acl`: Chỉ thị xác định mạng cục bộ `LAN` or `internal-network`
           - `allow-query`: Chỉ thị xác định địa chỉ IP nào có thể truy vấn đến DNS server.
           - `forwarders`: Chỉ thị xác định máy chủ DNS nào mà máy chủ này sẽ chuyển tiếp các truy vấn đệ quy tới.
           - `recursion`: Chỉ thị cho phép truy vấn đệ quy tới máy chủ.
             
             ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/f2f9053c-5943-4620-a03e-edce23d035c2)
             
         - Với `name.conf.local`: Sử dụng để xác định vùng DNS cục bộ cho 1 tên miền riêng.
             ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/5a382a0c-7c1c-4067-a65e-e9d3fcbfff06)
           - Vùng chuyển tiếp(forward zone):
             - `zone "toilamlab.com" IN`: Là định nghĩa của 1 vùng có tên là `toilamlab.com`. `IN` là viết tắt của internet
             - `type master`: Là loại vùng master. Là máy chủ chính cho vùng này. Máy chủ chính có bản sao gốc của tất cả các bản ghi có trong vùng.
             - `file "/etc/bind/zones/toilamlab.com"`: Đây là đường dẫn tới tệp tin chứa các bản ghi DNS cho vùng `toilamlab.com`.
           - Vùng ngược( reveser zone):
             - `zone "89.45.103.in-addr.arpa" IN`: Định nghĩa của 1 vùng ngược cho dải IP 103.45.89.x. Sử dụng để ánh xạ địa chỉ IP thành tên miền. Lưu ý, địa chỉ ip trong vùng này được viết ngược lại và thêm vào đuôi phần `.in-addr.arpa`.
             - `type master: Tương tự vùng chuyển tiếp
             - `file "/etc/bind/zones/toilamlab.com.rev"`: Tương tự vùng chuyển tiếp
     - B2: Tạo ra thư mục zones và các tệp tin của vùng chuyển tiếp và vùng ngược:
       - Tạo thư mục zones: `mkdir zones` trong thư mục `/etc/bind`
       - Di chuyển đến thư mục zones và tạo ra các tệp cho vùng chuyển tiếp và vùng ngược:
         - Tạo file `toilamlab.com` và cấu hình vùng chuyển tiếp này như sau:
           
           ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/a3d3ae88-8f9d-4e1f-a62a-258d4b77baf0)
         - Tạo file `toilamlab.com.rev` và cấu hình vùng ngược như sau:

           ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/167a6e4e-272b-4b64-a0cb-33914815af72)
         - Kiểm tra các cấu hình đã chính xác hay chưa bằng lệnh:
           ```
           named-checkconf /etc/bind/named.conf.options
           named-checkconf /etc/bind/named.conf.local
           named-checkzone toilamlab.com /etc/bind/zones/toilamlab.com
           named-checkzone toilamlab.com /etc/bind/zones/toilamlab.com.rev
           ```
      - B3: Khởi động lại bind9 `systemctl restart bind9`
      - B4: Kiểm tra xem đã dựng thành công hay chưa
        - Tại máy local: sau khi đã trỏ DNS server về Server DNS(IP: 103.45.89.45)
          ```
          nslookup primary.toilamlab.com
          dig primary.toilamlab.com
          ```
          ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/ea3f6f2e-656f-4c13-bef2-8e0fc07c2f27)
  3. Những lưu ý quan trọng khi dựng Server DNS
#### Dịch vụ DHCP server
- Khái niệm: Là 1 giao thức mạng, giao thức cấu hình sử dujg để cấp phát địa chỉ ip động. Giao thức ở lớp ứng dụng trong mô hình OSI. Cung cấp dịch vụ mạng cho các ứng dụng khác.
- Giao thức mạng: Là quy tắc và chuẩn mực quy định cách thức giao tiếp giữa các thiết bị trên mạng. Giao thức mạng đảm bảo dữ liệu được truyền 1 cách chính xác hiệu quả và an toàn.
- DHCP server cung cấp Database để theo dõi các máy client trong hệ thống mạng để dễ dàng quản lý địa chỉ IP của chúng.
- DHCP Replay Agent: Là 1 tính năng được cấu hình cho các router trung gian để tiếp nhận các bản tin yêu cầu cấp phát IP của các clients sau đó chuyển thông tin đến DHCP server. Là 1 tính năng, nơi chuyển đổi bản tin broadcast thành unicast.
- DHCP daemon log( tệp nhật ký dhcpd): Là 1 dạng tệp ghi lại các hoạt động của máy chủ dhcp.
- Các bản tin trong DHCP: Discover, Offer, Request, ACK, Nack, Decline, Release, ...
  - Discover: Sử dụng để gửi đến DHCP server để yêu cầu 1 địa chỉ IP truy cập vào mạng. Nó gửi kèm cả địa chỉ MAC nhằm xác định được chính xác thiết bị đã gửi bản tin.
  - Offer: Là 1 bản tin được gửi từ DHCP server xuống để phản hồi bản tin Discover từ client. Gói tin này chứa địa chỉ IP, cấu hình TCP/IP bổ sung.
  - Request: Là 1 bản tin gửi từ Client lên DHCP server nhằm phản hồi về bản tin Offer và sự chấp nhận sử dụng IP có ở trong bản tin Offer
  - ACK: Là 1 dạng bản tin từ DHCP gửi cho client. Xác nhận rằng chính thiết bị này với địa chỉ MAC này sử dụng IP này.
  - NACK: Ngược lại với ACK. Khi Client gửi bản tin Request với địa chỉ IP cụ thể nhưng máy chủ DHCP không thể cung cấp địa chỉ đó thì bản tin NACK sẽ được DHCP phản hồi.
  - Decline: Trường hợp DHCP quyết định tham  số được đề nghị nào không có giá trị tức là sau khi Client gửi bản tin Request, Server nhận được thông tin nhưng không khớp với thông tin đã cấp trước đó. Khi đó Server yêu càu thực hiện lại quá trình thuê.
  - DHCP Release: Là quá trình client hoàn thành xong các công việc và gửi đến Server yêu cầu giải phóng địa chỉ IP và xóa bất kì IP đang còn tồn tại. Server sau đó sẽ thực hiện việc thu hồi địa chỉ IP và đánh dấu IP trống.
  - Cài đặt DHCP server: 
    - B1: Cài đặt DHCP server: `sudo apt install isc-dhcp-server`
    - B2: Cấu hình ip tĩnh cho server DHCP
    - B3: Mở file /etc/dhcp/dhcpd.conf và thay đổi các thông số cần thiết:
      - 38 dòng đầu tiên:

        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/0f23059b-6723-48ef-a85a-76da74fe4080)
      - 39 - 75 dòng tiếp theo: Xóa dấu ghi chú `#` ở các dòng cần cấu hình và thay đổi 1 số thông tin cần thiết:


        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/1b80f560-ed07-4212-8bd6-1e021a758065)

    - B4: Sau khi hoàn tất cấu hình và lưu cấu hình, thực hiện việc khởi động lại dịch vụ và kiểm tra trạng thái hoạt động:
      - Khởi động lại dịch vụ: `systemctl restart isc-dhcp-server`
      - Kiểm tra trạng thái dịch vụ: `systemctl status isc-dhcp-server`

        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/97d2f096-a580-4ea7-8c14-e52bdd68c5a8)
    - B5: Kiểm tra trên máy local và kiểm tra danh sách cấp phát địa chỉ ip trên server:
      - Trên máy local:

        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/36926365-f131-4f65-a127-51a6cd33887f)

      - Trên server DHCP:

        ![image](https://github.com/huylamquang/H-H---LINUX/assets/147602556/e71f6d7f-a57f-4bce-9f56-e51846c124b5)

      - Kết luận: Máy local được cấp phát địa chỉ IP `192.168.100.19` với địa chỉ MAC '00:0c:29:83:93:b2` trùng với địa chỉ IP và DHCP server cấp phát.

      LAB - Bắt bản tin DHCP bằng wireshark



      

     
