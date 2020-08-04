# Cơ bản về KVM
## KVM là gì?
* KVM (Kernel-based Virtual Machine): Là công nghệ ảo hóa trong nhân Linux cho phép hạt nhân hoạt động như một trình ảo hóa. Do đó máy chủ KVM được cung cấp riêng tài nguyên để sử dụng, tránh việc tranh chấp tài nguyên với máy chủ khác.
* Máy chủ gốc được cài hệ điều hành Linux nhưng KVM hỗ trợ tạo máy chủ ảo có thể chạy Linux, Window. Nó cững hỗ trợ cả X86 và X86-64 System
* KVM cung cấp ảo hóa hỗ trợ phần cứng cho nhiều hệ điều hành khách khác nhau.
* Ảo hóa KVM không có tài nguyên dùng chung, chúng đã được mặc định sẵn và chia sẻ. Như vậy RAM của mỗi KVM được định sẵn, tận dụng 100% và không bị chia sẻ. Điều này sẽ giúp cho chúng hoạt động được ổn định hơn, không bị ảnh hưởng đến các máy ảo khác chung hệ thống. 
## KVM để làm gì?
* KVM giúp sử dụng hệ thống máy chủ -> để tạo ra môi trường máy ảo phục vụ theo mục đích sử dụng
* KVM chuyển đổi một nhân Linux (linux Kernel) thành một Bare metal Hypervisor và thêm vào đó những đặc trưng riêng của của các bộ xử lý Intel VT-X hay ADM-V(ảo hóa của vi xử lý)
* Khi đã trở thành một Hypervisor, KVM hoàn toàn có thể setup các máy ảo với các hệ điều hành khác nhau và không phụ thuộc vào hệ điều hành của máy chủ vật lý.
* Trong KVM, Virtual Machine được thực hiện tương tự như là quy trình xử lý thông thường của Linux, được lập lịch như các Schuler tiêu chuẩn của Linux.
* Mỗi CPU ảo hoạt động hoạt động như một tiến trình xử lý của Linux. KVM được quyền thừa hưởng những ưu điểm từ các tính năng của nhân Linux

## Tính năng của công nghệ KVM

* Tính năng bảo mật: Công nghệ KVM kết hợp với Linux giúp tăng khả năng bảo mật SELinux(xây dựng rang giới bảo mật quanh máy ảo), sVirt: đẩy mạnh khả năng của SElinux, tăng bảo mật kiểm soát truy cập bắt buộc MAC dùng cho máy ảo khách, chống lỗi ghi nhãn thủ công, cách ly VM.
* Lưu trữ: Cho phép người dùng sử dụng các bộ lưu trữ được Linux hỗ trợ như: bộ lưu trữ gắn mạng NAS,.. Chia sẻ tệp để hình ảnh ảo hóa bởi nhiều máy chủ.
* Hỗ trợ phần cứng: Công nghệ KVM cũng có thể sử dụng được nhiều nền tảng phần cứng được Linux hỗ trợ.
* Quản lý bộ nhớ: Thừa hưởng các chức năng quản lý bộ nhớ của Linux, chúng hỗ trợ truy cập bộ nhớ không đồng nhất. Bộ nhớ ảo hóa của KVM có khả năng hoán đổi có hiệu suất tốt, được chia se hoặc sao lưu bởi một tệp đĩa.
* Di chuyển công nghệ ảo hóa KVM trực tiếp: KVM cho phép bạn di chuyển ảo hóa trực tiếp- di chuyển một chương trình ảo hóa đang chạy mà không gây ra sự gián đoạn giữa máy chủ vật lý. KVM vẫn được bật, mọi kết nối mạng và ứng dụng vẫn hoạt động bình thường. Đồng thường trong quá trình di chuyển nó thực hiện cả thao tác lưu trữ.
* Hiệu suất, khả năng mở rộng: Như đã đề cập ở các chức năng trên của ảo hóa KVM, chúng sở hữu ưu điểm của Linux, chúng sẽ có khả năng mở rộng giúp phù hợp để đáp ứng như cầu khi máy khách và yêu cầu truy cập tăng lên nhiều lần. Công nghệ KVM cho phép khối lượng công việc ứng dụng yêu cầu khắt nhất được ảo hóa và là cơ sở cho nhiều thiết lập ảo hóa doanh nghiệp, Ví dụ trung tâm dữ liệu, ảo hóa VPS và nghẹ đám mây riêng.

* Độ trễ thấp hơn: Linux có các phần cho phép mở rộng thời gian thực tế để các ứng dụng dựa trên KVM chạy trong một độ trễ  thấp hơn với mức độ ưu tiên tốt hơn. và chúng cũng tiến hành phân chia các quá trình yêu cầu một khoảng thời gian dài tính toán thành các khoảng nhở hơn, rồi sau đó lên lịch để xử lý tương ứng
* Quản lý với KVM: Thông qua KVM cho cho phép quản lý thủ công chương trình ảo hóa được kích hoạt từ máy trạm, không cần qua công cụ quản lý. Chức năng này thường được sử dụng bởi các doanh nghiệp lớn để quản trị nguồn tài nguyên, tăng khả năng phân tích dữ liệu, hợp lý các hoạt động.