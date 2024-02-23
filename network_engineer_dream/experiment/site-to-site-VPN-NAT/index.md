# CẤU HÌNH SITE-TO-SITE VPN

![topology](./img/topology.png)

Thực hiện cấu hình để mạng ở `ANOTHER SITE` và `MAIN SITE` kết nối với nhau thông qua kết nối VPN.

## CÁC BƯỚC CẤU HÌNH

### CẤU HÌNH CÁC KẾT NỐI

**Bảng các địa chỉ IP**:

Tại `MAIN SITE`:

|Machine|Interface|IP address|Netmask|Gateway|
|:------|:--------|:---------|:------|:------|
|Gateway 1|fa0/0|12.12.12.6|255.255.255.0|#|
|Gateway 1|fa0/1|10.0.1.1|255.255.255.0|#|
|Gateway 1|fa0/1.10|10.0.10.1|255.255.255.0|#|
|Gateway 1|fa0/1.20|10.0.20.1|255.255.255.0|#|
|Gateway 2|fa0/1.100|10.0.100.1|255.255.255.0|#|
|Core 1|VLAN 10|10.0.10.2|255.255.255.0|#|
|Core 1|VLAN 20|10.0.20.2|255.255.255.0|#|
|Core 1|VLAN 100|10.0.100.5|255.255.255.0|#|
|SERVER|Fa0|10.0.100.15|255.255.255.0|10.0.100.1|

Tại `ANOTHER SITE`:

|Machine|Interface|IP address|Netmask|Gateway|
|:------|:--------|:---------|:------|:------|
|Gateway 2|fa0/0|14.14.14.6|255.255.255.0|#|
|Gateway 2|fa0/1|10.0.10.1|255.255.255.0||

Tại `INTERNET`:

|Machine|Interface|IP address|Netmask|Gateway|
|:------|:--------|:---------|:------|:------|
|INTERNET|gi1/0/1|12.12.12.5|255.255.255.0|#|
|INTERNET|gi1/0/2|14.14.14.5|255.255.255.0|#|
|INTERNET|gi1/0/3|15.15.15.5|255.255.255.0|#|

Tại *CISCO* Server:

|Machine|Interface|IP address|Netmask|Gateway|
|:------|:--------|:---------|:------|:------|
|CISCO|Fa0|15.15.15.15|255.255.255.0|15.15.15.6|

#### CẤU HÌNH TẠI `INTERNET` và *CISCO* SERVER

**Cấu hình INTERNET**:

- Tạo các VLAN:

```
en
conf ter
interface gi1/0/1
no switchport
ip address 12.12.12.5 255.255.255.0
no shut
interface gi1/0/2
no switchport
ip address 14.14.14.5 255.255.255.0
no shut
interface gi1/0/3
no switchport
ip address 15.15.15.5 255.255.255.0
no shut
```

- Bật tính năng routing cho `INTERNET`:

```
ip routing
```

#### CẤU HÌNH TẠI `MAIN SITE`

**Cấu hình tại *Gateway 1***:

- Cấu hình địa chỉ IP:

```
en
conf ter
interface fa0/0
ip address 12.12.12.6 255.255.255.0
no shut
exit
interface fa0/1
ip address 10.0.1.1 255.255.255.0
no shut
exit
interface fa0/1.10
encapsulation dot1q 10
ip address 10.0.10.1 255.255.255.0
exit
interface fa0/1.20
encapsulation dot1q 20
ip address 10.0.20.1 255.255.255.0
exit
```

- Cấu hình default-route đi ra ngoài Internet:

```
ip 0.0.0.0 0.0.0.0 fa0/0
```

- Cấu hình PAT (Port Addresss Translation):

```
# XÁC ĐỊNH INTERFACE INSIDE VÀ OUTSIDE
interface fa0/0
ip nat outside
exit
interface fa0/1
ip nat inside
exit
interface fa0/1.10
ip nat inside
exit
interface fa0/1.20
ip nat inside
exit
interface fa0/1.100
ip nat inside

# TẠO NAT-POOL CÁC IP ĐỂ DỊCH
ip nat pool NAT_POOL 12.12.12.5 12.12.12.5 netmask 255.255.255.0

# TẠO ACCESS-LIST CÁC ĐỊA CHỈ IP CẦN DỊCH
access-list 1 permit 10.0.1.0 0.0.0.255
access-list 1 permit 10.0.10.0 0.0.0.255
access-list 1 permit 10.0.20.0 0.0.0.255
access-list 1 permit 10.0.100.0 0.0.0.255

# ÁP DỤNG NAT DỰA TEO ACCESS-LIST VÀ NAT-POOL ĐÃ TẠO
ip nat inside source list 1 pool NAT_POOL overload
```

- Lưu cấu hình:

```
wr
copy running-config startup-config
```

**Cấu hình *Core 1***:

- Tạo các VLAN:

```
en
conf ter
vlan 10
vlan 20
vlan 100
```

- Cấu hình IP cho các VLAN:

```
interface vlan 10
ip address 10.0.10.2 255.255.255.0
ip helper-address 10.0.100.15
exit
interface vlan 20
ip address 10.0.20.2 255.255.255.0
ip helper-address 10.0.100.15
exit
interface vlan 100
ip address 10.0.100.2 255.255.255.0
ip helper-address 10.0.100.15
exit
```

- Bật tính năng định tuyến:

```
ip routing
```

- Cấu hình cổng trunk cho các cổng kết nối với *Gateway 1* và *Access 1*:

```
interface range gi1/0/1-2
switchport mode trunk
```

- Lưu cấu hình:

```
wr
copy running-config startup-config
```

**Cấu hình *Access 1***:

- Tạo các VLAN:

```
en
conf ter
vlan 10
vlan 20
vlan 100
```

- Gán các VLAN cho các access port tương ứng:

```
interface fa0/22
switchport mode access
switchport access vlan 100
exit
interface fa0/23
switchoport mode access
switchport access vlan 10
interface fa0/24
switchport mode access
switchport access vlan 20
```

#### CẤU HÌNH TẠI `ANOTHER SITE`

**Cấu hình *Gateway 2***:

- Cấu hình địa chỉ IP:

```
en
conf ter
interface fa0/0
ip address 14.14.14.6 255.255.255.0
no shut
exit
interface fa0/1
ip address 10.0.10.1 255.255.255.0
exit
```

- Cấu hình default route:

```
ip route 0.0.0.0 0.0.0.0 fa0/0
```

- Cấu hình PAT để các máy giao tiếp ra Internet với địa chỉ 14.14.14.5:

```
# XÁC ĐỊNH INTERFACE INSIDE VÀ OUTSIDE
interface fa0/0
ip nat outside
exit
interface fa0/1
ip nat inside

# TẠO NAT-POOL CÁC ĐỊA CHỈ IP CÓ THỂ DỊCH
ip nat pool 14.14.14.6 14.14.14.6 netmask 255.255.255.0

# TẠO ACCESS-LIST CÁC ĐỊA CHỈ IP CẦN NAT
access-list 1 permit 10.0.10.1 0.0.0.255

# ÁP DỤNG NAT DỰA THEO NAT-POOL VÀ ACCESS-LIST ĐÃ CÓ
ip nat inside source list 1 pool NAT_POOL overload
```

### CẤU HÌNH SITE-TO-SITE TRÊN CISCO ROUTER

Tham khảo bước cấu hình tại [[2]](https://www.cisco.com/c/en/us/support/docs/routers/1700-series-modular-access-routers/71462-rtr-l2l-ipsec-split.html#toc-hId--579114321):

**Tại Gateway 1**:

- Tạo một ISAKMP policy cho Phase 1 negotiation của L2L tunnel với sequence number là 10, thuật toán mã hóa là AES, thuật toán băm là SHA 256, phương thức xác thực là pre-share [[5]](https://csrc.nist.gov/glossary/term/pre_shared_key) và Diffie-Hellman thuộc nhóm 1:

```
crypto isakmp policy 10
encryption aes
hash sha
authentication pre-share
group 1
```

- Preshare key là "vpnuser" sẽ được sử dụng với interface thiết lập VPN với địa chỉ là 14.14.14.6 (địa chỉ công khai `ANOTHER SITE`):

```
crypto isakmp key vpnuser address 14.14.14.6
```

- Tạo Phase 2 policy cho IPSec negotiation với transform-set là "MY_SET", ESP transform sử dụng mật mã AES và xác thực bằng SHA256:

```
crypto ipsec transform-set MY_SET esp-aes esp-sha-hmac
```

- Tạo access-list (Extend ACL) cho luồng mạng cần được mã hóa (cụ thể là từ các mạng 10.0.10.0/24, 10.0.20.0/24 và 10.0.100.0/24 đến 14.14.14.6):

```
access-list 100 permit ip 10.0.10.0 0.0.0.255 12.12.12.6 0.0.0.255
access-list 100 permit ip 10.0.20.0 0.0.0.255 12.12.12.6 0.0.0.255
access-list 100 permit ip 10.0.100.0 0.0.0.255 12.12.12.6 0.0.0.255
```

- Tạo một Crypto Map có tên là "MY_MAP" với sequence number là 10, và chế độ cấu hình ipsec-isakmp:

```
crypto map MY_MAP 10 ipsec-isakmp
set peer 14.14.14.6 # địa chỉ IP của bên đầu kia của kết nối VPN
set transform-set MY_SET # transform-set đã tạo
match address 100 # access-list đã tạo
```

- Cấu hình interface đối diện với INTERNET áp dụng Crypto Map đã thiết lập là "MY_MAP" cho IPSec VPN:

```
interface fa0/0
crypto map MY_MAP
```

**Taị Gateway 2**:

- Tạo ISAKMP policy cho Phase 1 negotiation cho L2L tunnel với sequence number là 10, thuật toán mã hóa aes, hàm băm là sha256, phương thức xác thực là pre-share và Diffie-Helman group là 1:

```
crypto isakmp policy 10
encryption aes
hash sha
authentication pre-share
group 1
```

- Preshare key là "vpnuser" sẽ được sử dụng với interface thiết lập VPN với địa chỉ là 12.12.12.6 (địa chỉ công khai `ANOTHER SITE`):

```
crypto isakmp key vpnuser address 12.12.12.6
```

- Tạo Phase 2 policy cho IPSec negotiation với transform-set là MY_SET ESP transform sử dụng mật mã AES và xác thực bằng SHA 256:

```
crypto ipsec transform-set MY_SET esp-aes esp-sha-hmac
```

- Tạo access-list (Extend ACL) cho luồng mạng cần được mã hóa (cụ thể là từ mạng 192.168.10.0/24 đến 14.14.14.0/24)

```
access-list 100 permit ip 192.168.10.0 0.0.0.255 14.14.14.0 0.0.0.255
```

- Tạo một Crypto Map có tên là "MY_MAP" với sequence number là 10, và chế độ cấu hình ipsec-isakmp:

```
crypto map MY_MAP 10 ipsec-isakmp
set peer 12.12.12.6
set transform-set MY_SET
match address 100
```

- Cấu hình interface đối diện với INTERNET áp dụng Crypto Map đã thiết lập là "MY_MAP" cho IPSec VPN:

```
interface fa0/0
crypto map MY_MAP
```

## REFERENCE

[1] <https://support.huawei.com/enterprise/en/doc/EDOC1100034238/f2298f86/using-ipsec-vpn-to-implement-secure-interconnection-between-lans>

[2] <https://www.cisco.com/c/en/us/support/docs/routers/1700-series-modular-access-routers/71462-rtr-l2l-ipsec-split.html>

[3] <https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Fireware/mvpn/general/ipsec_vpn_negotiations_c.html>

[4] <https://www.cisco.com/c/en/us/support/docs/security-vpn/ipsec-architecture-implementation/118048-technote-ipsec-00.html>

[5] <https://csrc.nist.gov/glossary/term/pre_shared_key>

[6] <https://www.firewall.cx/cisco/cisco-routers/cisco-router-site-to-site-ipsec-vpn.html>
