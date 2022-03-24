# Giới thiệu về DirectAdmin
- DirectAdmin là một trong những Bảng điều khiển (Control Pannel) dành cho người quản trị Web Hosting được ưa chuộng hiện nay với giao diện trực quan, dễ dàng sử dụng. DirectAdmin cung cấp các tính năng như xem, thay đổi thiết lập phần cứng và phần mềm máy chủ. Đồng thời nâng cao tính bảo mật và kiểm soát tài khoản người dùng.
- DirectAdmin hướng đến sự đơn giản, tiện dụng, tốc độ và sự ổn định. Nhưng vẫn có đầy đủ các tính năng cần thiết cho một quản trị hosting server. Việc quản trị máy chủ và chia sẻ trang web sẽ được thực hiện một cách dễ dàng hơn
# Ưu và nhược điểm của DirectAdmin
## Ưu điểm 
- Phương thức sử dụng đơn giản: DirectAdmin được phân cấp thành 3 loại tài khoản, thứ tự cấp quyền cao đến thấp là Administrator, Reseller và User. Người dùng có thể dễ dàng chuyển đổi giữa 3 loại tài khoản 1 cách dễ dàng
- Tốc độ xử lý nhanh, ít tiêu tốn tài nguyên: DirectAdmin có tốc độ xử lý nhanh chóng và khả năng thích ứng cao. Bên cạnh đó giao diện của phần mềm này cũng được thiết kế theo hướng tối giản, dễ sử dụng và ít tiêu tốn tài nguyên hệ thống
- Ổn định: Tính ổn định của DirectAdmin rất cao. Nó có thể hoạt động trong thời gian dài mà không mắc phải lỗi hệ thống như các phần mềm quản trị hosting khác. DirectAdmin còn có khả năng tự phục hồi trong trường hợp xảy ra lỗi bằng cách khởi động lại hệ thống.
- Gía bản quyền thấp: Giá cả hợp lý là điều vẫn giữ cho DA cạnh tranh trong khi thị trường nơi tồn tại các giải pháp hoàn thiện hơn nhiều. DA còn cung cấp một tài khoản dùng thử miễn phí
## Nhược điểm
- Không hỗ trợ tiếng việt
- Khả năng thêm các chức năng: Về mặt này DirectAdmin còn khá hạn chế. Tuy nhiên, vẫn có thể thêm các chức năng nhưng sẽ tốn thêm chi phí cho việc này
- Cộng đồng người dùng ít: Sẽ khó để tìm được các câu trả lời hướng dẫn cho DirectAdmin khi gặp một vấn đề khó khăn nào đó vì không có quá nhiều cộng động sử dụng DirectAdmin.
# Các tính năng của DirectAdmin
## Chức năng của Administrator trong DirectAdmin
- Create/Modify Admins and Resellers:
	+ Admin có thể tạo Reseller hoặc bổ sung một Admin mới một cách nhanh chóng và dễ dàng
- Reseller Package:
	+ Admin có thể tạo các gói tài khoản với các thông số được xác định trước bằng cách sử dụng tính năng `Reseller Package`. Đến khi tạo tài khoản, Admin chỉ cần chọn 1 gói thay vì thiết lập thử công từng tính năng cho tài khoản
- Show All User: Tính năng này cho phép Admin xem nhanh từng tài khoản trên hệ thống và sắp xếp danh sách này theo nhiều cách khác nhau
- DNS Administration: Cho phép Admin tạo, sửa đổi hoặc xóa bất kỳ bản ghi DNS nào trên máy chủ
- IP Manager: Đây là nơi Admin đặt địa chỉ IP có sẵn cho máy chủ. Admin cũng có thể phân bổ địa chỉ IP cho Reseller từ menu này
- Mail Queue Administration: Công cụ để xem danh sách mail và message. Bao gồm các công cụ để thực hiện hành động đối với các message đó
- System/Services Info: Admin có thể xem, dừng, bắt đầu và khởi động lại các dịch vụ từ menu này
- Complete Usage Statistics: Tính năng này cung cấp cho Admin  một cái nhìn tổng quan đầy đủ về việc sử dụng hệ thống. Đầu vào và đầu ra chính xác từ card Ethernet của máy chủ cũng được giám sát
- DNS Clustering: DirectAdmin giao tiếp với các máy DirectAdmin khác để tự động chuyển dữ liệu DNS giữa chúng. Nó có khả năng kiểm tra máy chủ khác để tìm tên miền và không cho phép các tên miền trùng lặp trên DirectAdmin của bạn
- SPAM fighting tools in DirectAdmin: Nhiều công cụ chống SPAM được cung cấp bởi DirectAdmin
- Licensing/Updates: Admin có thể xem trạng thái giấy phép của mình và tải xuống các bản nâng cấp phần mềm và bảo mật DirectAdmin mới nhất từ menu này
## Chức năng của Reseller trong DirectAdmin
- Create/List/Modify Accounts: Việc tạo, liệt kê, sửa đổi và xóa tài khoản được thực hiện nhanh chóng và dễ dàng
- User Packages: Reseller có thể tạo các Packages được xác định trước bằng cách sử dụng tính năng này. Khi tạo tài khoản, Reseller chỉ cần chọn một Package thay vì thiết lập từng tính năng tài khoản theo cách thủ công
- Reseller Statistics: Reseller được cung cấp thông tin tổng quan đầy đủ về tổng mức sử dụng của họ. Reseller cũng có thể sắp xếp dữ liệu theo User để nhanh chóng đánh giá tình hình tổng thể
- Message All Users: Reseller có thể nhanh chóng gửi tin nhắn đến tất cả khách hàng của họ bằng cách sử dụng hệ thống hỗ trợ ticket được tích hợp sẵn của DirectAdmin
- Import/Manage Skins: Với tùy chọn menu này, Reseller có thể nhanh chóng import và áp dụng giao diện mới chỉ bằng một nút bấm
- IP Assignment: Reseller có thể phân bổ địa chỉ IP cho khách hàng của họ bằng cách sử dụng tùy chọn menu này
- System/Services Information: Bằng cách nhấp vào tính năng này, Reseller có quyền truy cập tức thì vào trạng thái máy chủ và thông tin hệ thống
- Name Servers: Reseller có thể tạo nameservers được cá nhân hóa cho khách hàng của họ từ menu này
## Chức năng của User trong DirectAdmin
- E-mail Administration: User có thể tạo tài khoản POP/IMAP, địa chỉ e-mail, forwarder, danh sách gửi thư, thư trả lời tự động và webmail. Bộ lọc cho phép người dùng chặn mail theo tên miền, từ khóa và kích thước
- FTP Management: User có thể tạo tài khoản FTP và thiết lập quyền thư mục cho từng tài khoản. FTP ẩn danh cũng được hỗ trợ
- DNS Menu: User có thể thêm và xóa các bản ghi, thay đổi cài đặt MX và bất kỳ thứ gì khác với toàn quyền kiểm soát DNS
- Statistics Menu: User có sẵn mọi thống kê về tài khoản của họ. Các tùy chọn nâng cao hơn và Webalizer cũng được bao gồm
- Subdomains Menu: User có thể liệt kê, tạo, xóa và lấy số liệu thống kê về các subdomains
- File Manager: Một sự thay thế nhanh chóng và thân thiện với người dùng cho FTP. Bao gồm mọi tính năng cần thiết để xây dựng và duy trì một trang web
- MySQL Databases: User có thể dễ dàng tạo, sửa đổi và xóa cơ sở dữ liệu MySQL từ menu này
- Site Backup: Sử dụng công cụ hữu ích này, User có thể sao lưu và khôi phục những gì họ muốn
- Error Pages: User có thể tạo các thông báo và kết quả đầu ra tùy chỉnh cho các mã lỗi 401, 403, 404 và 500
- Directory Password Protection: User có thể đặt mật khẩu bảo vệ bất kỳ thư mục nào bằng tên username và password
- PHP Selector: Cho phép khách hàng chọn phiên bản PHP nào sẽ được liên kết với phần mở rộng .php
- Advanced Tools: User có thể cài đặt chứng chỉ SSL, xem thông tin máy chủ và các mô-đun perl đã cài đặt, đặt cron job, mime types và trình xử lý apache, đồng thời cho phép chuyển hướng trang web và trỏ tên miền
## Chức năng chung trong DirectAdmin
- Integrated Ticket Support System: Với hệ thống tích hợp hỗ trợ ticket của DA, bạn sẽ được cung cấp dịch vụ hỗ trợ khách hàng tốt hơn và ít rắc rối hơn. "Bạn có XX tin nhắn đang chờ" được hiển thị mỗi khi đăng nhập và bạn có thể đặt DA thông báo cho bạn về các yêu cầu hỗ trợ qua email, đảm bảo rằng không có yêu cầu nào bị bỏ qua. Nếu muốn cung cấp hỗ trợ theo một cách khác, chỉ cần tắt tính năng này.
- Two-Factor Authentication: Cho phép bất kỳ tài khoản DirectAdmin nào yêu cầu Xác thực hai yếu tố bằng mã từ ứng dụng trên smartphone
- Plugin System: Cho phép mở rộng chức năng DirectAdmin một cách dễ dàng
- Live Updates: Quản trị viên máy chủ có thể nhấp vào nút 'Licensing/update' để xem trạng thái phiên bản và giấy phép hiện tại. Không cần phải tải xuống, giải nén và cài đặt theo thủ công - DA tự động thực hiện tất cả các bản cập nhật
- Completely Customizable: Mọi khía cạnh của giao diện DirectAdmin đều có thể được thay đổi và các thiết kế mới được import dễ dàng thông qua menu “skin”
- Automatic Recovery From Crashes: DirectAdmin TaskQueue đảm bảo rằng tất cả các dịch vụ luôn hoạt động. Nếu có sự cố, DirectAdmin sẽ cố gắng khắc phục sự cố bằng cách khởi động lại dịch vụ. Nếu không thành công, DirectAdmin sẽ thông báo cho quản trị viên máy chủ ngay lập tức.

