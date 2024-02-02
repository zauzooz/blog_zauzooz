# CẤU HÌNH NAT

![Topology](./img/topology.png)

**Yêu cầu:**

Cấu hình mạng có kiến trúc như hình, đảm bảo các user trong mạng nội bộ có thể giao tiếp với DNS server và Web Server.

Ở mạng nội bộ Zone A, PC 0 có thể truy cập đến DNS server và Web server. Server cung cấp dịch vụ DHCP và HTTP/HTTPS. Router R1 thực hiện dynamic NAT để máy PC 0 truy cập Internet bằng một IP công khai. Router R1 cũng thực hiện static NAT cho HTTP server có một địa chỉ IP công khai, DNS server sẽ lưu địa chỉ công khai của HTTP server này.

Mạng nội bộ Zone B PC 1 có thể truy cập đến DNS Server, Web Server và HTTP Server của Zone A. Server cung cấp dịch vụ DHCP. Router R2 thực hiện dynamic NAT để máy PC 1 truy cập Internet bằng một IP công khai.

## Bước cấu hình

B1: Thực hiện cấu hình các interface như sau, dùng địa chỉ mạng là 8.8.8.0/24 để mô phỏng mạng Internet.

|Machine|Interface|IP address|Netmask|
|:------|:--------|:---------|:------|
|DNS Server|Fa0|8.8.8.8|255.255.255.0|
|Web Server|Fa0|8.8.8.9|255.255.255.0|
|R1|Gig0/0|8.8.8.100|255.255.255.0|
|R1|Gig0/1|192.168.1.1|255.255.255.0|
|R2|Gig0/0|8.8.8.101|255.255.255.0|
|R2|Gig0/1|192.168.1.1|255.255.255.0|
|Internal Server (Zone A)|Fa0|192.168.1.2|255.255.255.0|
|Internal Server (Zone B)|Fa0|192.168.1.2|255.255.255.0|

## REFERENCE

[1] <https://www.cisco.com/c/en/us/support/docs/ip/network-address-translation-nat/13772-12.html>