# MPLS example

![Topology](./img/topology.png)

Thực hiện cấu hình MPLS để cho luồng mạng di chuyển từ PC 3 đến PC1 theo đường dẫn đã chỉ định.

## BƯỚC CẤU HÌNH

### GÁN ĐỊA CHỈ IP

|Machine|Interface|IP address|Netmask|Gateway|
|:------|:--------|:---------|:------|:------|
|PC 1|Fa0|192.168.1.10|255.255.255.0|192.168.1.254|
|PC 2|Fa0|192.168.2.10|255.255.255.0|192.168.2.254|
|PC 3|Fa0|192.168.3.10|255.255.255.0|192.168.3.254|
|PC 4|Fa0|192.168.4.10|255.255.255.0|192.168.4.254|
|G1|g0/0|192.168.1.254|255.255.255.0|N/A|
|G1|g0/1|13.13.13.6|255.255.255.248|N/A|
|G1|g0/2|192.168.2.254|255.255.255.0|N/A|
|R1|g0/0|13.13.13.5|255.255.255.248|N/A|
|R1|g0/1|13.13.13.22|255.255.255.248|N/A|
|R1|g0/2|13.13.13.14|255.255.255.248|N/A|
|R2|g0/0|13.13.13.21|255.255.255.248|N/A|
|R2|g0/1|13.13.13.30|255.255.255.248|N/A|
|R2|g0/2|13.13.13.54|255.255.255.248|N/A|
|R3|g0/0|13.13.13.62|255.255.255.248|N/A|
|R3|g0/1|13.13.13.53|255.255.255.248|N/A|
|R3|g0/2|13.13.13.38|255.255.255.248|N/A|
|R4|g0/0|13.13.13.13|255.255.255.248|N/A|
|R4|g0/1|13.13.13.29|255.255.255.248|N/A|
|R4|g0/2|13.13.13.37|255.255.255.248|N/A|
|G2|g0/0|192.168.3.254|255.255.255.0|N/A|
|G2|g0/1|13.13.13.61|255.255.255.248|N/A|
|G2|g0/2|192.168.4.254|255.255.255.0|N/A|

### CẤU HÌNH OSPF ROUTING

Thực hiện cấu hình OSPF routing, tham khảo tại [đây](../OSPF_routing/index.md), sử dụng OSPF id là 1 và area là 0.

### CẤU HÌNH MPLS

Cấu hình chuyển mạch MPLS trên Cisco router yêu cầu Cisco Express Forwarding (CEF) được bật [[1]](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/mp_basic/configuration/xe-16/mp-basic-xe-16-book/multiprotocol-label-switching-mpls-on-cisco-routers.html) [[4]](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/15-s/isw-cef-15-s-book/isw-cef-enable-disable.html#GUID-405A8371-43FF-40F2-8559-D5E43F3E25F7):

```
enable
configure terminal
ip cef
```

Để kiểm tra CEF có được cấu hình đúng cách hay không sử dụng lệnh 

```
show ip cef summary
```

Thực hiện cấu hình MPLS cho các router kết nối trực tiếp với nhau [[3]](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/mp_ldp/configuration/xe-16/mp-ldp-xe-16-book/mp-ldp.html). Lưu ý rằng interface kết nối trực tiếp vào vùng mạng của các host sẽ không cần cấu hình MPLS.

- Tại G1:

```
enable
configure terminal
interface gi0/1
mpls ip
exit
```

- Tại R1:

```
en
conf ter
interface gi0/0
mpls ip
exit
interface gi0/1
mpls ip
exit
```

- Tại R2:

```
en
conf ter
interface gi0/0
mpls ip
exit
interface gi0/1
mpls ip
exit
```

- Tại R4:

```
en
conf ter
interface gi0/1
mpls ip
exit
interface gi0/2
mpls ip
exit
```

- Tại R3:

```
en
conf ter
interface gi0/0
mpls ip
exit
interface gi0/2
mpls ip
exit
```

- Tại G2:

```
en
conf ter
interface gi0/1
mpls ip
```

### KIỂM TRA

...

## REFERENCE

[1] <https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/mp_basic/configuration/xe-16/mp-basic-xe-16-book/multiprotocol-label-switching-mpls-on-cisco-routers.html>

[2] <https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/mp_ldp/configuration/xe-16/mp-ldp-xe-16-book.html>

[3] <https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/mp_ldp/configuration/xe-16/mp-ldp-xe-16-book/mp-ldp.html>

[4] <https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipswitch_cef/configuration/15-s/isw-cef-15-s-book/isw-cef-enable-disable.html#GUID-405A8371-43FF-40F2-8559-D5E43F3E25F7>
