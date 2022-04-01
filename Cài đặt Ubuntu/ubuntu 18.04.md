# Cài đặt Ubuntu server 18.04 
Bước 1: Tải file iso của Ubuntu 18.04 tại

https://mirrors.nhanhoa.com/ubuntu-releases/18.04/ubuntu-18.04.6-live-server-amd64.iso

Bước 2: Cài đặt Ubuntu server 18.04
- Tạo máy ảo trên môi trường VMware
- Máy ảo sẽ bắt đầu boot vào ISO và bắt đầu quá trình cài đặt Ubuntu Server

- Chọn ngôn ngữ để bắt đầu

![](./images/ubuntu18-1.png)

- Nếu bản iso download đã cũ rồi, có thể đã có một vài cập nhật rồi, ta có thể lựa chọn cập nhật trước khi cài đặt hoặc có thể bỏ qua với lựa chọn `Continue without updating`

![](./images/ubuntu18-2.png)

- Chọn bàn phím để tiếp tục. Khuyến nghị nên sử dụng English (mặc định). Chọn `Done` để tiếp tục 

![](./images/ubuntu18-3.png)

- Tiếp đến là phần cấu hình IP cho máy ảo để có thể kết nối với Internet hoặc mạng nội bộ. Ta có thể sử dụng IP động do DHCP cấp hoặc IP tĩnh để đặt. Ở đây ta đặt IP tĩnh. Sau đó `Save` -> `Done`

![](./images/ubuntu18-4.png)

![](./images/ubuntu18-5.png)

- Cài đặt proxy. Ta có thể chọn `Done` để nhận proxy theo mặc định

![](./images/ubuntu18-6.png)

- Cài đặt địa chỉ mirror cho ubuntu. Nhấn `Done` để nhận mặc định

![](./images/ubuntu18-7.png)

- Phân vùng ổ cứng. Chọn `Done` để phân vùng ổ cứng tự động

![](./images/ubuntu18-8.png)

- Chọn `Done` để hệ thống tự động phân vùng ổ cứng. Hệ thống sẽ cần ta xác nhận trước khi chuyển tới bước tiếp theo. Ấn `Continue` để tiếp tục

![](./images/ubuntu18-9.png)

- Tiếp tục, ta sẽ khai báo thông tin về username để đăng nhập sử dụng Ubuntu sau khi cài đặt xong

![](./images/ubuntu18-10.png)

- Lựa chọn OpenSSH để có thể SSH vào Ubuntu server

![](./images/ubuntu18-11.png)

- Cài đặt thêm một số gói. Có thể chọn `Done` để bỏ qua

![](./images/ubuntu18-12.png)

- Quá trình cài đặt sẽ tiếp tục diễn ra, sẽ mất khoảng 10 phút để quá trình này kết thúc. Sau khi kết thúc ta sẽ cần khởi động lại để hoàn tất quá trình cài đặt Ubuntu Server

![](./images/ubuntu18-13.png)

- Chọn `Reboot Now` để khởi động lại sau khi hoàn tất cài đặt

![](./images/ubuntu18-14.png)

- Quá trình cài đặt Ubuntu Server đã hoàn tất. Ta có thể đăng nhập vào Ubuntu để sử dụng

- Kiểm tra phiên bản của hệ điều hành và IP tĩnh đã đặt trước đo

![](./images/ubuntu18-15.png)


# Đổi mật khẩu root Ubuntu 

```sh
sudo passwd root
```

![](./images/setpasswd.png)
