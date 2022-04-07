# Triển khai web site cơ bản trên IIS

Yêu cầu

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
- Một trong những tính năng được sử dụng nhiều nhất của IIS là tạo một ứng dụng web bằng ASP .NET