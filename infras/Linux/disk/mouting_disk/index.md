# MOUNTING

Khi một hệ thống tập tin (file system) mount vào Linux thành công, dữ liệu trên đó sẽ sắn sàng được truy cập tại *mount point*.

Cú pháp:

```
mount <partition> <directory_path>
```

Ví dụ:

```
mount /dev/sdb /mnt/datab
```

Lệnh này sử dụng để mount partition `sdb` đến thư mục hay mount point `/mnt/datab`.

Để unmount phân vùng, ta thực hiện:

```
unmount /dev/sdb /mnt/datab
```

Để kiểm tra file system có được mount hay chưa, ta có thể dùng lệnh `lsblk` hoặc `df -h`.

Một khi file system được mount, bạn có thể di chuyển đến mount point đó như một thư mục để đọc, ghi và xóa dữ liệu trong thư mục đó. Ví dụ:

- Ghi dữ liệu

```
echo "flag{Thoi_dai_moi_da_den}" > /mnt/datab/flag.txt
```

- Đọc dữ liệu:

```
cat /mnt/datab/flag.txt
```

- Xóa dữ liệu:

```
rm /mnt/datab/flag.txts
```
