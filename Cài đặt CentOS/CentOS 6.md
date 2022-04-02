# Cài đặt CentOS 6.9
Bước 1: Tải file iso của CentOS 6 tại

http://mirror.nsc.liu.se/centos-store/6.9/isos/x86_64/CentOS-6.9-x86_64-bin-DVD1.iso

Bước 2: Cài đặt CentOS 6.9
- Tạo máy ảo trên môi trường VMware
- Máy ảo sẽ bắt đầu boot vào ISO và bắt đầu quá trình cài đặt CentOS 6.9

- Lựa chọn `Install or upgrade an existing system` 

![](./images/centos6.png)

- Nhấn `Skip` để bỏ qua

![](./images/centos6-1.png)

- Tiếp theo chọn `Next`

![](./images/centos6-2.png)

- Chọn ngôn ngữ là `English` và chọn `Next`

![](./images/centos6-3.png)

- Chọn bàn phím mặc định

![](./images/centos6-4.png)

- Chọn `Basic Storage Devices` và chọn `Next` 

![](./images/centos6-5.png)

- Nhấp vào `Yes, discard any data` sau đó chọn `Next` như hình dưới

![](./images/centos6-6.png)

- Đặt hostname. Có thể để mặc định

![](./images/centos6-7.png)

- Chọn thành phố để thiết lập time zone bằng cách di chuyển và click vào bản đồ sau đó chọn `Next`

![](./images/centos6-8.png)

- Đặt mật khẩu cho root và chọn `Next`

![](./images/centos6-9.png)

- Tùy chọn phân vùng. Chọn option `Create Custom Layout`

![](./images/centos6-10.png)

- Chọn dung lượng còn trống trong ổ cứng sda
	+ Nhấp vào `Create`. Thao tác này sẽ bật lên cửa sổ `Create Storage`
	+ Tích vào `Standard Partition` 
	+ Nhấp vào `Create`

![](./images/centos6-12.png)

- Tạo phân vùng ổ cứng `/boot`
	+ Mount Point: `/boot`
	+ File System Type: `/ext4`
	+ Size: 1024 MB
	+ Tại option `Additional Size Options` chọn `Fixed size`
	+ Bấm `OK`

![](./images/centos6-13.png)

- Tạo phân vùng ổ cứng `/swap`
	+ Mount Point: None
	+ File System Type: `swap`
	+ Size: 8096 MB
	+ Tại option `Additional Size Options` chọn `Fixed size`
	+ Bấm `OK`

![](./images/centos6-14.png)

- Tạo phân vùng ổ cứng `/`
	+ Mount Point: `/`
	+ File System Type: `ext4`
	+ Size: 48000 MB
	+ Tại option `Additional Size Options` chọn `Fixed size`
	+ Bấm `OK`

![](./images/centos6-15.png)

- Tạo 1 phân vùng LVM Physical Volume
	+ File System Type: `Physical Volume (LVM)`
	+ Size: 500 MB
	+ Tại option `Additional Size Options` chọn `Fill to maximum allowable size`
	+ Bấm `OK`

![](./images/centos6-16.png)

![](./images/centos6-17.png)

- Tạo phân vùng `/home`
	+ Create LVM: `LVM Volume Group`
	+ Mount Point: `/home`
	+ File System Type: `ext4`
	+ Size 4300
	+ Bấm `OK`

![](./images/centos6-18.png)

- Danh sách các ổ cứng đã tạo

![](./images/centos6-19.png)

- Nhấn `Next` -> `Format`

![](./images/centos6-20.png)

![](./images/centos6-21.png)

- Chọn `Install boot loader on /dev/sda`

![](./images/centos6-22.png)

- Chọn `Minimal` sau đó nhấn `Next`

![](./images/centos6-23.png)

- Hệ thống sẽ tiến hành cài đặt

![](./images/centos6-24.png)

- Sau khi hệ thống cài đặt xong. Chọn `Reboot` để khởi động lại

![](./images/centos6-25.png)

- Kiểm tra hệ điều hành

![](./images/centos6-26.png)
