# Virtualization
- Virtualization, hay còn gọi là ảo hóa, là một công nghệ được thiết kế để tạo ra tầng trung gian giữa hệ thống phần cứng máy tính và phần mềm chạy trên nó. Ý tưởng của công nghệ ảo hóa máy chủ là từ một máy vật lý đơn lẻ có thể tạo thành nhiều máy ảo độc lập. Mỗi một máy ảo đều có một thiết lập nguồn hệ thống riêng rẽ, hệ điều hành riêng và các ứng dụng riêng. Ảo hóa có nguồn gốc từ việc phân chia ổ đĩa, chúng phân chia một máy chủ thực thành nhiều máy chủ logic. Một khi máy chủ thực được chia, mỗi máy chủ logic có thể chạy một hệ điều hành và các ứng dụng độc lập
- Phân loại Virtuallizatione
	+ RAM virtualization
	+ CPU virtualization
	+ Network virtualization
	+ Device I/O virtualization

# Hypervisor/VMM (Virtual Machine Monitor)
- Hypervisor hay còn gọi là phần mềm giám sát máy ảo: Là một chương trình phần mềm quản lý một hoặc nhiều máy ảo (VM). Nó được sử dụng để tạo, startup, dừng và reset lại các máy ảo. Các hypervisor cho phép mỗi VM hoặc "guest" truy cập vào lớp tài nguyên phần cứng vật lý, chẳng hạn như CPU, RAM và lưu trữ. Nó cũng có thể giới hạn số lượng tài nguyên hệ thống mà mỗi máy ảo có thể sử dụng để đảm bảo cho nhiều máy ảo cùng sử dụng đồng thời trên cùng một hệ thống
- Hypervisor tạo nên một nền tảng ảo hóa (virtual platform) trên máy chủ, và dựa trên đó các máy ảo hoạt động và được quản lý
- Hypervisor chia thành 2 loại:
	+ Native of Bare Metal Hypervisor: Là các hệ phần mềm chạy trực tiếp trên phần cứng của máy chủ để kiểm soát và monitor các máy ảo. Các ví dụ điển hình của kiến trúc máy ảo này là: Oracle VM, Microsoft Hyper-V, VMware ESX và Xen
	+ Hosted Hypervisor: Hosted Hypervisor được thiết kế để có thể chạy được trên các hệ điều hành truyền thống. Các ví dụ điển hình của kiến trúc ảo hóa này là Oracle VM VirtualBox, VMware Workstation, KVM, QEMU, Parallels.
