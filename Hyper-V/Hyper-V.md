# Cài đặt Hyper-V

**Yêu cầu**
- Cài đặt Hyper-V để tạo 2 VM: mỗi VM cấu hình 8 RAM + 8 core + 200Gb Disk lấy ở Data 500GB, IP 172.16.3.201/20 172.16.3.202/20 Gateway 172.16.10.1

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

- Chỉ định bộ nhớ cho máy ảo

![](./images/hyperv18.png)

- Chọn Virtual Switch để sử dụng kết nối mạng của máy ảo

![](./images/hyperv19.png)

- Cấu hình ổ cứng ảo. Đặt giá trị theo yêu cầu (200 GB từ Data)

![](./images/hyperv20.png)

- Cài OS cho máy ảo hoặc có thể để sau

![](./images/hyperv21.png)

- Nhấp vào `Finish` để hoàn tất

![](./images/hyperv22.png)

- Máy ảo vừa được tạo. Để bắt đầu, hãy nhấp chuột phải vào nó và chọn `Start`

![](./images/hyperv24.png)

- Để kết nối bảng điều khiển của máy ảo, hãy nhấp chuột phải vào nó và chọn `Connect`

