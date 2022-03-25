# Build PHP + Nginx trên DirectAdmin
- Vào thư mục CustomBuild
```sh
cd /usr/local/directadmin/custombuild
```

- Kiểm tra các phiên bản PHP đang được build
```sh
vi /usr/local/directadmin/custombuild/options.conf
```

![](./images/buildphp.png)

- Ta thấy có thể build đồng thời 4 phiên bản PHP trên DirectAdmin. Và đã có sẵn 2 phiên bản php 7.4 và 8.0.
- Để build thêm 1 phiên bản PHP, web server nginx và phpMyAdmin ta cần chỉnh sửa thông tin trong file `/usr/local/directadmin/custombuild/option.conf` như sau

![](./images/buildphpnginx.png)

- Thoát và lưu

- Sau đó ta chạy các lệnh để build đúng như thiết lập
```sh
./build update
./build nginx
./build php n
./build rewrite_confs
```

![](./images/buildnginx.png)

![](./images/buildphp1.png)

- Đổi phiên bản php và kiểm tra 

![](./images/phpver.png)

- Vào `File Manager` tạo một file `info.php` trong thư mục `public_html` để kiểm tra phiên bản

![](./images/info.png)

![](./images/info1.png)

- Vào trình duyệt kiểm tra 

![](./images/info2.png)

>> Với Apache ta build tương tự như Nginx