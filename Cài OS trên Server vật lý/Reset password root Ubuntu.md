# Reset mật khẩu gốc trong Ubuntu

Khởi động lại hệ thống

- Khởi động lại hệ thống. Khi nhìn thấy màn hình hiển thị, hãy giữ phím `Shift`. Hệ thống sẽ đưa đến `GRUB` hoặc menu khởi động với các phiên bản nhân Linux khác nhau được hiển thị

![](./images/resetubuntu.png)

- Chọn `Recovery mode`

![](./images/resetubuntu1.png)

- Sau khi vào `Recovery Mode` sẽ có giao diện sau. Chọn root

![](./images/resetubuntu2.png)

- Nhập lệnh 

```sh
mount -o remount,rw /
```

- Sau đó thực hiện đặt lại mật khẩu cho root và khởi động lại

```sh
passwd root
reboot
```

![](./images/resetubuntu3.png)
