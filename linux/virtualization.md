# Virtualization



## Qemu

#### Convert ova file to qemu

unpack like zip/tar file:

```sql
tar -xvf "filename.ova"
```

convert to qcow2 format:

```sql
qemu-img convert -f vmdk -O qcow2 "filenameunpacked.vmdk" new.qcow2
```

run:

```sql
qemu-system-x86_64 -enable-kvm -m 2G -hda new.qcow2
```
