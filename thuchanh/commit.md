# Sử dụng Blockcommit và Pullcommit

 virsh blockcommit newvm2 /var/lib/libvirt/images/newvm2.qcow2 -base snapshot2 -top snapshot3 -wait -verbose

virsh snapshot-info --domain newvm2 --snapshotname snapshot3

virsh snapshot-create-as –domain newvm2 centos-state01 –diskspec vda, file = /root/overlay.qcow2 –disk-only –atomic