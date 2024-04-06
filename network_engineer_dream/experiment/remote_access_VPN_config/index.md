# CẤU HÌNH REMOTE-ACCESS-VPN

![topology](./img/topology.png)

Yêu cầu:

- Trong SITE 1, đảm bảo các máy có thể ping được với nhau.
- Trong SITE 1, cấu hình VTP server cho Core switch và Access switch là VTP client với domain là NNT.
- Trong SITE 1, PC 1 tham gia VLAN 10 và File Server tham gia VLAN 100.
- Thực hiện cấu hình remote access VPN để máy PC2 có thể tham gia vào SITE 1, có thể ping đến PC 1 và có thể ping và ftp vào File Server.

## CÁC BƯỚC CẤU HÌNH

### Cấu hình địa chỉ IP

Đầu tiên, thực hiện cấu hình địa chỉ cho các interface sau:

|Machine|Interface|IP address|Netmask|Gateway|
|:------|:--------|:---------|:------|:------|
|Gateway 1|gi0/0|10.0.1.254|255.255.255.0|#|
|Gateway 1|se0/0/0|172.16.0.2|255.255.255.252|#|
|Core|gi1/0/1|10.0.1.253|255.255.255.0|#|
|Core|VLAN 10|10.0.10.254|255.255.255.0|#|
|Core|VLAN 100|10.0.100.254|255.255.255.0|#|
|PC 1|Fa0|10.0.10.5|255.255.255.0|10.0.10.254|
|File Server|Fa0|10.0.100.5|255.255.255.0|10.0.100.5|
|ISP|se0/2/0|172.16.0.1|255.255.255.252|#|
|ISP|se0/2/1|172.16.0.5|255.255.255.252|#|
|Gateway 2|se0/0/0|172.16.0.6|255.255.255.252|#|
|Gateway 2|gi0/0|192.168.1.254|255.255.255.0|#|
|PC 2|Fa0|192.168.1.5|255.255.255.0|192.168.1.254|

### Cấu hình định tuyến

- Cấu hình OSPF area 1 cho Core switch:

```
router ospf 1
network 0.0.0.0 255.255.255.255 are 1
```

- Cấu hình OSPF are 1 cho interface gi0/0 và OSPF area 0 cho interface se0/0/0 của Gateway 1:

```
interface gi0/0
ip ospf 1 area 1
interface se0/0/0
ip ospf 1 area 0
```

- Tại ISP, cấu hình quảng bá OSPF area 0 với process id là 1 cho toàn bộ interface:

```
router ospf 1
network 0.0.0.0 255.255.255.255 area 0
```

- Tại Gateway 2, cấu hình quảng bá OSPF area 0 với process id là 1 cho toàn bộ interface:

```
router ospf 1
network 0.0.0.0 255.255.255.255 area 0
```

### Cấu hình remote-access VPN

Tại Gateway 1:

- Đầu tiên cung cấp pool IP sẽ cung cấp cho người dùng VPN và username password cho người dùng:

```
ip local pool ACCESSVPN 10.0.30.5 10.0.30.10
username nnt password 1234
```

- Khai báo tham số IPSec pha 1:

```
crypto isakmp policy 10
encryption aes
hash md5
authentication pre-share
group 2
```

## REFERENCE

[1] <https://www.cisco.com/c/en/us/td/docs/security/firepower/623/fdm/fptd-fdm-config-guide-623/fptd-fdm-ravpn.html>

[2] <https://hainguyenit.edubit.vn/blog/cau-hinh-vpn-remote-access-tren-router-cisco>

[3] <https://www.firewall.cx/cisco/cisco-routers/cisco-router-vpn-client.html>
