# MÔ HÌNH OSI

Mô hình OSI (Open Systems Interconnection) là một khung khái nhiệm chia hoạt động của mạng thành 7 lớp, mỗi lớp có một vai trò riêng nhằm đảm bảo hoạt động giao tiếp trên mạng chính xác và ổn định.

Mô hình OSI:

- Layer 1 - Tầng vật lý (Physical): Đảm bảo thông điệp có thể truyển trong một môi trường cụ thể như không khí, dây cáp,.... Một số thiết bị liên quan đến lớp này như RJ45, [Hub](../1_network_devices/index.md#hub), Phisical Interface
- Layer 2 - Data Link: MAC address, [Bridge](../1_network_devices/index.md#bridge), [Switch (L2)](../1_network_devices/index.md#switch), [ARP](./ARP/index.md), VTP
- Layer 3 - Network: [IP address](../4_1_IPaddress_Netmask/index.md), Router, [ICMP](./ICMP/index.md)
- Layer 4 - [Transport Layer](../2_OSI_model_and_Protocol/Transport_Layer_Protocol/index.md): [TCP](../2_OSI_model_and_Protocol/Transport_Layer_Protocol/TCP/index.md), [UDP](../2_OSI_model_and_Protocol/Transport_Layer_Protocol/UDP/index.md)
- Layer 7 - Application Layer: HTTP, [DNS](../2_OSI_model_and_Protocol/DNS/index.md), [DHCP](./DHCP/index.md), [NTP](./NTP/index.md), [SNMP](../8_Network_Management/SNMP/index.md)
