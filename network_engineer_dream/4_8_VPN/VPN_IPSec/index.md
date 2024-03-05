# IPSEC VPN

## IPSec VPN

Công nghệ VPN dựa trên IPSec sử dụng chuẩn Internet Security Association and Key Managment Protocols (ISMKMP hoặc IKE) tunelling và chuẩn IPSec tunneling để xây dựng và quản lý các VPN tunnel [[1]](https://www.cisco.com/c/en/us/td/docs/security/firepower/623/fdm/fptd-fdm-config-guide-623/fptd-fdm-s2svpn.html).

## Internet Key Exchange

Trao đổi khóa Internet (IKE) là một **giao thức quản lý khóa** được sử dụng để xác thực các IPsec ngang hàng, thương lượng và phân phối các khóa mã hóa IPsec và để tự động thiết lập các liên kết bảo mật IPsec (SA).

VPN Negotiation được chi làm hai bước quan trọng [[1]](https://www.cisco.com/c/en/us/td/docs/security/firepower/623/fdm/fptd-fdm-config-guide-623/fptd-fdm-s2svpn.html) [[2]](https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Fireware/mvpn/general/ipsec_vpn_negotiations_c.html):

- *Phase 1*: Thiết lập một đường kết nối an toàn giữa hai máy ngang hàng để thực hiện Phase 2.
- *Phase 2*: Bước này là bước cho hai bên đồng ý một tập các tham số để cho biết traffic nào có thể đi qua VPN, và cách mã hóa và xác thực luồng mạng.

Lưu ý rằng cấu hình Phase 1 và Phase 2 ở các thiết bị thiết lập cổng cần phải khớp với nhau.

## REFERENCE

[1] <https://www.cisco.com/c/en/us/td/docs/security/firepower/623/fdm/fptd-fdm-config-guide-623/fptd-fdm-s2svpn.html>

[2] <https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Fireware/mvpn/general/ipsec_vpn_negotiations_c.html>
