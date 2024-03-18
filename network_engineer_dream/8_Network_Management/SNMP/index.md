# SIMPLE NETWORK MANAGEMENT PROTOCOL

SNMP là giao thức ở tầng ứng dụng (Application Layer), sử dụng UDP port là 161/162 để giám sát mạng, phát hiện lỗi mạng và đôi khi là điều khiển thiết bị mạng từ xa.

Các thành phần của SNMP:

- **SNMP Manager**: SNMP là một hệ thông quản lý mạng (Network Management System - NMS). SNMP manager là một hệ thống chịu trách nhiệm quản lý và giám sát các thiết bị mạng. Nó thu thập và xử lý thông tin từ các tác nhân SNMP, đưa ra lệnh sửa đổi cấu hình thiết bị và tạo cảnh báo dựa trên các sự kiện mạng. SNMP manager chạy ***SNMP client program*** cho phép lý mạng cho phép quản trị viên dùng giao thức SNMP để tương tác với các thiết bị được quản lý.
- **SNMP Agent**: SNMP agent là một mô-đun phần mềm được nhúng trong các thiết bị mạng như bộ định tuyến (router), bộ chuyển mạch (switch), máy trạm (workstation), PC,.... SNMP agent chạy một ***SNMP server program*** mà nó thực hiện các tác vụ như thu thập và lưu trữ thông tin về hoạt động và trạng thái của thiết bị, phản hồi yêu cầu hoặc thực hiện hành động từ SNMP manager chẳng hạn cung cấp dữ liệu từ Cơ sở thông tin quản lý (MIB) của nó, thực thi các lệnh để thay đổi cài đặt thiết bị,...
- **MIB (Management Information Base)**: MIB là cơ sở dữ liệu ảo lưu các thông tin quản lý từ việc thu thập của SNMP agent. Nó bao gồm một tập hợp các đối tượng có thứ bậc, mỗi đối tượng đại diện cho một khía cạnh cụ thể của thiết bị mạng, chẳng hạn như cấu hình hệ thống, thống kê hiệu suất hoặc trạng thái giao diện. Mỗi đối tượng trong MIB có một mã định danh duy nhất gọi là OID và được mô tả bằng một định nghĩa văn bản được gọi là định nghĩa MIB. Người quản lý SNMP sử dụng định nghĩa MIB để hiểu cấu trúc và ý nghĩa của dữ liệu được lấy từ các SNMP agent.

SNMP quản lý mạng dựa vào các ý tưởng cơ bản như sau:

- SNMP Manager thực hiện gửi một yêu cầu đến SNMP agent.
- SNMP Agent thực hiện lắng nghe các yêu cầu từ SNMP manager và thực thiện:
    - Nếu yêu cầu trích xuất thông tin thì Agent sẽ trích xuất thông tin từ MIB và gửi lại cho SNMP Manager.
    - Nêu yêu cầu là một hành động, chẳng hạn như thay đổi cấu hình, Agent sẽ thực thi nó.

## REFERENCE

[1] <https://datatracker.ietf.org/doc/html/rfc1157>

[2] <https://www.geeksforgeeks.org/simple-network-management-protocol-snmp/>

[3] <https://www.cisco.com/c/en/us/td/docs/optical/cpt/r9_3/configuration/guide/cpt93_configuration/cpt93_configuration_chapter_010011.pdf>
