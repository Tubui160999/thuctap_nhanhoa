# Hyper-V là gì

**Yêu cầu**
- Cài đặt Hyper-V để tạo 2 VM: mỗi VM cấu hình 8 RAM + 8 core + 200Gb Disk lấy ở Data 500GB, IP 172.16.3.201/20 172.16.3.202/20 Gateway 172.16.10.1

- Hyper-V là công nghệ ảo hóa thể hệ mới của Microsoft, dựa trên nền tảng hypervisor. Mang đến cho người dùng (chủ yếu là doanh nghiệp) một nền tảng ảo hóa mạnh và linh hoạt, có khả năng mở rộng, tính tin cậy và sẵn sàng cao

- Đặc biệt ảo hóa Hyper-V giúp đáp ứng nhu cầu ảo hóa mọi cấp độ cho môi trường doanh nghiệp. Ngoài ra, người dùng không cần phải mua thêm bất cứ phần mềm nào khi muốn nâng cấp hoặc khai thác csac tính năng ảo hóa của server

# Hyper-V mang lại lợi ích gì?
- Hyper-V cung cấp cơ sở hạ tầng phần mềm và các công cụ quản lý cơ bản mà doanh nghiệp có thể sử dụng để tạo ra và quản lý một môi trường điện toán máy chủ ảo hóa. Một môi trường máy chủ ảo hóa với các tính năng nổi bật sau:
	+ Ảo hóa linh hoạt
	+ Nền tảng ảo hóa mạnh
	+ Tăng cường bảo mật
	+ Trung tâm dữ liệu động 
	+ Hợp nhất server
 
# Cài đặt Hyper-V
- Chạy `Server Manager` và nhấp vào `Add roles and features`

![](./images/hyperv1.png)

- Nhấp vào `Next`

![](./images/hyperv2.png)

- Chọn `Role-based or feature-based installation` -> Nhấn `Next`

![](./images/hyperv3.png)

- Chọn host muốn thêm vào các service

![](./images/hyperv4.png)

- Tích vào `Hyper-V` -> `Add Features` -> `Next`

![](./images/hyperv5.png)

- Nhấp vào nút `Next`

![](./images/hyperv6.png)

- Tiếp tục chọn `Next`

![](./images/hyperv7.png)

- Tại phần `Virtual Switches` chọn 1 network adapter cho nó

![](./images/hyperv8.png)

- Phần `Virtual Machines Migration`, giữ nguyên tùy chọn mặc định và tiếp tục nhấn `Next`

![](./images/hyperv9.png)

- Phần chỉ định vị trí cấu hình của máy ảo. Trong phần này ta giữ nguyên tùy chọn mặc định và tiếp tục nhấn `Next`

![](./images/hyperv10.png)

- Nhấp vào nút `Install` để bắt đầu cài đặt

![](./images/hyperv11.png)

- Sau khi kết thúc quá trình cài đặt, nhấp vào nút `Close` và khởi động lại máy tính

![](./images/hyperv12.png)

## Tạo máy ảo 
- Chạy `Server Manager` và mở `Tools` -> `Hyper-V Manager` 

![](./images/hyperv13.png)

- Chọn Hostname ở bên trái và nhấp chuột phải vào nó để mở menu, sau đó chọn `New` -> `Virtual Machine`

![](./images/hyperv14.png)

- Nhấp vào nút `Next`

![](./images/hyperv15.png)

- Nhập tên máy ảo

![](./images/hyperv16.png)

- Chỉ định thế hệ máy ảo. Chọn `Generation 2`

![](./images/hyperv17.png)

- Chỉ định bộ nhớ cho máy ảo (8 GB RAM)

![](./images/hyperv18.png)

- Chọn Virtual Switch để sử dụng kết nối mạng của máy ảo

![](./images/hyperv19.png)

- Cấu hình ổ cứng ảo. Đặt giá trị theo yêu cầu (200 GB từ Data)

![](./images/hyperv20.png)

- Cài OS cho máy ảo hoặc có thể để sau

![](./images/hyperv21.png)

- Nhấp vào `Finish` để hoàn tất

- Máy ảo vừa được tạo. Để bắt đầu, hãy nhấp chuột phải vào nó và chọn `Start`

- Để kết nối bảng điều khiển của máy ảo, hãy nhấp chuột phải vào nó và chọn `Connect`

![](./images/hyperv28.png)

- Làm tương tự với VM-2

![](./images/hyperv26.png)

- Cài OS cho máy ảo để tiến hành đặt địa chỉ IP

![](./images/hyperv27.png)

![](./images/hyperv29.png)

![](./images/hyperv31.png)

- Tiến hành đặt địa chỉ IP cho 2 máy ảo 

- VM-1 IP: 172.16.3.201/20 Gateway: 172.16.10.1

![](./images/hyperv32.png)

![](./images/hyperv33.png)

- VM-2 IP: 172.16.3.202/20 Gateway: 172.16.10.1

![](./images/hyperv34.png)

![](./images/hyperv35.png)

- Chỉnh thông số `Number of virtual processors` (8 core)

![](./images/hyperv36.png)
