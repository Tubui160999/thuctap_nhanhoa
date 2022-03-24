# Block 1 địa chỉ IP 
- Ví dụ block địa chỉ IP 117.4.255.125
```sh
server {
	deny 117.4.255.125
}
```

# Block 1 dải địa chỉ IP
- Ví dụ block địa chỉ IP 117.4.255.0
```sh
server {
	deny 117.4.255.0/24
}
```

# Block tất cả IP truy cập vào site
```sh
server {
	deny all;
}
```