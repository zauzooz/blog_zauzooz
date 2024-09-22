# CÁC LỆNH ĐỂ LIST DISK

## 1. `lsblk`

Liệt kê các thiết bị block (bao gồm ổ đĩa hoặc phân vùng)

```
zauzooz@zauzooz:~$ lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
fd0                         2:0    1  1.4M  0 disk
loop0                       7:0    0   64M  1 loop /snap/core20/2318
loop1                       7:1    0   64M  1 loop /snap/core20/2379
loop2                       7:2    0 91.9M  1 loop /snap/lxd/24061
loop3                       7:3    0 91.9M  1 loop /snap/lxd/29619
loop4                       7:4    0 38.8M  1 loop /snap/snapd/21759
loop5                       7:5    0 49.9M  1 loop /snap/snapd/18357
sda                         8:0    0   25G  0 disk
├─sda1                      8:1    0    1M  0 part
├─sda2                      8:2    0    2G  0 part /boot
└─sda3                      8:3    0   23G  0 part
  └─ubuntu--vg-ubuntu--lv 253:0    0 11.5G  0 lvm  /
sr0                        11:0    1 99.4M  0 rom
sr1                        11:1    1 1024M  0 rom
```

## 2. `sudo fdisk -l`

Lệnh này cho phép quản lý các phân vùng đĩa. Sử dụng tùy chọn -l để liệt kê các ổ đĩa và phân vùng.

```
zauzooz@zauzooz:~$ sudo fdisk -l
[sudo] password for zauzooz:
Disk /dev/loop0: 63.97 MiB, 67051520 bytes, 130960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 63.10 MiB, 67080192 bytes, 131016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 91.85 MiB, 96292864 bytes, 188072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 91.9 MiB, 96346112 bytes, 188176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 38.85 MiB, 40714240 bytes, 79520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 49.86 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/fd0: 1.42 MiB, 1474560 bytes, 2880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x90909090

Device     Boot      Start        End    Sectors  Size Id Type
/dev/fd0p1      2425393296 4850786591 2425393296  1.1T 90 unknown
/dev/fd0p2      2425393296 4850786591 2425393296  1.1T 90 unknown
/dev/fd0p3      2425393296 4850786591 2425393296  1.1T 90 unknown
/dev/fd0p4      2425393296 4850786591 2425393296  1.1T 90 unknown




Disk /dev/sda: 25 GiB, 26843545600 bytes, 52428800 sectors
Disk model: VMware Virtual S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 18A3B380-756A-4071-A273-CF89CB0171A7

Device       Start      End  Sectors Size Type
/dev/sda1     2048     4095     2048   1M BIOS boot
/dev/sda2     4096  4198399  4194304   2G Linux filesystem
/dev/sda3  4198400 52426751 48228352  23G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 11.51 GiB, 12343836672 bytes, 24109056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

## 3. `sudo parted -l`

Lệnh này để quản lý phân vùng, có thể được sử dụng để liệt kê các ổ đĩa.

```
zauzooz@zauzooz:~$ sudo parted -l
Model: VMware, VMware Virtual S (scsi)
Disk /dev/sda: 26.8GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  2150MB  2147MB  ext4
 3      2150MB  26.8GB  24.7GB


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 12.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system  Flags
 1      0.00B  12.3GB  12.3GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: NECVMWar VMware SATA CD00 (scsi)
Disk /dev/sr0: 104MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:
```

## 4. `df -h`

`df` là viết tắt của Disk Free. Lệnh này chủ yếu dùng để xem dung lượng ổ đĩa còn trống, nhưng cũng liệt kê các thiết bị lưu trữ đang được mount.

```
zauzooz@zauzooz:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               421M     0  421M   0% /dev
tmpfs                               94M  1.3M   93M   2% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   12G   11G  426M  97% /
tmpfs                              467M     0  467M   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              467M     0  467M   0% /sys/fs/cgroup
/dev/loop0                          64M   64M     0 100% /snap/core20/2318
/dev/loop2                          92M   92M     0 100% /snap/lxd/24061
/dev/loop1                          64M   64M     0 100% /snap/core20/2379
/dev/sda2                          2.0G  211M  1.6G  12% /boot
/dev/loop3                          92M   92M     0 100% /snap/lxd/29619
/dev/loop4                          39M   39M     0 100% /snap/snapd/21759
/dev/loop5                          50M   50M     0 100% /snap/snapd/18357
tmpfs                               94M     0   94M   0% /run/user/1000
```

## 5. `ls /dev/*`

Bạn có thể liệt kê các thiết bị lưu trữ bằng cách kiểm tra thư mục `/dev/` với các tên thiết bị như `sd*`, `nvme*`, `vd*`.

```
zauzooz@zauzooz:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3
```
