# LUỒNG DỮ LIỆU (DATA FLOW)

## Địa chỉ MAC (MAC Address)

Là một giá trị địa chỉ **duy nhất** được đăng ký trên NIC (Network Interface Card) hay Network Adapter. Giá trị này có độ dài 48 bit, với 24 bit đầu sẽ là định danh nơi sản xuất, trong khi đó 24 bit còn lại có vai trò định danh.

## Carrier-Sense Multiple Access / Colision Detection (CSMA/CD)

## Broadcast domain, Collision domain

Miền quảng bá (Broadcast domain) : hiểu đởn giản là miền thực hiện gửi broadcast, có thể nằm trong cùng một vùng phân mạng LAN.

Miền xung đột (Collision domain): là miền kết nối giữa 2 thiết bị L2 (Switch, Bridge) với nhau.

## Half dumplex, Full dumplex

Half dumplex chỉ có một kết nối mỗi lượt, không cùng một lúc. Hub sử dụng half dumplex.

Full dumplex cho phép cả hai cùng lúc gửi và nhận dữ liệu. Switch có thể sử dụng full dumplex và cả half dumplex. Lưu ý rằng khi sử dụng full dumplex thì CD sẽ bị vô hiệu và chỉ có CSMA được sử dụng.

## Routing

[Routing](../4_4_Routing/index.md) là quá trình chọn ra hướng đi phù hợp cho gói tin để đến được đích đến.
