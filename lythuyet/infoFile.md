# Các file của VM trên KVM
Sau đây là tìm hiểu của mình về các cấu trúc file cấu hình mặc định của VM trên KVM

Ở đây mình sẽ giới thiệu 2 nhánh chính của thư mục:
* **/var/lib/libvirt**
* **/etc.libvirt/qume**
## Thư mục chứa các disk của VM
`/var/lib/libvirt/images/`

107

![huydv](../image/Screenshot_107.png)
## Thư mục chứa file `.xml` thông số kỹ thuật của VM

`/etc/libvirt/qemu/`

![huydv](../image/Screenshot_108.png)

tại file xml của VM có thể thay đổi một số thông số phần cứng như:

Virtual RAM, vcpus:

![huydv](../image/Screenshot_109.png)

Thay đổi đường dẫn cho file Image:

![huydv](../image/Screenshot_110.png)

## Thư mục chứa các file liên quan đến network

`/etc/libvirt/qemu/networks/`

![huydv](../image/Screenshot_111.png)

## Thư mục chứa các file Image
`/var/lib/libvirt/images/`

![huydv](../image/Screenshot_112.png)

## Thư mục chứa các bản snapshot
`/var/lib/libvirt/qemu/snapshot/`

![huydv](../image/Screenshot_113.png)