# Các thao tác cơ bản trên WebVirtCloud
## Thay đổi password admin
- Tài khoản và Mật khẩu mặc định là admin/admin, vì vậy bước đầu tiên ta cần phải đổi ngay mật khẩu

![](./images/webvirtcloud8.png)

![](./images/webvirtcloud9.png)

## Tạo user
- Click vào `+`

![](./images/webvirtcloud10.png)

- Nhập thông tin và chọn `Create`

![](./images/webvirtcloud11.png)

![](./images/webvirtcloud12.png)

- Nhấp vào biểu tượng bánh răng để phân quyền cho user vừa tạo
- Ở đây ta có thể phân quyền cho user là một user thường (is staff) hoặc một superuser (is superuser)
![](./images/webvirtcloud13.png)

## Tạo Storage Pool 

- Vào tab `Computes` chọn compute mà ta muốn tạo pools

![](./images/webvirtcloud14.png)

- Chọn `Storages`

![](./images/webvirtcloud15.png)

- Tạo một pool mới

![](./images/webvirtcloud16.png)

![](./images/webvirtcloud18.png)

- Sau khi tạo xong các pool

![](./images/webvirtcloud17.png)

## Tạo network 

![](./images/webvirtcloud19.png)

- Chọn name và mode network mà ta muốn thiết lập

![](./images/webvirtcloud20.png)

## Gán VM cho user thường 
- Nếu là user admin, ta có toàn quyền nhưng nếu ta là một user thường thì chỉ có thể sử dụng VM do superuser hay còn gọi là admin gán quyền. Và ta chỉ có thể thao tác với chính con VM đó chứ không phải là các computes chứa các VM

- Chọn User thường (tubui1)

![](./images/webvirtcloud21.png)

- Click `+`

![](./images/webvirtcloud22.png)


- Chọn VM thuộc compute sau đó click `Add`

![](./images/webvirtcloud23.png)

- Chọn edit nếu muốn thay đổi quyền quản trị của user đối với VM đó
- Ở đây ta không cho phép User tubui1 delete VM

![](./images/webvirtcloud24.png)

- Đăng nhập vào user `tubui1`

![](./images/webvirtcloud25.png)

- User `tubui1` có quyền Resize

![](./images/webvirtcloud26.png)

- User `tubui1` không có quyền Destroy

![](./images/webvirtcloud27.png)

## Tạo VM
- Để thực hiện tạo VM, user ta thực hiện phải là user có quyền admin

![](./images/webvirtcloud28.png)

- Lựa chọn `compute`

![](./images/webvirtcloud29.png)

- Có thể tạo VM từ `Flavor` có sẵn hoặc `Custom`

![](./images/webvirtcloud30.png)

- Nếu tạo từ `Flavor`

![](./images/webvirtcloud31.png)

- Chọn các thông số cần thiết để tạo máy ảo

![](./images/webvirtcloud32.png)

- Chọn các chế độ boot sau đó apply

![](./images/webvirtcloud33.png)

- Power On

![](./images/webvirtcloud34.png)

- Tiến hành cài đặt như bình thường

![](./images/webvirtcloud35.png)

## Một số tính năng hữu ích
Resize CPUs, RAM và dung lượng của ổ cứng 

- Nếu muốn resize dung lượng của ổ cứng, ta cần phải xóa các snapshot đi

![](./images/webvirtcloud37.png)

- Add thêm ổ cứng

![](./images/webvirtcloud36.png)

- Add thêm card mạng 

![](./images/webvirtcloud38.png)

- Phân quyền quản lyus VM cho user 

![](./images/webvirtcloud39.png)

- Xem log 

![](./images/webvirtcloud40.png)