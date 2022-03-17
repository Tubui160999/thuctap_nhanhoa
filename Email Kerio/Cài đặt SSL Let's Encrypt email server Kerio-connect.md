# Cài đặt SSL Let's Encrypt cho mail server Kerio-connect
Bước 1: Tại `Configuration` -> `SSL Certificates` chọn `New` -> `New Let's Encrypt Certificate` như hình bên dưới

![](./images/ssl.png)

- Điền thông tin -> `ok`

![](./images/ssl2.png)

Bước 3: `New` -> `New Certificate Request`

![](./images/ssl3.png)

- Điền thông tin -> `ok`

![](./images/ssl4.png)

Bước 4: `Export Certificate` và `Export Private Key` SSL Let's Encrypt Certificate đã tạo trước đó về máy

![](./images/ssl5.png)

Bước 5: Tại `Certificate Request` đã tạo trước đó click chuột phải chọn `Import` -> `Import a New Certificate`

![](./images/ssl6.png)

- `Select` các file vừa `Export` và `Import`

![](./images/ssl7.png)

Bước 6: Sau khi Import thành công `Certificate` mới được tạo ra

![](./images/ssl8.png)

- Để cho phép máy chủ sử dụng chứng chỉ này, hãy chọn chứng chỉ và nhấp vào nút `Set as Default`

![](./images/ssl9.png)

Bước 7: Kiểm tra

![](./images/ssl11.png)

![](./images/ssl10.png)