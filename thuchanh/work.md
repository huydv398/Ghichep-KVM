# Các tính năng của KVM đối với KVM
## Thêm VM
để thêm 1 VM ta thực hiện câu lệnh sau:

`virt-install --name=VM1 --vcpus=1 --memory=1024 --cdrom=/var/lib/libvirt/file-iso/CentOS-7-x86_64-Minimal-1804.iso --disk=/var/lib/libvirt/images/vm1.img,size=10 --os-variant=rhel7 --graphics vnc --network bridge=br0`

thực hiện câu lệnh để Begin setup:

`virt-manager`
## Sửa VM

`virsh edit [name VM]`

## Xóa VM

Sử dụng câu lệnh:

`virsh underfine [tên vm]`
## Clone
Để clone 1 VM ra thực hiện các bước sau:

```
[root@kvm images]# virsh list
 Id    Name                           State
----------------------------------------------------
 3     VM1                            running

```
Show số lượng và vị trí Disk mà máy ảo nguồn sử dụng:
```
[root@kvm images]# virsh dumpxml VM1 | grep "source file"
      <source file='/var/lib/libvirt/images/vm1.qcow2'/>
```

Tạm dừng máy ảo
```
[root@kvm images]# virsh suspend VM1
Domain VM1 suspended

```

### Auto-clone VIrtual Machine- tự động sao chép
Một cách để sao chép Máy ảo dựa trên KVM: `--auto-clone`
* Ưu điểm: tự động sao chép bất kỳ số lượng đĩa nguồn nào, người dùng không cần biết số lượng và vị trí đĩa được gắn vào máy ảo.
* Nhược điểm: người dùng không thể chỉ định tên đĩa và chủ động một vị trí thay thế cho các đĩa ảo mới nhân bản

```
[root@kvm images]# virt-clone --original=VM1 --name=VM1.clone --auto-clone
WARNING  Setting the graphics device port to autoport, in order to avoid conflicting.
Allocating 'vm1-clone.qcow2'                               |  10 GB  00:10

Clone 'VM1.clone' created successfully.
```

Thay đổi tên mới ảo và tên bản Clone muốn tạo 


### CLone thủ công nhiều disk
Để kiểm soát vị trí disk tốt hơn với vị trí và tên disk được sao chép mới, chúng ta có thể bỏ qua `--auto-clone` và cung cấp tên đĩa và đường dẫn đích được nhân bản mới bằng cách sử dụng `--file`

`virt-clone --original=name_VM --name=name_VM_clone --file /var/lib/libvirt/images/VM1.qcow2 --file /var/lib/libvirt/images/VM1-1.qcow2 --file /var/lib/libvirt/images/VM1-2.qcow2`

Tiếp tục chạy máy ảo ban đầu

```
[root@kvm images]# virsh resume VM1
Domain VM1 resumed
```

Bắt đầu chạy mới bản clone

```

```

## Snapshot
* Tạo Snapshot

`virsh snapshot-create-as --domain VM1 --name Begin --description "mo ta"`

* Xem danh sách các bản snapshot trên 1 VM:

`virsh snapshot-list [name_vm]`

* Xem thông tin chi tiết của bản Snapshot

`virsh snapshot-info --domain [tên máy ảo] --snapshotname [tên bản snapshot]`

* revert để chạy lại một bản snapshot đã tạo:

`virsh snapshot-revert [Name_VM] [Name_Snapshot]`