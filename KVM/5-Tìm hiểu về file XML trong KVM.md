# Tổng quan về file XML
- VM trong KVM có 2 thành phần chính đó là VM's definition được lưu dưới dạng file XML mặc định ở thư mục `/etc/libvirt/qemu` và VM's storage lưu dưới dạng file image
- File domain XML chứa những thông tin về thành phần của máy ảo (số CPU, RAM, các thiết lập của I/O devices...)
- Libvirt dùng những thông tin này để tiến hành khởi chạy tiến trình QEMU-KVM tạo máy ảo
- KVM cũng có các file XML khác để lưu các thông tin liên quan tới network, storage...
- Mục đích chính của XML là đơn giản hóa việc chia sẻ dữ liệu giữa các hệ thống khác nhau, đặc biệt là các hệ thống được kết nối với Internet
## Các thành phần của file XML
- File XML tổ chức theo khối lệnh, có nhiều khối lệnh cùng trong 1 khối lệnh tổng quan, cú pháp giống HTML có thẻ đóng, thẻ mở 

![](./images/filexml.png)

- Thẻ quan trọng không thể thiếu trong file domain xml là `domain`
	+ Tham số `type` cho biết hypervisor đang sử dụng của VM 
	+ Các tham số bên trong có ý nghĩa như sau:
		+ `name`: Thông tin về VM
		+ `uuid`: Mã nhận dạng quốc tế duy nhất cho máy ảo. Format theo RFC 4122. Nếu thiếu trường `uuid` khi khởi tạo, mã này sẽ được tự động generate
	+ Một số thẻ khác có thêm thông tin về các tham số như sau:
		+ `title`: Tiêu đề của máy ảo
		+ `description`: Đoạn mô tả của máy ảo
		+ `metadata`: Chứa những thông tin về file xml
		+ `memory`: Dung lượng RAM của máy ảo được cấp khi khởi tạo máy
		+ `unit`: Đơn vị, mặc định là KiB
		+ `currentMemory`: Dung lượng RAM đang được sử dụng tại thời điểm trích xuất file XML
		+ `maxMemory`: Dung lượng RAM tối đa có thể sử dụng 
		+ `vcpu`: Tổng số vcpu máy ảo được cấp khi khởi tạo

	+ `vcpu` có một số tham số:
		+ `cpuset`: Danh sách các cpu vật lý mà máy ảo sử dụng
		+ `current`: Chỉ định cho phép kích hoạt nhiều hơn số CPU đang sử dụng 
		+ `placement`: Vị trí của cpu, giá trị bao gồm static và dynamic 
	+ Block OS: Chứa các thông tin về hệ điều hành của máy ảo
		+ `arch`: Hệ điều hành thuộc kiến trúc 32 hay 64 bit 
		+ `machine`: Thông tin về kernel của hệ điều hành
		+ `loader`: Readonly có giá trị yes hoặc no chỉ ra file image writable hay readonly, type có giá trị rom hoặc pflash chỉ ra nơi guest memory được kết nối
		+ `kernel`: Đường dẫn tới kernel image trên hệ điều hành máy chủ
		+ `initrd`: Đường dẫn tới ramdisk image trên hệ điều hành máy chủ
		+ `cmdline`: Xac định giao diện điều khiển thay thế
	+ Hành động xảy ra đối với một số sự kiện của OS 
		+ `on_poweroff`: Hành động được thực hiện khi người dùng yêu cầu tắt máy
		+ `on_reboot`: Hành động được thực hiện khi người dùng yêu cầu reset máy
		+ `on_crash`: Hành động được thực hiện khi có sự cố
	+ Những hành động được phép thực thi:
		+ `destroy`: Chấm dứt và giải phóng tài nguyên
		+ `restart`: Chấm dứt rồi khởi động lại giữ nguyên cấu hình
		+ `preserve`: Chấm dứt nhưng dữ liệu vẫn được lưu lại
		+ `rename-restart`: Khởi động lại với tên mới
		+ `destroy` và `restart` được hỗ trợ trong cả `on_poweroff` và `on_reboot`, rename-restart dùng trong on_poweroff 
	+ CPU: Khuyến cáo đối với CPU model, các tính năng và cấu trúc liên kết của nó có thể được xác định bằng cách sử dụng tập hợp các phần tử sau
		```sh
		...
		<cpu match='exact'>
		  <model fallback='allow'>core2duo</model>
		  <vendor>Intel</vendor>
		  <topology sockets='1' cores='2' threads='1'/>
		  <cache level='3' mode='emulate'/>
		  <feature policy='disable' name='lahf_lm'/>
		</cpu>
		...
		```
		```sh
		<cpu mode='host-model'>
		  <model fallback='forbid'/>
		  <topology sockets='1' cores='2' threads='1'/>
		</cpu>
		```
		```sh
		<cpu mode='host-passthrough'>
		  <cache mode='passthrough'/>
		  <feature policy='disable' name='lahf_lm'/>
		...
		```
	+ CPU chứa các mô tả yêu cầu của guest CPU, thuộc tính `match` của nó xác định mức độ liên kết của CPU ảo được cung cấp cho guest phù hợp với các yêu cầu này. Một số giá trị mà `match` có thể có là:
		+ `minimum`
		+ `exact`
		+ `strict`

	+ `clock`: Thiết lập về thời gian
		```sh
		<clock offset='utc'>
		    <timer name='rtc' tickpolicy='catchup'/>
		    <timer name='pit' tickpolicy='delay'/>
		    <timer name='hpet' present='no'/>
		</clock>
		```
	+ `offset`: Giá trị utc, localtime, timezone, variable
	+ `feature`: Là hypervisors cho phép thao tác một số tính năng như bật/tắt
		```sh
		<features>
		  <pae/>
		  <acpi/>
		  <apic/>
		  <hap/>
		  <privnet/>
		  <hyperv>
		    <relaxed state='on'/>
		    <vapic state='on'/>
		    <spinlocks state='on' retries='4096'/>
		    <vpindex state='on'/>
		    <runtime state='on'/>
		    <synic state='on'/>
		    <reset state='on'/>
		    <vendor_id state='on' value='KVM Hv'/>
		    <frequencies state='on'/>
		    <reenlightenment state='on'/>
		    <tlbflush state='on'/>
		  </hyperv>
		  <kvm>
		    <hidden state='on'/>
		  </kvm>
		  <pvspinlock state='on'/>
		  <gic version='2'/>
		  <ioapic driver='qemu'/>
		  <hpt resizing='required'>
		    <maxpagesize unit='MiB'>16</maxpagesize>
		  </hpt>
		  <vmcoreinfo state='on'/>
		  <smm state='on'>
		    <tseg unit='MiB'>48</tseg>
		  </smm>
		  <htm state='on'/>
		</features>
		```
		+ `pae`: Chế độ địa chỉ vậy lý mở rộng cho phép 32 bit và lớn hơn 4 GB RAM
		+ `acpi`: Sử dụng trong việc quản lý máy ảo, ví dụ bắt buộc tắt máy
		+ Ngoài ra còn các thẻ khác như: `apic`, `hap`, `viridian`, `privnet`, `hyperv`, `pvspinlock`, `kvm`, `pmu`, `vmport`, `gic`, `smm`, `ioapic`, `hpt`, `vmcoreinfo`, `htm`
	+ Block device: Khai báo thông tin về thành phần của máy ảo như disk, network..
		+ `emulator`: Khai báo đường dẫn tới thư viện ảo hóa các device
		+ `device='disk'`: Khai báo thông tin về disk của máy ảo
		```sh
		<disk type='file' device='disk'>
		    <driver name='qemu' type='qcow2'/> : định dạng disk
		    <source file='/var/lib/libvirt/images/centos6.9.img'/>: Đường dẫn chứa disk
		    <target dev='vda' bus='virtio'/>: Tên ổ, kiểu ảo hóa
		    <boot order='2'/>: Thứ tự ưu tiên boot của ổ.
		    <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
		</disk>
		```
		+ `device='cdrom'`: Thông tin về ổ đĩa CDROM
		```sh
		<disk type='file' device='cdrom'>
		    <driver name='qemu' type='raw'/>
		    <target dev='hda' bus='ide'/>
		    <readonly/>
		    <boot order='1'/>
		    <address type='drive' controller='0' bus='0' target='0' unit='0'/>
		</disk>
		```
	+ Interface: Khai báo thông tin về Network

## Tạo máy ảo từ file XML
- Ta phải có một file XML khai báo đầy đủ các thông số của máy ảo. Có thể thực hiện theo 2 cách
	+ Cách 1: Khai báo file xml đúng cấu trúc
	+ Cách 2: Dump 1 máy ảo hiện có hoặc copy file xml máy ảo hiện có ra sử dụng cấu trúc máy ảo đó và thay thế tham số cần thiết
- Ở đây ta sử dụng cách copy file xml của một máy ảo hiện có và chỉnh sửa tham số cần thiết
Bước 1: Thay đổi tham số cần thiết
- Những tham số cần thay đổi 
- Thông tin về cấu hình
```sh
- Thông tin RAM, vCPU, disk

- Đường dẫn tới disk: /var/lib/libvirt/images/tubui.img

- Máy ảo được boot từ CDROM (/var/lib/libvirt/images/CentOS-7-x86_64-Minimal-2009.iso)

- Card mạng: Sử dụng Linux Bridge br0
```
Bước 2: Install KVM
```sh
yum install -y qemu-kvm libvirt libvirt-python libguestfs-tools virt-install bridge-utils
```

Bước 2: Tạo disk
- Tạo một ổ đĩa cho máy ảo khai báo dung lượng và định dạng là raw
```sh
yum -y install qemu-img
```

```sh
qemu-img create -f raw /var/lib/libvirt/images/tubui.img 15G
```

![](./images/createdisk.png)

Bước 3: Tạo `uuid`
- Tạo mã uuid, cài đặt gói uuid và generate đoạn mã uuid
```sh
yum install uuid -y
uuid
```

![](./images/uuid.png)

Bước 4: Khởi tạo máy ảo
Copy file xml đã chỉnh sửa vào node KVM

```sh
<domain type='kvm'>
  <name>tubui</name>
  <uuid>4e893778-bbb5-11ec-9796-b8ca3a5eb048</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static'>5</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-rhel7.0.0'>hvm</type>
    <boot dev='cdrom'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>SandyBridge</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/libexec/qemu-kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/tubui.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
	  <source file="/var/lib/libvirt/images/CentOS-7-x86_64-Minimal-2009.iso"/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:28:5f:94'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='unix'>
      <target type='virtio' name='org.qemu.guest_agent.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='2'/>
    </channel>
    <input type='tablet' bus='usb'>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

- Sử dụng lệnh virsh để tạo máy ảo từ file xml vừa chỉnh sửa 
```sh
virsh create tubui.xml
```

- Sử dụng lệnh `virt-manager` để hiển thị cửa sổ mới với VM vừa tạo
```sh
yum install -y virt-manager
virt-manager
```

- Tiến hành cài đặt OS cho máy ảo như bình thường

![](./images/tubui.png)

