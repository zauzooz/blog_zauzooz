# IP ADDRESS VÀ SUBNET MASK

Địa chỉ IP là một dãy số $x.y.z.t$ với $x , y, z, t \in [0,..,255]$ và $x, y, z, t \in \mathbb{N}$ là một giá trị định danh để có thể giao tiếp trên Internet. Ví dụ địa chỉ 192.168.1.12 là một địa chỉ IP. Thực tế mỗi $x$, $y$, $z$ hay $t$ là có thể được biễu diễn bằng một dãy số nhị phân có độ dài là 8 bit:

![Decical to Binary](/network_engineer_dream/4_1_IPaddress_Netmask/ip_address.png)

Bên cạnh địa chỉ IP, còn hai khái niệm quan trọng đó là Netmask, địa chỉ mạng và địa chỉ broadcast.

Netmask là một phần quan trọng để xác định địa chỉ mạng và địa chỉ máy tính, sẽ có dạng như địa chỉ IP trên, nhưng các bit đầu sẽ bằng 1 sẽ đại diện cho địa chỉ của mạng:

![Netmask](/network_engineer_dream/4_1_IPaddress_Netmask/netmask_network_address.png)

Như đã thấy, phần màu đỏ đại diện cho phần địa chỉ của mạng, trong khi đó phần màu xanh lá sẽ là vị trí của địa chỉ dành cho host. Khi đó ta có thể biễu diễn địa chỉ mạng ở dạng thập phân theo ký hiệu 192.168.1.0/24 với 192.168.1.0 là địa chỉ mạng sau khi đã mask bằng netmask và /24 chính là netmask - tương đương với 24 bit đầu tiên là 1.

![host_and_broadcast_addr](/network_engineer_dream/4_1_IPaddress_Netmask/host_broadcast.png)

Dựa vào hình trên, với địa chỉ mạng là 192.168.1.0/24:

- Địa chỉ IP cho máy đầu tiên là: 192.168.1.1
- Địa chỉ IP cho máy cuối cùng là: 192.168.1.254
- Địa chỉ broadcast là: 19.168.1.255
