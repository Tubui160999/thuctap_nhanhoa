# Samba Server và Windows File Sharing
## Khái niệm
-Samba Server được xem là một máy chủ tập tin (File Server), sử dụng trong mạng nội bộ. Là nơi lưu trữ tập trung các thông tin của một tổ chức, doanh nghiệp bất kỳ và thường được cài đặt trên hệ điều hành Linux hoặc Windows
- Samba Server hoạt động chủ yếu dựa trên giao thức SMB (Server Message Block Protocol)
## Cách thức hoạt động của giao thức SMB
- Giao thức SMB hoạt động trong mạng Internet dựa trên giao thức TCP/IP. Và đem cho người dùng toàn quyền trong việc tạo một tập tin với các quyền hạn như (read, write, excute). Ngoài ra SMB còn hỗ trợ các tính năng như:
	+ Phát hiện các máy chủ sử dụng SMB trên mạng (browse network)
	+ Xác thực truy cập file, thư mục chia sẻ
	+ Thông báo sự thay đổi file và thư mục
	+ Xử lý các thuộc tính mở rộng của file
	+ Hỗ trợ Unicode
## Dịch vụ
- Samba bao gồm các dịch vụ sau:
	+ `smbd`: Cung cấp dịch vụ chia sẻ tệp và máy in cho các Windows Client. Ngoài ra nó còn chịu trách nhiệm xác thực người dùng, khóa tài nguyên và chia sẻ dữ liệu thông qua giao thức SMB. Cổng mặc định mà máy chủ lắng nghe lưu lượng SMB là TCP 139 và 445
	+ `nmbd`: Hiểu và trả lời NetBIOS qua các yêu cầu dịch vụ bởi SMB trong các hệ thống dựa trên Windows. Cổng mặc định mà máy chủ lắng nghe lưu lượng NMB là UDP 137
	+ `winbinđd`: Là dịch vụ phân giải thông tin người dùng và nhóm nhận được từ máy chủ chạy Windows. Điều này giúp cho người dùng Windows và thông tin các nhóm có thể hiểu được bởi các nền tảng Linux và UNIX. Nó cho phép người dùng Windows xuất hiện và hoạt động như người dùng Linux
- Cả `winbindd` và `smbd` đều được đóng gói với các bản phân phối của Samba, nhưng dịch vụ `winbindd` được kiểm soát tách biệt từ dịch vụ `smbd`
