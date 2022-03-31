# Cài đặt Ubuntu server 21.10
Bước 1: Tải file iso của Ubuntu

http://mirrors.nhanhoa.com/ubuntu-releases/21.10/ubuntu-21.10-live-server-amd64.iso

Bước 2: Cài đặt Ubuntu server 21.10
- Tạo máy ảo trên môi trường VMware
- Sau khi boot thì màn hình sẽ hiện lên như sau
- Ta chọn ngôn ngữ cho hệ điều hành của mình muốn sử dụng

![](./images/ubuntusetup.png)

- Chọn bàn phím muốn sử dụng

![](./images/keyboard.png)

- Chọn loại ubuntu muốn cài đặt: Có 2 loại là
	+ Ubuntu Server
	+ Ubuntu Server (minimized)

![](./images/ubuntuver.png)

- Ta sẽ cài đặt IP cho máy tính muốn sử dụng
	+ Chọn done để nhận IP theo DHCP
	+ Chọn vào edit để có thể cài IP static

> Ở đây ta chọn đặt IP tĩnh

![](./images/ipv4.png)

![](./images/ipv4a.png)

- Cài đặt proxy. Ta có thể chọn `Done` để nhận proxy theo mặc định

![](./images/proxy.png)

- Cài đặt địa chỉ mirror cho ubuntu. Nhấn `Done` để nhận mặc định

![](./images/mirror.png)

- Phân vùng ổ cứng. Chọn done để không chia, chỉ sử dụng 1 phân vùng

![](./images/disk.png)

- Chọn phân vùng để cài đặt hệ điều hành, chọn `Done` sau đó chọn `Continue` để xác nhận tiếp tục cài đặt

![](./images/disk1.png)

- Cài đặt tên máy sử dụng, đặt user và password để đăng nhập vào máy. Rồi chọn `Done` để hoàn thành việc cài đặt

![](./images/info.png)

- Lựa chọn cài đặt dịch vụ SSH cho máy hay là không. Nếu có cài đặt thì có sử dụng mật khẩu cho dịch vụ ssh hay là không. Và chọn có cho ssh bằng password hay là không. Rồi chọn `Done`

![](./images/ssh.png)

- Cài đặt thêm 1 số gói, nếu không cần thì chọn `Done`

![](./images/pakage.png)

- Đợi hệ thống cài đặt

![](./images/wait.png)

- Sau khi cài đặt xong chọn `Reboot` để hoàn thành
- Đăng nhập với user và password.