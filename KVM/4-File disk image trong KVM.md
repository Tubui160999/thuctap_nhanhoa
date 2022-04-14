# File image trong KVM
- Công nghệ ảo hóa phần cứng QEMU rất giống với KVM. Cả hai đều được điều khiển thông qua libvirt, cả 2 đều hỗ trợ tính năng thiết lập giống nhau, và tất cả các hình ảnh máy ảo tương thích với KVM thì cũng tương thích với QEMU. Điểm khác biệt chính giữa QEMU và KVM là QEMU không hỗ trợ native virtualization, dó đó QEMU có hiệu suất kém hơn KVM 
- QEMU được sử dụng trong các trường hợp sau: 
	+ Chạy trên các phần cứng cũ không hỗ trợ ảo hóa 
	+ Chạy trên các dịch vụ Compute trên một máy ảo cho mục đích phát triển hoặc thử nghiệm
- QEMU hỗ trợ các định dạng hình ảnh máy ảo sau đây:
	+ Raw
	+ QEMU Copy-on-write (qcow2)
	+ VMware virtual machine disk format (vmdk)
- File Image (còn được gọi là file ảnh) của đĩa CD/DVD chính là một dạng file có định dạng theo các chuẩn tại file ảnh. File image là một file đóng gói hết tất cả nội dung của một đĩa CD/DVD vào trong nó
- Trong KVM Guest có 2 thành phần chính đó là VM definition được lưu dưới dạng file xml tại `/etc/libvirt/qemu`. File này chứa các thông tin của máy ảo như tên, số ram, số cpu... File còn lại là storage thường được lưu dưới dạng file image tại thư mục `/var/lib/libvirt/images`
- 3 định dạng thông dụng nhất của file image sử dụng trong KVM đó là iso, raw và qcow2
## Định dạng file image phổ biến trong KVM 
1. File ISO
- File ISO là file ảnh của 1 đĩa CD/DVD, nó chứa toàn bộ dữ liệu của đĩa CD/DVD đó. File ISO thường được sử dụng để cài đặt hệ điều hành của VM, người dùng có thể import trực tiếp hoặc tải từ Internet về
- Boot từ file ISO cũng là một trong số những tùy chọn mà người dùng có thể sử dụng khi tạo máy ảo
2. File raw
- Là định dạng file image phi cấu trúc 
- Khi người dùng tạo mới một máy ảo có disk format là raw thì dung lượng của file disk sẽ đúng bằng dung lượng của của ổ địa máy ảo bạn đã tạo
- Định dạng raw là hình ảnh theo dạng nhị phân (bit by bit) của ổ đĩa
- Mặc định khi tạo máy ảo với virt-manager hoặc không khai báo khi tạo VM bằng virt-install thì định dạng ổ đĩa sẽ là raw. Hay nói cách khác, raw chính là định dạng mặc định của QEMU
3. File qcow2
- Qcow2 là một định dạng tập tin cho image nơi các tập tin được sử dụng bởi QEMU. Viết tắt của "QEMU Copy On Write" và sử dụng cách thức tối ưu hóa lưu trữ disk để trì hoãn phân bổ dung lượng lưu trữ cho đến khi nó thực sự cần thiết. Các tập tin trong định dạng qcow có thể chứa một loạt các disk image thường được gắn liền với client cụ thể các hệ điều hành
- Qcow2 là một phiên bản cập nhật của định dạng qcow, nhằm để thay thế. Khác biệt với bản gốc là qcow2 hỗ trợ nhiều snapshots thông qua một mô hình mới. Khi khởi tạo máy ảo mới sẽ dựa vào disk này rồi snapshot thành một máy mới 
- Qcow2 hỗ trợ copy-on-write với những tính năng đặc biệt như snapshot, mã hóa, nén dữ liệu
	+ Các tập tin với định dạng này có thể phát triển khi dữ liệu được thêm vào. Điều này cho phép kích thước tệp nhỏ hơn hình ảnh đĩa thô, phân bổ toàn bộ không gian image vào tệp
	+ Định dạng qcow cũng cho phép lưu trữ các thay đổi được thực hiện với một base image chỉ đọc trên một tập tin qcow riêng biệt bằng cách sử dụng copy on write. Tập tin qcow mới này chứa đường dẫn đến base image để có thể tham chiếu trở lại khi cần thiết. Khi một phần dữ liệu cụ thể đã được đọc từ image mới này, nội dung sẽ được lấy ra từ nó nếu nó là mới và được lưu giữ ở đó; Nếu không, dữ liệu sẽ được lấy ra từ base image
	+ Tính năng tùy chọn bao gồm AES mã hóa và zlib dựa trên giải nén trong suốt
	+ Bất lợi của image qcow là không được gắn trực tiếp như disk image
- Copy on write (cow), đôi khi được gọi là chia sẻ tiềm ẩn, là một kỹ thuật quản lý tài nguyên được sử dụng trong lập trình máy tính để thực hiện có hiệu quả thao tác "nhân bản" hoặc "sao chép" trên các tài nguyên có thể thay đổi. Nếu một tài nguyên được nhân đôi nhưng không được sửa đổi thì không cần thiết phải tạo một tài nguyên mới. Tài nguyên có thể được chia sẻ giữa bản sao và bản gốc
- Qcow2 hỗ trợ việc tăng bộ nhớ bằng cơ chế Thin Provisioning
