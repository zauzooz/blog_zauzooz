# TĂNG DUNG LƯỢNG Ổ ĐĨA TỪ Ổ ĐĨA TRỐNG

## TÓM TẮT

```
# Step 1: Prepare the New Disk
sudo pvcreate /dev/sdb
sudo pvs

# Step 2: Extend the Volume Group
sudo vgextend ubuntu-vg /dev/sdb
sudo vgs

# Step 3: Extend the Logical Volume
sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv

# Verify
df -h
sudo lvs

```
