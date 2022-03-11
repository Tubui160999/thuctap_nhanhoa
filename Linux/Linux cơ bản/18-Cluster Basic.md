# Cluster 
- Một cluster (Cụm) là hai hay nhiều máy tính làm việc cùng nhau để thực hiện một tác vụ. Ví dụ như là: cung cấp tính sẵn sàng cao cho một dịch vụ. Các cụm khả dụng cao cung cấp các dịch vụ khả dụng cao bằng cách loại bỏ những điểm bị lỗi và lỗi dịch vụ từ một thành viên của cụm đến những trường hợp khác không hoạt động 
- Thông thường, các dịch vụ trong cụm khả dụng cao, duy trì tính toàn vẹn của dữ liệu 
- Trong Linux, có nhiều công cụ cụm đạt được tính sẵn sàng cao cho tài nguyên. Công cụ được sử dụng nhiều nhất là Pacemaker. 
- Một cụm được định cấu hình với Pacemaker bao gồm các trình nền thành phần riêng biệt theo dõi các thành viên trong cụm, tập lệnh quản lý dịch vụ và các hệ thống con quản lý tài nguyên theo dõi tài nguyên
- Kiến trúc Pacemaker gồm:
	+ Cluster Information Base (Cụm thông tin cơ sở): Trình thông tin Pacemaker phân phối, đồng bộ cấu hình cụm và trạng thái thông tin điều phối được chỉ định (DC) của cụm tới tất cả các thành viên trong cụm. DC là một thành viên cụm được chỉ định để lưu trạng thái cụm 
	+ Cluster Resource Management Daemon (Quản lý tài nguyên cụm): Tài nguyên cụm được quản lí bởi thành phần này có thể được truy vấn bởi hệ thống máy khách, di chuyển, khởi tạo và thay đổi khi cần thiết. Mỗi nút cụm bao gồm một trình nền quản lý tài nguyên cục bộ hoạt động như một giao diện giữa trình nền quản lý tài nguyên cụm và chính tài nguyên đó