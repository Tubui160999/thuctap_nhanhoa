# Triển khai web site cơ bản trên IIS

**Yêu cầu**

- Triển khai một web site cơ bản trên IIS.
- Cài đặt Hyper-V để tạo 2 VM: mỗi VM cấu hình 8 RAM + 8 core + 200Gb Disk lấy ở Data 500GB, IP 172.16.3.201/20 172.16.3.202/20 Gateway 172.16.10.1

## IIS là gì?
- IIS là viết tắt của từ Internet Information Services, được đính kèm với các phiên bản của Windows. Microsoft Internet Information Services (Các dịch vụ cung cấp thông tin Internet) là các dịch vụ dành cho máy chủ chạy trên nền hệ điều hành Window nhằm cung cấp và phân tán các thông tin lên mạng, nó bao gồm nhiều dịch vụ khác nhau như Web Server, FTP Server ...
- Nó có thể được sử dụng để xuất bản nội dung của các trang Web lên Internet bằng việc sử dụng "Phương pháp chuyển giao siêu văn bản" - Hypertext Transport Protocol (HTTP)
- Như vậy, sau khi thiết kế xong trang web của mình, nếu ta muốn đưa chúng lên mạng để mọi người có thể truy cập và xem chúng thì phải nhờ đến một Web Server, ở đây là IIS
## IIS có thể làm được gì
- Nhiệm vụ của IIS là tiếp nhận yêu cầu của máy trạm và đáp ứng lại yêu cầu đó bằng cách gửi về máy trạm những thông tin mà máy trạm yêu cầu
- Ta có thể sử dụng IIS để 
	+ Xuất bản một Website trên Internet
	+ Tạo các giao dịch thương mại điện tử 
	+ Chia sẻ file dữ liệu thông qua giao thức FTP
	+ Cho phép người ở xa có thể truy xuất database của bạn (Database remote access)

## Hoạt động của IIS
- IIS sử dụng các giao thức mạng phổ biến là HTTP và FTP (File Transfer Protocol) để tiếp nhận yêu cầu và truyền tải thông tin trên mạng với các định dạng khác nhau
- Một trong những dịch vụ phổ biến nhất của IIS là dịch vụ WWW (World Wide Web)
- Dịch vụ Web sử dụng giao thức HTTP để tiếp nhận yêu cầu (Requests) của trình duyệt Web (Web browser) dưới dạng một địa chỉ URL của một trang Web và IIS phản hồi lại các yêu cầu bằng cách gửi về cho Web browser nội dung của trang web tương ứng

## Các tính năng của IIS
- Một trong những tính năng được sử dụng nhiều nhất của IIS là tạo một ứng dụng web bằng ASP .NET. Bên cạnh đó, IIS hoàn toàn có thể chạy được với các trang web viết bằng ngôn ngữ khác như PHP, Perl...
- IIS hỗ trợ một số loại xác thực như Basic access authentication, Digest access authentication, Windows Authentication, Certificate Authentication... các tính năng bảo mật khác bao gồm hỗ trợ SSL/TLS, Thiết lập bảo mật cho máy chủ FTP...

## Cài đặt IIS
- Chạy `Server Manager` sau đó nhấp vào `Add roles and features`

![](./images/iis1.png)

- Click vào `Next`

![](./images/iis2.png)

- Chọn `Role-based or feature-based installation`

![](./images/iis3.png)

- Chọn máy chủ lưu trữ mà ta muốn thêm dịch vụ 

![](./images/iis4.png)

- Chọn mục `web server (IIS)` và click vào `Add Features` sau đó click `Next`

![](./images/iis5.png)

- Tiếp tục chọn `Next`

- Tại phần `Role Services`. Đây là phần chọn các tính năng của Web Server ta có thể giữ nguyên mặc định và chọn `Next`

![](./images/iis6.png)

- Click vào `Install`

- Sau khi hoàn tất cài đặt, chọn `Close`

![](./images/iis7.png)

- Chạy trình duyệt Web và truy cập vào `http://localhost` để xác minh IIS đang chạy bình thường

![](./images/iis8.png)

![](./images/iiss.png)

- Trỏ IP về tên miền

- Thư mục chứa web site mặc định khi cài dịch vụ là `C:\inetpub\wwwroot`
- Tại đây ta tạo 1 file `index.html` và thêm vào nội dung

![](./images/iis16.png)

- Kiểm tra

![](./images/iis17.png)

## Cài đặt WordPress

Bước 1: Mở IIS -> Chọn `Get New Web Platform Components`

![](./images/iis28.png)

Bước 2: Cài đặt Web Platform Installer

![](./images/iis29.png)

Bước 3: Mở Web Platform Installer

![](./images/iis30.png)

Bước 4: Tìm kiếm PHP và cài đặt PHP 7.4.13 (x86)

![](./images/iis31.png)

![](./images/iis32.png)

![](./images/iis33.png)

Bước 5: Tải PHP manager và cài đặt 

https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10

Bước 6: Tải MariaDB

Tải MariaDB tại https://mariadb.org/download/?t=mariadb&p=mariadb&r=10.6.5&os=windows&cpu=x86_64&pkg=msi&m=inet

![](./images/iis34.png)

![](./images/iis35.png)

![](./images/iis36.png)

- Nhập mật khẩu cho người dùng root

![](./images/iis37.png)

![](./images/iis38.png)

![](./images/iis39.png)

Bước 10: Sau khi cài đặt, vào HeidiSQL

![](./images/iis40.png)

Bước 11: Thêm một phiên mới và thay đổi tên của nó từ “Uname” thành “localhost”

![](./images/iis41.png)

Bước 12: Nhập mật khẩu cho người dùng root sau đó bấm `Save` và `Open`

![](./images/iis42.png)

Bước 13: Tạo cơ sở dữ liệu mới trong localhost

![](./images/iis43.png)

Bước 14: Đặt tên cho DB

![](./images/iis44.png)

Bước 15: Đi tới trình quản lý người dùng

![](./images/iis45.png)

Bước 16: Nhấp vào `Add`. Đặt tên người dùng là `admindb`. Tại `From host` chọn `Access from everywhere`

![](./images/iis46.png)

Bước 17: Tải xuống WordPress tại https://wordpress.org/download/

![](./images/iis47.png)

Bước 18: Sao chép nội dung của tệp WordPress đã tải xuống tới thư mục `C:\inetpub\wwwroot`

- Tạo một thư mục ở đó (Đặt tên là `test`)

- Dán nội dung WordPress đã sao chép vào thư mục này

![](./images/iis48.png)

Bước 19: Mở IIS

- Đi đến `Sites` và chọn `Add Website` 

![](./images/iis49.png)

- Điền thông tin như dưới hình

![](./images/iis50.png)

Bước 20: Click `Connect as ..` -> `Specific user` -> `set` sau đó nhập user pass của vps

![](./images/iis51.png)

Bước 22: Mở IIS và mở sites vừa tạo `tubui`

- Mở `PHP Manager`

![](./images/iis53.png)

Bước 23: Nhấp vào `View recommendations`

![](./images/iis54.png)

Bước 24: Chọn 2 option và nhấn vào `OK`

![](./images/iis55.png)

Bước 25: Trong phần `Action`, nhấp vào `Browse *:8041(http)`

![](./images/iis56.png)

Bước 26: Trang web WordPress mở ra và ta thực hiện thiết lập

![](./images/iis57.png)

![](./images/iis58.png)
