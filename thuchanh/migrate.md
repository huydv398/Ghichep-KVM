# Live migrate trên KVM
I. [Tổng quan](#tongquan)
II. [Chuẩn bị](#chuanbi)
III. [Điểm nổi bật](#noibat)
IV. [Cài đặt](#caidat) 
1. [Cài đặt NFS](#nfs)
2. [Cài đặt KVM](#kvm)
3. [Kết nối qemu giữa hai KVM host](#qemu)
4. [Migrate](#mig)



<a name="caidat"></a>
<a name="nfs"></a>
<a name="kvm"></a>
<a name="qemu"></a>
<a name="mig"></a>



<a name="tongquan"></a>
## Tổng quan
Trong quá trình vận hành để phục vụ cho việc bảo trì và nâng cấp hệ thống chúng ta cần chuyển các VM từ host này sang host khác. Với các VM đang chạy các ứng dụng quan trọng chúng ta không thể tắt nó đi trong quá trình di chuyển. Trên KVM việc live migrate sẽ đảm bảo được các yêu cầu này

* Máy 64bit chỉ có thể di chuyển sang máy chủ 64, nhưng máy 32bit có thể di chuyển xang máy bất kỳ.

### Yêu cầu
- Image VM có thể truy cập được trên cả máy chủ nguồn và máy đích
- Máy chủ nguồn và máy chủ đích cùng dải mạng(giữ mạng của khách khi tap được sử dụng)
- Không sử dụng tùy chọn lệnh `-snapshot`
<a name="chuanbi"></a>
## Chuẩn bị

<a name="noibat"></a>
## Điểm nổi bật

* Không gây sự chú ý của khách hàng về down time
* Khả năng chuyển đổi trạng thái VM đường chuyển thông qua một chương trình bên ngoài.
* Khi thành công, khách hàng tiếp tục chạy trên máy chủ đích, khi thất bại, khách tiếp tục chạy trên máy nguồn
* Nhanh và đơn giản
* Độc lập phần cứng
* Hỗ trợ di chuyển máy ảo đã dừng hoặc tạm dừng
* 
### Mô Hình
### Cơ chế cơ bản của Live migrate
## Cài đặt
### Cấu hình phân giải tên miền 
### Cài đặt NFS
### Cài đặt KVM
### Kết nối qemu giữa hai KVM host
### Migrate

