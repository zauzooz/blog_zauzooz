# Điều gì sẽ xảy ra nếu xóa 1 vlan trên VTP server switch

Cho mô hình mạng bên dưới

![example model](./img/image.png)

Cấu hình các địa chỉ cho các máy có địa chỉ X.Y.10.Z (PC0, PC 3 và PC 6) sẽ thuộc VLAN 10, X.Y.20.Z (PC 1, PC 4 và PC 7) thuộc VLAN 20 và X.Y.30.Z (PC 2, PC 5 và PC 8) thuộc VLAN 30.

Cấu hình VTP có domain name là IT.

## Giả sử xóa VLAN 30 để thí nghiệm

Trong trường hợp VLAN 30 chưa xóa, PC 2 ping thành công đến PC 5 và PC 8.

![PC 2 ping vào PC 5 và PC 8](./img/image1.png)

Sau khi xóa VLAN 30, PC 2 không còn ping đến PC 5 và PC 8 nữa.

![Alt text](./img/image2.png)

Kiểm tra VLAN trên VTP client switch 1, như đã thấy VLAN 30 đã biến mất.

![Alt text](./img/image3.png)

## Khôi phục lại VLAN 30 sau khi đã xóa

## Tạo VLAN 40 thay vì VLAN 30 sau khi đã xóa
