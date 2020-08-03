# Tìm hiểu về Navite (bare metal)

Là một máy chủ vật lý chỉ bao gồm phần cứng và dành riêng cho một khách hàng. Thuật ngữ này để phân biệt no svoiws các dạng máy chủ áo hóa trên nền tảng cloud.

Bare_Metal server đơn giản chỉ là một máy chủ đeicate truyền thống, được đặt thêm tên mới do sự xuất hiện của xu hướng điện toán đám mây với các máy chủ ảo...

Mỗi máy chủ logic được cấp cho một người dùng, khách hàng và họ hoàn oàn quyền khai thác phần cứng riêng biệt cho hộ nó không phải là các máy ảo chạy trên phần cứng được chia sẻ chung. Người dùng có thể truy cập trực tiếp và không hạn chế vào máy chủ của họ và có thể truy cập phần cứng chi tiếp ở cấp component so với các máy ảo, nơi mà việc truy cạp vào máy chủ vật lý chỉ được thực hiện thông qua Hypervisor.

Các sản phẩn thế giới dùng cho Navite(Bare metal):
SIMMON(ra đời đầu tiên do IBM phát hành 1960), CP/CMS, Hyper-V, KVM (Red Hat Enterprise Virtualization), LDoms/Oracle VM Server for SPARC, Logical Partition (LPAR), LynxSecure, PikeOS, Proxmox VE, VMware ESXi (VMware vSphere, vCloud), VMware Infrastructure, Xen (Oracle VM Server for x86, XenServer), XtratuMz/VM

Tham khao:
https://thenewstack.io/bare-metal-in-a-cloud-native-world/

## Thuật ngữ

* Network card - Nơi bạn kết nối vật lý máy tính với mạng bằng cáp. Đây có thể là đồng, hoặc trong một số trường hợp là cáp quang. Một máy tính có thể có nhiều Network Card hoặc Port.
* Management Port - đây là một khái niệm dành riêng cho máy chủ. Để đạt hiệu quả, quản trị viên cần quản lý máy tính từ xa mà không cần cắm bàn phím và chuột.
* [Intelligent Platform Management Interface (IPMI)](https://en.wikipedia.org/wiki/Intelligent_Platform_Management_Interface) - Giao diện quản lý có xu hướng dành riêng cho nhà cung cấp và được truy cập qua mạng bằng cách sử dụng máy khách làm giao diện bằng Java
* Wake on Lan(WoL): Thay vì cho phép WoL quản lý từ xa có thể được sử dụng để bật máy tính từ xa.
* iPXE- Một chương trình cơ sở khởi động bằng mã nguồn mở mới hơn cho phép khởi động qua http và Internet
* Netbooting - Khởi động từ network có nghĩa là bạn không cần truy cập vật lý vào máy tính để cấu hình hoặc cài đặt hệ điều hành
* DHCP - Gắn địa chỉ IP và metadata khác như DNS gateway, SubnetMask cho Network Interface.
* TFTP (trivial file transfer): máy chủ dựa trên UDP được sử dụng để tìm nạp chương trình cơ sở để khởi động qua mạng
* NFS (Network File System)- Được sử dụng để chia sẻ tệp trên máy tính Linux hoạt động. NFS không tương thích với các hệ thống tệp overlay sử dụng với containers
* iSCSI (Internet Small Computer Systems Interface) - thay thế cho NFS cung cấp các thiết bị block-devices thay vì một hệ thống tệp tin nối mạng. Bạn có thể định nghĩa theo cách bạn muốn, với hệ thống tệp ext4 và thậm chí chạy docker.
* Thin client
* Operating System: cho dù triển khai Wd, linux, hoặc OS khác. Hệ điều hành thường phải cài đặt bằng UI, CLI hoặc thông qua cấu hình được xác định trước.

Không phải tất cả các bare metal đều như nhau. 