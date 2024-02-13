# SPANNING TREE PROTOCOL example

![topology](./img/topology.png)

Cấu hình cho một switch L3 là STP root và switch L3 còn lại là STP backup root. Bên cạnh đó, cấu hình portfast cho các cổng kết nối trực tiếp với các máy trạm và server. Giao thức STP dược sử dụng là Rapid-PVST.

## CÁC BƯỚC CẤU HÌNH

### CẤU HÌNH ĐỊA CHỈ IP, VLAN

|Machine|Inerface|IP address|Netmask|Gateway|
|:------|:-------|:---------|:------|:------|
|PC1|Fa0|192.168.10.5|255.255.255.0|192.168.10.1|
|PC2|Fa0|192.168.20.5|255.255.255.0|192.168.20.1|
|PC3|Fa0|192.168.10.6|255.255.255.0|192.168.10.1|
|PC4|Fa0|192.168.20.6|255.255.255.0|192.168.20.1|
|Server|Fa0|192.168.100.5|255.255.255.0|192.168.100.1|
|SD1|VLAN 10|192.168.10.1|255.255.255.0|#|
|SD1|VLAN 20|192.168.20.1|255.255.255.0|#|
|SD1|VLAN 100|192.168.100.1|255.255.255.0|#|

Cấu hình VTP server cho SD1, VTP client cho các switch còn lại. Đặc biệt SD2 được cấu hình như một backup VTP server.

### CẤU HÌNH VTP (v3)

**Cấu hình SD1**:

- Cấu hình SD1 là một VTP server với VTP domain là `ZAUZOOZ`:

```
en
conf ter
vtp domain ZAUZOOZ
vtp mode server
exit
```

- Bên cạnh đó cũng tạo các VLAN 10 (HR), 20 (IR) và 100 (APP) và gán địa chỉ IP cho các VLAN này dựa vào bảng trên:


```
vlan 10
name HR
exit
vlan 20
name IT
exit
vlan 100
name APP
exit
interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shut
exit
interface vlan 20
ip address 192.168.20.1 255.255.255.0
exit
interface vlan 100
ip address 192.168.100.1 255.255.255.0
exit
```

- Cấu hình trunk port cho các cổng đến SA1 và SA 2:

```
interface gi1/0/1
switchport mode trunk
exit
interface gi1/0/2
switchport mode trunk
end
```

- Lưu cấu hình:

```
copy running-config startup-config
```

**Cấu hình SD2:**

- Cấu hình VTP:

```
en
conf ter
vtp domain ZAUZOOZ
vtp mode server
interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shut
exit
interface vlan 20
ip address 192.168.20.1 255.255.255.0
exit
interface vlan 100
ip address 192.168.100.1 255.255.255.0
end
copy running-config startup-config
```

- Cấu hình trunk port cho các cổng đến SA1 và SA 2:

```
interface gi1/0/1
switchport mode trunk
exit
interface gi1/0/2
switchport mode trunk
end
```

- Lưu cấu hình:

```
copy running-config startup-config
```

**Cấu hình SA1**:

- SA1 tham gia vào VTP domain `ZAUZOOZ` tham gia VTP domain `ZAUZOOZ` với vai trò là client:

```
en
conf ter
vtp domain ZAUZOOZ
vtp mode client
exit
```

- Cấu hình các trunk port với các cổng kết nối với SD1 và SD2:

```
interface gi0/1
switchport mode trunk
exit
interface gi0/2
switchport mode trunk
exit
```

- Cấu hình các access port với các cổng kết nối đến máy trạm với VLAN tương ứng:

```
interface fa0/24
switchport mode access
switchport access vlan 10
exit
interface fa0/23
switchport mode access
switchport access vlan 20
end
```

- Lưu cấu hình:

```
copy running-config startup-config
```

**Cấu hình SA2**:

- SA2 tham gia vào VTP domain `ZAUZOOZ` với vai trò là client:

```
en
conf ter
vtp domain ZAUZOOZ
vtp mode client
exit
```

- Cấu hình các trunk port với các cổng kết nối với SD1 và SD2:

```
interface gi0/1
switchport mode trunk
exit
interface gi0/2
switchport mode trunk
exit
```

- Cấu hình các access port cho các cổng kết nối đến máy trạm với các VLAN tương ứng:

```
interface fa0/24
switchport mode access
switchport access vlan 10
exit
interface fa0/23
switchport mode access
switchport access vlan 20
interface fa0/22
switchport mode access
switchport access vlan 100
end
```

- Lưu cấu hình:

```
copy running-config startup-config
```

### CẤU HÌNH STP

Mặc dù mặc định, các switch sẽ tự động sử dụng hoạt động spanning-tree (mặc định sử dụng Rapid PVST+ [[4]](https://www.cisco.com/en/US/docs/switches/datacenter/nexus5000/sw/configuration/guide/cli_rel_4_1/Cisco_Nexus_5000_Series_Switch_CLI_Software_Configuration_Guide_chapter12.pdf)), tuy nhiên ta cần tự cấu hình spanning-tree để mọi thứ được như ý muốn. Cụ thể ta cần cấu hình tất cả các switch tham gia một cách thống nhất bằng giao thức rapid-pvst và thực hiện cấu hình STP sao cho SD1 là root chính, SD2 là backup root như yêu cầu đặt ra.

Các giá trị mặc định của STP và vai trò của mỗi giá trị xem tại [[3]](https://www.cisco.com/c/en/us/td/docs/routers/access/3200/software/wireless/SpanningTree.html#wp1044449). Ta cần cấu hình SD1 và SD2 với các tham số như sau:

- Đối với SD1:

|Setting|Value|
|:------|:----|
|mode|rapid-pvst|
|vlan 10 priority|0|
|vlan 20 priority|0|
|vlan 100 priority|0|

- Đối với SD2:

|Setting|Value|
|:------|:----|
|mode|rapid-pvst|
|vlan 10 priority|1|
|vlan 20 priority|1|
|vlan 100 priority|1|

- Đối với SA1:

|Setting|Value|
|:------|:----|
|mode|rapid-pvst|
|vlan 10 priority|32768|
|vlan 20 priority|32768|
|vlan 100 priority|32768|

- Đối với SA2:

|Setting|Value|
|:------|:----|
|mode|rapid-pvst|
|vlan 10 priority|32768|
|vlan 20 priority|32768|
|vlan 100 priority|32768|

**Tại SD1**:

```
en
conf ter
spanning-tree
spanning-tree mode rapid-pvst
spanning-tree vlan 1 priority 0
spanning-tree vlan 10 priority 0
spanning-tree vlan 20 priority 0
spanning-tree vlan 100 priority 0
exit
copy running-config startup-config
```

**Tại SD2**:

```
en
conf ter
spanning-tree
spanning-tree mode rapid-pvst
spanning-tree vlan 1 priority 4096
spanning-tree vlan 10 priority 4096
spanning-tree vlan 20 priority 4096
spanning-tree vlan 100 priority 4096
exit
copy running-config startup-config
```

**Tại SA1**:

```
en
conf ter
spanning-tree
spanning-tree mode rapid-pvst
spanning-tree vlan 1 priority 32768
spanning-tree vlan 10 priority 32768
spanning-tree vlan 20 priority 32768
spanning-tree vlan 100 priority 32768
exit
copy running-config startup-config
```

**Tại SA2**:

```
en
conf ter
spanning-tree
spanning-tree mode rapid-pvst
spanning-tree vlan 1 priority 32768
spanning-tree vlan 10 priority 32768
spanning-tree vlan 20 priority 32768
spanning-tree vlan 100 priority 32768
exit
copy running-config startup-config
```

### BẬT CHẾ ĐỘ ROUTING TRÊN L3 SWITCH

Để các L3 switch có thể cho các VLAN khác nhau có thể giao tiếp với nhau, cần bật chế độ routing của các switch lên:

- Tại SD1:

```
en
conf ter
ip routing
```

- Tại SD2:

```
en
conf ter
ip routing
```

### VTP version 3

Có thể thực hiện cấu hình VTP version 3 cho phép switch L3 SD1 là một primary VTP server và SD2 như là một secondary VTP server [[2]](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus6000/sw/layer2/7x/b_6k_Layer2_Config_7x/config_vtp_v3.pdf). Tuy nhiên do packet tracert không có VTP version 3 nên cần thực hiện cấu hình STP version 3 ở các ứng dụng giả lập khác như GNS3 hay EVE-NG.

## REFERENCE

[1] <https://www.cisco.com/c/en/us/support/docs/smb/switches/cisco-small-business-300-series-managed-switches/smb5760-configure-stp-settings-on-a-switch-through-the-cli.html>

[2] <https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus6000/sw/layer2/7x/b_6k_Layer2_Config_7x/config_vtp_v3.pdf>

[3] <https://www.cisco.com/c/en/us/td/docs/routers/access/3200/software/wireless/SpanningTree.html>

[4] <https://www.cisco.com/en/US/docs/switches/datacenter/nexus5000/sw/configuration/guide/cli_rel_4_1/Cisco_Nexus_5000_Series_Switch_CLI_Software_Configuration_Guide_chapter12.pdf>
