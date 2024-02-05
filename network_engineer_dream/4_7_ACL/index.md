# ACCESS CONTROL LIST (ACL)

Chúng ta chỉ xét ACL trong vấn đề Networking.

ACL trong Networking được cài đặt trên Router hay Switch như là một bộ lọc gói tin để kiểm soát (allow/deny) truy cập (in/out) một mạng nào đó dựa vào các quy tắc (rules) đã được cấu hình [[1]](https://support.huawei.com/enterprise/en/doc/EDOC1100086647).

ACL hoạt động như một stateless firewall [[5]](https://www.juniper.net/documentation/us/en/software/junos/routing-policy/topics/concept/firewall-filter-overview.html) - tức là không xét đến trạng thái tương tác giữa hai máy mà chỉ xét dến gói tin một cách thuần túy. Cisco ISO cung cấp từ khóa **established** để mô phỏng statefull bằng cờ ACK hoặc RST.

Đối với cấu hình IP ACL trên Cisco, IP ACL sẽ dựa vào địa chỉ IP và port để đưa ra các quy tắc để kiểm soát truy cập. Có rất nhiều loại IP ACL điển hình như là **Standard ACL** và **Extented ACL**, xem thêm các ACL khác và cách cấu hình tại [[2]](https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html).

So sánh giữa Standard ACL và Extended ACL [[3]](https://www.ciscopress.com/articles/article.asp?p=3089353&seqNum=7):

- Standard ACL: ACL chỉ cho phép hay cấm gói tin dựa trên địa chỉ IP(v4). ACL number cho Standard ACL là 1-99 và 1300-1999 đối với thiết bị Cisco [[4]](https://www.ciscopress.com/articles/article.asp?p=1697887).
- Extended ACL: ACL cho phép hay cấm gói tin dựa trên địa chỉ IP(v4), giao thức, cổng nguồn và đích của giao thức TCP hoặc UDP,... ACL number cho Extend ACL là 100-199 và 2000-2699 đối với thiết bị Cisco [[4]](https://www.ciscopress.com/articles/article.asp?p=1697887)

## REFERENCE

[1] <https://support.huawei.com/enterprise/en/doc/EDOC1100086647>

[2] <https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html>

[3] <https://www.ciscopress.com/articles/article.asp?p=3089353&seqNum=7>

[4] <https://www.ciscopress.com/articles/article.asp?p=1697887>

[5] <https://www.juniper.net/documentation/us/en/software/junos/routing-policy/topics/concept/firewall-filter-overview.html>
