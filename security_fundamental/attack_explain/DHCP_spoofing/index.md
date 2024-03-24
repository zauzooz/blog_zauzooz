# DHCP ATTACK

Các phương pháp tấn công DHCP server:

- Giả mạo DHCP response (trước khi DHCP response thật từ server có thể đến được) đến cho user và cài đặt các tham số như IP address, netmask, IP gateway (có thể là IP của attacker) và IP DNS server (IP DNS server là IP của máy attacker).
- Nếu switch cấu hình ip-helper có cơ chế bảo mật yếu, ta có thể telnet vào và thay đổi cấu hình ip-helper sang địa chỉ IP máy attacker.
