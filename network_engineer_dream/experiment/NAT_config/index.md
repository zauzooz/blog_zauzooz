# CẤU HÌNH NAT

![Topology](./img/topology.png)

**Yêu cầu:**

Cấu hình mạng có kiến trúc như hình, đảm bảo các user trong mạng nội bộ có thể giao tiếp với DNS server và Web Server.

Mạng nội bộ bên trái, PC 0 có thể truy cập đến DNS server và Web server. Server cung cấp dịch vụ DHCP và HTTP/HTTPS.

Mạng nội bộ bên phải PC 1 và PC 2 có thể truy cập đến DNS Server, Web Server và Web Server của mạng nội bộ bên trái. Server cung cấp dịch vụ DHCP.

## Bước cấu hình

B1: Thực hiện cấu hình các interface như sau, dùng địa chỉ mạng là 8.8.8.0/24 để mô phỏng mạng Internet.

|Machine|Interface|IP address|Netmask|
|:------|:--------|:---------|:------|
|DNS Server|Fa0|8.8.8.8|255.255.255.0|
|Web Server|Fa0|8.8.8.9|255.255.255.0|
|Gateway (Left)|Gig0/0|8.8.8.100|255.255.255.0|
|Gateway (Left)|Gig0/1|192.168.1.1|255.255.255.0|
|Gateway (Right)|Gig0/0|8.8.8.101|255.255.255.0|
|Gateway (Right)|Gig0/1|192.168.1.1|255.255.255.0|
|Internal Server (Left)|Fa0|192.168.1.2|255.255.255.0|
|Internal Server (Right)|Fa0|192.168.1.2|255.255.255.0|

B2: Tại mạng bên trái, cấu hình dynamic NAT để các máy có thể truy cập ra ngoài Internet và static NAT cho máy server.

B3: Tại mạng bên phải, cấu hình dynamic NAT để cho các máy có thể truy cập Internet.
