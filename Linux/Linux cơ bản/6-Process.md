# Process
Mỗi lệnh trên Linux khi thực thi sẽ 'run' một process hoặc một group các process
## 1. Tổng quan 
- Tất cả các chương trình trong Linux thực chất là các "process". Process chính là đơn vị cấu thành nên Linux
## 2. Kiểm tra tất cả các process đang chạy trên hệ thống
- Sử dụng lệnh `ps` và show thêm các thuộc tính `opid,ppid,user,rss,command` của process
```sh
ps -e -opid,ppid,user,rss,command
```

![](./images/ps.png)

> Ta có thể thấy mỗi một process sẽ có một process ID (PID) khác nhau và thuộc về một process ID cha (PPID) nào đó

## 3. Kiểm tra live các process đang chạy
```sh
top
```

![](./images/top.png)

- Thông tin được hiển thị:
	+ Dòng 1: 
		+ Thời gian
		+ Máy tính đã chạy được bao lâu rồi
		+ Số lượng người dùng
		+ Trung bình tải
		+ Trung bình tải hiển thị thời gian load hệ thống trong 1, 5 và 15 phút cuối.

	+ Dòng 2: 
		+ Tổng số nhiệm vụ
		+ Số lượng tác vụ đang chạy
		+ Số lượng tác vụ trong trạng thái “ngủ”
		+ Số lượng tác vụ đã dừng
		+ Số lượng tác vụ zombie (tiến trình không tồn tại)

	+ Dòng 3:
		+ Mức sử dụng CPU bởi người dùng theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi hệ thống theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi các tiến trình có mức ưu tiên thấp theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi idle process (tiến trình cho biết bộ xử lý đang rảnh rỗi) theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi io wait (thời gian CPU không hoạt động để chờ I/O disk hoàn thành) theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi việc ngắt phần cứng theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi việc ngắt phần mềm theo tỷ lệ phần trăm
		+ Mức sử dụng CPU bởi steal time (thời gian CPU ảo “chờ” CPU thực) theo tỷ lệ phần trăm

	+ Dòng 4:
		+ Tổng bộ nhớ hệ thống
		+ Bộ nhớ trống
		+ Bộ nhớ đã sử dụng
		+ Bộ nhớ đệm buffer cache

	+ Dòng 5: 
		+ Tổng swap có sẵn
		+ Tổng swap còn trống
		+ Tổng swap đã sử dụng
		+ Bộ nhớ khả dụng

	+ Bảng chính:
		+ ID tiến trình
		+ Người dùng
		+ Mức độ ưu tiên
		+ Mức độ nice (gọi một tập lệnh shell với mức độ ưu tiên cụ thể)
		+ Bộ nhớ ảo được sử dụng bởi tiến trình
		+ Bộ nhớ “thường trú” mà một tiến trình sử dụng (tức là tiến trình luôn ở trong bộ nhớ và không thể chuyển ra thiết bị lưu trữ khác)
		+ Bộ nhớ có thể chia sẻ
		+ CPU được sử dụng bởi tiến trình theo tỷ lệ phần trăm
		+ Bộ nhớ được sử dụng bởi tiến trình theo tỷ lệ phần trăm
		+ Thời gian tiến trình đã được chạy
		+ Lệnh

## 4. Sơ đồ pstree
- Lệnh `pstree` hiển thị các quy trình đang chạy trên hệ thống dưới dạng sơ đồ cây thể hiện mối quan hệ giữa một quy trình và quy trình mẹ của nó và bất kỳ quy trình nào khác mà nó tạo ra
```sh
pstree
```

![](./images/pstree.png)

## 5. Kill process
- Để dừng một Process nào đó ta dùng lệnh `kill [PID]` trong đó PID là giá trị oid của Process muốn dừng

## 6. Process ID
- Process ID được đánh số theo thứ tự tăng dần. Bắt đầu từ 0 và tăng dần lên khi tới giá trị maximum. Giá trị maximum của Process ID có thể cấu hình được tùy vào từng hệ thống
- Có thể thay đổi giá trị Process ID maximum bằng cách thay đổi file `/proc/sys/kernel/pid_max`

## 7. Process Resource
- Process Resource chính là bộ nhớ mà Process sử dụng, không gian địa chỉ của Process là riêng biệt, nhờ thiết kế này mà các Process là độc lập với nhau 
## 8. Forking 
- Khi fork một process mới, bộ nhớ của process con và process cha vẫn là độc lập. Tức là nếu process con không thay đổi các giá trị trong process cha, process con và process cha sẽ vẫn dùng chung bộ nhớ. Điều này làm cho các process con chỉ đọc, sẽ có memory rất nhỏ. Hay nói cách khác, Linux cung cấp cho chúng ta một công cụ để chạy các multiprogram với một lượng resource vửa đủ.
## 9. Delay processes
- Để trì hoãn 1 tiến trình ta có thể làm như sau
- Thêm đoạn text dưới vào file `tuu.sh` rồi chạy nó
```sh
!
echo "The system will go to sleep fo 5 seconds ..."
sleep 5
echo "The system is awaked"
```
```sh
./tuu.sh
```

![](./images/delayprocess.png)

>> Kết quả tiến trình sẽ ngủ 5 giây trước khi hoạt động