# Network File System (NFS)
## Giới thiệu
- NFS (Network File System) cho phép gắn kết các hệ thống tệp cục bộ của mình qua mạng và các máy chủ từ xa để tương tác với chúng khi chúng được gắn cục bộ trên cùng một hệ thống
## Lợi ích
- NFS cho phép truy cập cục bộ vào các tệp từ xa
- Nó sử dụng kiến trúc client/server tiêu chuẩn để chia sẻ tệp giữa các máy
- Với NFS, không cần thiết cả 2 máy đều phải chạy trên cùng một hệ điều hành
- Với NFS, có thể cấu hình các giải pháp lưu trữ tập trung
- Người dùng có được dữ liệu của họ bất kể vị trí thực tế
- Không cần làm mới thủ công cho các tập tin mới
- Hỗ trợ acl, mount root ảo
- Hỗ trợ bảo mật với tường lửa và kerberos
## Dịch vụ NFS
- NFS bao gồm `portmap` và `nfs-utils package`
	+ `portmap`: Nó ánh xạ các cuộc gọi được thực hiện từ các máy khác đến dịch vụ RPC
	+ `nfs`: Nó dịch các yêu cầu chia sẻ tệp từ xa thành các yêu cầu trên hệ thống tệp cục bộ
	+ `rpc.mountd`: Dịch vụ này có trách nhiệm lắp và unmount toàn bộ các hệ thống tập tin
- Các tệp quan trọng cho cấu hình NFS
	+ `/etc/export`: Đây là tệp cấu hình chính của NFS, tất cả các tệp và thư mục đã xuất được xác định 
	+ `/etc/fstab`: Để gắn một thư mục NFS trên hệ thống trên các lần khởi động lại, chúng ta cần tạo một mục trong `etc/fstab`
	+ `/etc/sysconfig/nfs`: Tệp cấu hình của NFS để kiểm soát cổng rpc và các dịch vụ đang nghe