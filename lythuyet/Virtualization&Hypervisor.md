# Note Overview Virtualization và Hypervisor

1. [Virtualization là gì?](#1)
2. [Tại sao lên sử dụng công nghệ ảo hóa](#whyuse)
3. [Hypervisor là gì?](#Hypervisor)
4. [Vitual Machine là gì?](#Machine)
5. [Hypervisor/VMM là gì?](#Hypervisor)

[Hypervisor hoạt động như thế nào](Hypervisor-active.md)
 [**Loại 1**: Native](#Native)

 [**Loại 2**: Hosted](#Hosted)

6. [Các thành phần của một hệ thống ảo hóa](#element)
7. [Ảo hóa hoạt động như thế nào?](#active)
8. [Mục Tiêu của Ảo hóa](#target)
9. [Lợi ích và nhược điểm của Ảo hóa](#loiich)

<a name="Virtualization"></a>

### Virtualization là gì?
Virtualization, hay còn gọi là ảo hóa, là một công nghệ thiết kế ***để tạo ra phần trung gian giữa hệ thống và phần cứng máy tính và phần mềm chạy trên nó***. Ý tưởng của công nghệ ảo hóa máy chủ là **từ một máy vật lý** đơn giản **tạo** ra **nhiều máy ảo** độc lập. **Mỗi máy ảo** đều có **thiết lập** nguồn h**ệ thống riêng biệt**,**hệ điều hành riêng và ứng ụng riêng**. Ảo hóa có nguồn gốc từ việc phân chia ổ đĩa, chúng chia một máy chủ thực thành nhiều máy chủ logic. Một khi máy chủ thực được chia, mỗi máy chủ logic có thể chạy một hệ điều hành và các ứng dụng độc lập.

>**Ý nghĩa**: ẢO HÓA LÀ PHƯƠNG PHÁP ĐỂ TẠO RA PHIÊN BẢN ẢO HÓA TRÊN MÁY TÍNH VẬT LÝ.

<a name="whyuse"></a>
### Tại sao lên sử dụng công nghệ ảo hóa

Tiết kiệm chi phí và tối ưu hóa hạ tầng CNTT là điều các doanh nghiệp quan tâm, đặc biệt là các doanh nghiệp có nhiều chi nhánh trên cả nước hay toàn cầu. Ảo hóa giúp doanh nghiệp nâng cao năng lực bảo mật dữ liệu, tăng cường khả năng khôi phục sau thảm họa, nâng cao tính linh hoạt và cắt giảm chi phí đầu tư cho CNTT như phải cập nhật liên tục phần mềm, các tính năng mới... trên nhiều máy vật lý.

<a name="Hypervisor"></a>
### Hypervisor/VMM(Virtual Machine Monitor) là gì?

**Hypervisor** hay còn gọi là phần mềm giám sát máy ảo: ***là một chương trình phần mềm quản lý môt hoặc nhiều máy ảo VM***. Nó được sử dụng để **tạo**, **Startup**, **Suspend** và **reset** lại các **máy ảo**. Các Hypervisor cho phép mỗi VM hoặc "Guest" truy cập vào phần cứng vật lý bên dưới, Chẳng hạn như CPU, RAM, Disk. Nó cũng có thể giới hạn tài nguyên hệ thống mà mỗi máy ảo có thể dụng để đảm bỏa  cho nhiều máy ảo cùng sử dụng đồng thời trên một hệ thống.
>**Ý nghĩa**: Hypervisor là các phần mềm công nghệ để tạo máy ảo và giám sát, điều khiển máy ảo. Muốn Ảo Hóa thì cài Hypervisor nào đó.

<a name="Native"></a>
### Loại 1: **Native**

Một Hypervisor ở dạng native (hay còn gọi là "bare-metal") **chạy trực tiếp trên phần cứng**. nó nằm giữa phần cứng và một hệ điều hành khách (Guest Operating System). Nó được khởi động trước hệ điều hành và tương tác trực tiếp với kernel. Điều này mang lại **hiệu suất cao nhất** có thể vì *không có hệ điều hành chính* nào *cạnh tranh tài nguyên máy tính* với nó. Tuy nhiên, nó có thể đồng nghĩa với việc hệ thống chỉ có thể sử dụng để chạy các máy ảo vì Hypervisor luôn phải chạy ngầm bên dưới.

Các Hypervisor dạng Native này có hteer kể như VMware ESXi, Microsoft Hyper-V và Apple boot Camp.

![huydv](../image/Screenshot_1.png)


<a name="Hosted"></a>
### Loại 2: **Hosted**

Một Hypervisor dạng Hosted được **cài đặt trên một máy tính** chủ (host computer)
, mà trong đó *có một hệ điều hành đã được cài đặt*. Nó **chạy như một ứng dụng** cũng như các phần mềm khác trên máy tính. Hầu hết các Hypervisor dạng hosted **có thể quản lý và chạy nhiều máy ảo cùng một lúc**. Lợi thế của một Hypervisor hosted là có thể được bật lên hoặc thoát ra khi cần thiết, giải phóng tài nguyên cho máy chủ. Tuy nhiên, vì chạy trên một hệ điều hành, nó có thể đem lại hiệu suất tương tự như một Hypervisor ở dạng Native.

Ví dụ về các Hypervisor dạng hosted bao gồm VMwaware Workstation, Oracle VirtualBox và Parallels Desktop for Mac.

![huydv](../image/Screenshot_2.png)


Khác biệt giữa 2 loại là:
* Native: được cài đặt làm OS trực tiếp để tạo VM
* Hosted: Hypervisor được cài sau một hệ điều hành làm nền. Đứng giữa OS và VM

<a name="Machine"></a>
### Vitual Machine là gì?
Virtual Machine-VM hay còn gọi là máy ảo, là một môi trường hoạt động độc lập - phần mềm hoạt động cùng nhưng độc lập với hệ điều hành máy chủ

<a name="element"></a>
## Các thành phần của một hệ thống ảo hóa

* **Tài nguyên vật lý** chính: Máy chủ vật lý, CPU, RAM, Ổ đĩa cứng, Card mạng.. Nhiệm vụ là chia tài nguyên cấp cho các máy ảo.
* **Phần mềm ảo hóa**(Hypervisor): Cung cấp truy cập cho mỗi máy chủ ảo đến tài nguyên của máy chủ vật lý, Lập kế hoạch phân chia tài nguyên của máy chủ vật lý cho các máy chủ ảo.
* H**ệ điều hành Khách**(Guest Operating System): được cài đặt trên một máy chủ ảo, thao tác như ở trên hệ điều hành thông thường.
* **Máy ảo**(Virtual machine): Nó hoạt động như một máy chủ vật lý thông thường với tài nguyên riêng, giao diện riêng, hệ điều hành riêng.

Một **hệ thống ảo hóa bắt buộc** phải có đầy đủ các thành phần: **tài nguyên vật lý**, phần mềm ảo hóa, máy chủ ảo và hệ điều hành khách. Khi có đầy đủ 4 thành phần của hệ thống ảo hóa, máy chủ ảo và hệ điều hành khách. Khi có đầy đủ 4 thành phần của hệ thống ảo hóa, người dùng có thể dễ dàng xây dựng cho mình một hệ thống ứng dụng ảo hóa hoàn chỉnh

<a name="active"></a>
## Ảo hóa hoạt động như thế nào?

Ảo hóa được xây dựng dựa trên giải pháp chia 1 máy vật lý thành nhiều máy VM. Virtual Machine Monitor (VMM) hay còn được gọi là Hypervisor -  Cho phép tạo tách rời các máy ảo và điều phối truy cập của các máy ảo này đến tài nguyên phần cứng và cấp phát tài nguyên tự động theo nhu cầu sử dụng.
* Nhiều ứng dụng chạy trên 1 server, mỗi VM được lập trình trên máy chủ, do đó nhiều ứng dụng và các hệ điều hành có thể cùng lúc chạy trên host.
* Tối đa hóa công suất sử dụng và tối thiểu hóa server: mỗi máy chủ vật lý Được sử dụng với đầy đủ công suất, cho phép giảm đáng kể chi phí nhờ sử dụng tối đa server.
* Cấp phát tài nguyên và ứng dụng nhanh chóng, dễ dàng. VM được triển khai từ một file chứa đầy đủ phần mềm với cơ chế đơn giản là copy và mang điều này đến sự giản đơn, nhanh chóng và linh hoạt chưa từng có cho việc quản lý và cung cấp hạ tầng công nghệ thông tin. Máy ảo thậm chí có thể di chuyển sang một server vật lý khác trong khi vẫn đang chạy, Hoạt động bình thường. Doanh nghiệp có thể ảo hóa những ứng dụng quan trọng của doanh nghiệp để nâng cao hiệu suất, sự ổn định, khả năng mở rộng và giảm thiểu chi phí.

<a name="target"></a>
## Mục Tiêu của Ảo hóa
Ảo hóa xoay quanh 4 mục tiêu chính: Availability, Scalability, Optimization, Management.

* **Availability**(tính khả dụng): Giúp các ứng dụng hoạt động liên tục bằng cách giảm thiểu(bỏ qua) thời gian chết (Downtime) khi phần cứng gặp sự cố, khi nâng cấp hoạt di chuyển.
* **Scalability**(Khả năng mở rộng): Khả năng tùy biến thu hẹp hay mở rộng mô hình server dễ dàng mà không làm gián đoạn ứng dụng.
* **Optimization**(Tối ưu hóa): Sử dụng triệt để nguồn tài nguyên phần cứng và tránh lãng phí bằng cách giảm số lượng thiết bị vật lý cần thiết(giảm số lượng server, switch, cáp,...)
* **Management**(sự quản lý): khả năng quản lý tập trung, giúp việc quản lý trở nên dễ dàng hơn bao giờ hết

<a name="loiich"></a>
## Lợi ích và nhược điểm của ảo hóa

* Lợi ích của ảo hóa: Ảo hóa trở thành xu hướng của toàn cầu. Những khó khăn, khủng hoảng bắt buộc các doanh nghiệp phải giảm thiểu chi phí. Ảo hóa được coi là một công nghệ giúp các doanh nghiệp cắt giảm chi phí hiệu quả với khả năng tận dụng tối đa năng suất của các thiết bị phần cứng. Việc áp dụng công nghệ ảo hóa máy chủ đem lại những lợi ích như:
    * Tiết kiệm năng lượng tiêu thụ, giảm chi phí duy trì server(tiền điện để chạy và làm mát server)
    * Giảm số lượng thiết bị vật lý cần thiết( giảm số lượng server, switch, cáp, phí gia công)
    * Tận dụng tối đa nguồn tài nguyên trách lãng phí.
    * khả năng mở rộng dễ dàng.
* Nhược điểm:
    * Thông thường mỗi máy ảo chỉ sử dụng một file VMDK (File này có thể chia nhỏ theo cách cài đặt) để lưu lại toàn bộ dữ liệu trong máy ảo và một số file nhỏ khác để lưu cấu hình máy ảo. Do đó, nếu một trong số những tệp tin bị lỗi hoặc mất mà chưa được backup thì có thể xem như máy ảo đã bị hư hoàn toàn và không thể phục hồi.
    * Ngoài ra  nếu máy chủ có cấu hình phần cứng thấp nhưng lại có một máy ảo sử dụng quá nhiều tài nguyên hoặc chạy quá nhiều máy ảo sẽ làm chậm toàn bộ hệ thống bao gồm các máy ảo và các ứng dụng chạy trên máy ảo. Đồng thời, do một hoặc vài máy chủ gặp trục trặc, sự cố thì các máy ảo cũng sẽ bị ảnh hưởng theo.
    * Còn ở góc độ bảo mật, nếu hacker có thể kiểm soát một máy chủ vật lý chứa các máy ảo thì hacker có thể kiểm soát được tất cả các máy ảo trong đó.




Link tham khảo:
https://news.cloud365.vn/kvm-tong-quan-ve-virtualization-va-hypervisor/

https://www.thegioimaychu.vn/blog/ao-hoa/huong-dan-tong-quan-ve-ao-hoa-vmware-p3588/
