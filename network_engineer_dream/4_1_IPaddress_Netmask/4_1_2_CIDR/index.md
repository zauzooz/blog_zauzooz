# CLASSES INTER-DOMAIN ROUTING

Sự phát triển của mạng dẫn đến các vấn đề như sau [[1]](https://datatracker.ietf.org/doc/html/rfc1519):

- Cạn kiệt không gian địa chỉ mạng lớp B. Một Nguyên nhân cơ bản của vấn đề này là do thiếu mạng loại có kích thước phù hợp cho kích thước trung bình tổ chức; lớp C, với tối đa 254 địa chỉ thì quá nhỏ, trong khi lớp B cho phép tối đa 65534 địa chỉ thì lại quá lớn đối với hầu hết các tổ chức.

- Sự phát triển của bảng định tuyến trong các bộ định tuyến Internet vượt ra ngoài phạm vi khả năng của phần mềm, phần cứng và con người hiện tại quản lý một cách hiệu quả.

- Cuối cùng không gian địa chỉ IP 32-bit sẽ cạn kiệt.

CIDR là một phương pháp phân bố địa chỉ IP cho IP routing, xác định địa chỉ IP và tiền tố (prefix - liên quan đến netmask, ví dụ netmask 255.255.255.0 thì tương đương với prefix là 24). Ký hiệu của CIDR đối với địa chỉ IPv4 là 192.168.3.5/24.

## REFERENCE

[1] <https://datatracker.ietf.org/doc/html/rfc1519>

[2] <https://www.solarwinds.com/resources/it-glossary/cidr>
