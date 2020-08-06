# Tìm hiểu một số mô hình mạng trong KVM

Cũng giống như các công cụ ảo hóa khác KVM cũng cung cấp các mô hình mạng trong việc ảo hóa Network.

## 1. NAT

![huydv](../image/Screenshot_44.png)

Với mô hình này KVM thực hiện ánh xạ một dải địa chỉ mạng để cung cấp cho máy ảo. Dải địa chỉ ta có thể giao tiếp với Internet. Nhưng có một chú ý rằng từ VM có thể ping được ra ngoài Internet nhưng máy bên ngoài sẽ không tháy được VM của ta chính vì vậy ta không thể ping từ bên ngoài đến VM sử dụng mô hình mạng NAT.

### Cách cấu hình.
Bình thường khi cài KVM nó sẽ cung cấp cho ta một mạng ảo NAT mang tên `defaul` mạng này thường mang dải địa chỉ IP `192.168.122.x`. Ta có thể add thêm một mạng ảo cũng với mô hình NAT khác. Có nhiều cách để thực hiện việc này nhưng ở đây tôi dùng công cụ Virt-manager.


Thông tin của dải mạng defaul:

![huydv](../image/Screenshot_37.png)

### Add một mạng ảo với mô hình NAT

Tại Virt-manager : Chọn **Edit** -> **Connection Details**

![huydv](../image/Screenshot_38.png)


Chọn địa chỉ dải mạng cho mạng định tạo. Sau đó chọn một dải IP cấp phát DHCP cho máy ảo trong dải mạng. Ta cũng có thể đặt IP tĩnh trên máy ảo nếu tích vào 

![huydv](../image/Screenshot_39.png)

Bỏ qua đối với IPv6

![huydv](../image/Screenshot_40.png)

Xác định mô hình muốn sử dụng:

![huydv](../image/Screenshot_41.png)

### Thao tác trên VM

![huydv](../image/Screenshot_42.png)

Reboot lại máy ảo và kiểm tra lại.

![huydv](../image/Screenshot_43.png)


## Host-only
Với mô hình mạng Host-only, cũng cho phép cấp phát địa chỉ tùy ý không giống mô hình NAT. Nhưng ở đây máy ảo không thể trao đổi với các máy tính bên ngoài. Nó chỉ có thể trao đổi thông tin với các máy tính trong cùng dải mạng bên trong máy server vật lý và trao đổi với với chủ vật lý.

![huydv](../image/Screenshot_44.png)

### Cấu hình
Ta cũng làm tương tự như cấu hình NAT.


![huydv](../image/Screenshot_46.png)

![huydv](../image/Screenshot_47.png)

![huydv](../image/Screenshot_48.png)

Thao tác trên máy ảo.

* Thêm 1 card mạng

![huydv](../image/Screenshot_49.png)

![huydv](../image/Screenshot_50.png)

Reboot và kiểm tra

![huydv](../image/Screenshot_51.png)

![huydv](../image/Screenshot_52.png)

![huydv](../image/Screenshot_53.png)

![huydv](../image/Screenshot_54.png)

## Bridge

Ở mô hình ta tìm hiểu về công nghệ Linux Bridge. Linux Bridge là một phần mềm được thích hợp trong nhân Linux giải quyết vấn đề ảo hóa network trong các máy vật lý. Về mặt logic Linux Bridge tạo ra một switch ảo để các VM kết nối và có thể nói chuyện được với nhau cũng như sử dụng để ra ngoài mạng.

![huydv](../image/Screenshot_55.png)

Với mô hình này ta có thể dùng dải mạng tương ứng với mỗi card mạng của ta. Ta cũng có thể add thêm 1 twitch ảo và gán cho nó các card mạng tương ứng . Lúc này các VM Kết nối vào switch đó sẽ nhận địa chỉ của card đã kết nối với switch.

### Lệnh tạo một bridge 

* Tạo một Bridge:
`brctl addbr [tên_bridge]`

* Gán port cho bridge :
`brctl addif [tên_bridge] [tên_card]`

* Kiểm tra lại hoạt động của bridge:
`brctl show`

* Ngắt card khỏi bridge:
`brctl delif [tên_tên_bridge] [tên_card]` 

Lưu ý: Với các card mạng có sẵn trên máy hoặc các card mạng được sinh ra trong quá trình cài các phần mềm ảo hóa thì mặc định nó đã được gắn với một switch ảo có cùng tên nên vì vậy muốn kết nối bridge đến các switch đó ta chỉ cần kết nối các máy VM đến nó là được. Thực hiện trên VM ta thực hiện giống với các mô hình trên

![huydv](../image/Screenshot_56.png)
