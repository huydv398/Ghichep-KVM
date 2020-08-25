# Hướng dẫn sử dụng WebVirtCloud
## Tạo Storage pool

![huydv](../image/Screenshot_169.png)

![huydv](../image/Screenshot_173.png)

![huydv](../image/Screenshot_172.png)

## Tạo network 
![huydv](../image/Screenshot_174.png)

![huydv](../image/Screenshot_175.png)
* NAT: Đối với NAT máy có thể ping được ra bên ngoài nhưng bên ngoài không thể ping được tới địa chỉ IP đang sử dụng NAT

![huydv](../image/Screenshot_177.png)

![huydv](../image/Screenshot_176.png)

## Gắn VM cho User thường
Tạo 1 User thường

Chọn VM:

![huydv](../image/Screenshot_178.png)

![huydv](../image/Screenshot_179.png)

Add để lưu

Kết quả:
![huydv](../image/Screenshot_180.png)

Thay đổi quyền của User:
![huydv](../image/Screenshot_181.png)

## Tạo VM
Để tạo được VM user phải có quyền admin

![huydv](../image/Screenshot_182.png)

Chọn Cụm KVM:

![huydv](../image/Screenshot_183.png)
* Flavor:
Cụm có các cấu hình mặc định của WebVirtCloud:

![huydv](../image/Screenshot_184.png)

Điền thông tin cho VM

![huydv](../image/Screenshot_185.png)

Tùy chọn boot

![huydv](../image/Screenshot_186.png)

Cấu hình Disk, mount file iso

![huydv](../image/Screenshot_187.png)

Hoặc có thể add disk có VM tại đây

![huydv](../image/Screenshot_188.png)

Điền thông tin disk mới => **Add Volume**

![huydv](../image/Screenshot_189.png)

![huydv](../image/Screenshot_190.png)

Bật VM

![huydv](../image/Screenshot_191.png)

Truy cập Console để cấu hình begin cho VM

![huydv](../image/Screenshot_192.png)

Cài đặt như bình thường:

![huydv](../image/Screenshot_193.png)

* Custom: tạo VM tùy chọn điền đầy đủ thông tin muốn cài đặt cho VM => **create** 

![huydv](../image/Screenshot_194.png)

Tạo các bước tiếp theo làm giống bên trên



## log

Để xem các thao tác của user và admin xem tại **log**

![huydv](../image/Screenshot_195.png)
