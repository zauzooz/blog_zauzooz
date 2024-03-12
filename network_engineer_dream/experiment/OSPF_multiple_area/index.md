# MULTIPLE AREA OSPF CONFIGURATION

![img](./img/topology.png)

Cấu hình OSPF nhiều area như mô hình.

## BƯỚC CẤU HÌNH

- **Cấu hình địa chỉ IP như bảng sau**:

|Machine|Interface|IP address|Netmask|
|:------|:--------|:---------|:------|
|ABR01|gi0/0|10.0.0.5|255.255.255.252|
|ABR01|gi0/1|10.0.0.9|255.255.255.252|
|ABR02|gi0/0|10.0.0.6|255.255.255.252|
|ABR02|gi0/1|10.0.0.21|255.255.255.252|
|IR11|gi0/1|10.0.0.10|255.255.255.252|
|IR11|gi0/0|10.0.0.13|255.255.255.252|
|IR11|gi0/2|10.0.0.17|255.255.255.252|
|IR12|gi0/0|10.0.0.14|255.255.255.252|
|IR12|loopback 0|2.2.2.2|255.255.255.252|
|IR21|gi0/1|10.0.0.22|255.255.255.252|
|IR21|gi0/0|10.0.0.25|255.255.255.252|
|IR22|loopback 0|2.2.2.2|255.255.255.255|
|IR22|gi0/0|10.0.0.26|255.255.255.252|
|ABR03|gi0/2|10.0.0.16|255.255.255.252|
|ABR03|gi0/0|10.0.0.29|255.255.255.252|
|IR31|gi0/0|10.0.0.30|255.255.255.252|
|IR32|loopback 0|3.3.3.1|255.255.255.255|

## REFERENCE

[1] <https://www.cisco.com/c/en/us/support/docs/ip/open-shortest-path-first-ospf/118879-configure-ospf-00.html>

[2] <https://www.cisco.com/c/en/us/support/docs/ip/open-shortest-path-first-ospf/7039-1.html>
