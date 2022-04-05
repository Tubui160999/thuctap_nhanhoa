# Cài đặt CentOS 7
- Chuẩn bị USB boot CentOS 7

Bước 1: Tải file iso của CentOS 7 tại

https://mirrors.nhanhoa.com/centos/7.9.2009/isos/x86_64/CentOS-7-x86_64-DVD-2009.iso

Bước 2: Khởi động lại máy chủ sau đó nhấn phím F11 để vào Boot Manager

- Tại `Boot Manager` chọn `BIOS Boot Menu` 

![](./images/centos7-11.png)

- Thực hiện Boot vào USB để cài đặt CentOS 7

![](./images/centos7-12.png)


- Lựa chọn Install CentOS 7

![](./images/centos7-13.png)

- Thiết lập ngôn ngữ. Mặc định `English`, sau đó chọn `Continue`

![](./images/centos7-14.png)

- Thiết lập ngày giờ `Date & Time` -> Trỏ chuột vào bản đồ để chọn giờ Việt Nam -> `Done`

![](./images/centos7-15.png)

![](./images/centos7-16.png)

- Ở mục `Software Selection`, chọn `Minimal Install` để không dùng GUI cho hệ điều hành này. Sau đó chọn `Done`

![](./images/centos7-17.png)

- Chọn mục `Installation Destination` để chọn ổ cứng 

![](./images/centos7-18.png)

- Tiến hành phân vùng ổ cứng
	+ /boot: 1 Gb
		+ Device type: Standard Partition
		+ File System: ext4
	+ /swap: 8 Gb
		+ Device type: Standard Partition
		+ File System: swap
	+ /: Tổng dung lượng còn lại
		+ Device System: LVM
		+ File System: ext4

![](./images/centos7-19.png)

- Tiếp tục chọn Network & Hostname. Ta click vào nút OFF để máy có kết nối về network. Nhập hostname tùy ý

![](./images/centos7-20.png)

- Chọn `Begin Instalation` để thực hiện cài đặt

![](./images/centos7-21.png)

- Sau đó nhập mật khẩu cho tài khoản `root` và chờ các bước cài đặt diễn ra

![](./images/centos7-22.png)

- Sau khi cài đặt hoàn tất, chọn `Reboot System` để máy khởi động lại và bắt đầu đăng nhập vào OS với tài khoản root và mật khẩu nhập trước nó

![](./images/centos7-23.png)

- Kiểm tra hệ điều hành

![](./images/centos7-24.png)
