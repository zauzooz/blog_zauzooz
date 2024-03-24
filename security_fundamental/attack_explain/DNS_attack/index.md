# DNS ATTACK

Một số cách tấn công DNS:

- Tấn công thực hiện gửi một DNS response giả mạo trước khi DNS response thật từ server để đánh lừa máy gửi DNS request như máy user hoặc DNS server.
- Đầu độc thiết bị chuyển mạch hoặc định tuyến để dẫn luồng mạng (bao gồm DNS) đến máy thực hiện tấn công (ví dụ ARP Poisoning).
- Dùng [DHCP spoofing](../DHCP_spoofing/index.md) attack, bằng cách giả mạo gói tin IP trong đó thay đổi trường IP DNS server là địa chỉ IP máy attacker.
