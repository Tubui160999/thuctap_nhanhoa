# System Info
- Xem thông tin hệ điều hành
```sh
cat /etc/*release
```

![](./images/tthdh.png)

- Kernel version: 
```sh
uname -r
```

![](./images/kernelversion.png)

- Thông tin bộ nhớ: 
```sh
head /proc/meminfo
```

![](./images/ttbonho.png)

- File hệ thống 
```sh
df -h
```

![](./images/filehethong.png)

- Đếm số lượng CPU: 
```sh
cat /proc/cpuinfo | grep model
```

![](./images/solgcpu.png)

- Tên máy chủ
```sh
cat /etc/hostname
```

![](./images/hostname.png)

- Đổi tên máy chủ
```sh
hostnamectl set-host name tubuixyz
```

![](./images/sethostname.png)

- Hệ thống tập tin `proc` chứa các tập tin ảo mà chỉ tồn tại trong bộ nhớ. Một số tập tin quan trọng trong `/proc` bao gồm
```sh
/proc/cpuinfo
/proc/interrupts
/proc/meminfo
/proc/mounts
/proc/partitions
/proc/version
/proc/<process-id-#>
/proc/sys
```

> Hệ thống tập tin /proc rất hữu ích vì thông tin mà nó báo cáo chỉ được thu thập khi cần thiết và không bao giờ cần lưu trữ trên đĩa.