# FIREWALL

Firewall là một phần mềm hoặc phần cứng được thiết kế để bảo vệ mạng máy tính khỏi các mối đe dọa bảo mật và nguy cơ xâm nhập từ bên ngoài. Chức năng chính của firewall bao gồm giám sát và kiểm soát lưu lượng dữ liệu giữa mạng nội bộ và mạng bên ngoài, quyết định xem liệu dữ liệu nào được phép đi qua hay không, dựa trên các quy tắc (rule) được cấu hình trước.

Một số loại tường lửa:

|Loại|Chức năng nổi bật|Sản phẩm|
|:---|:-------|:----------|
|Stateless Firewall|Quyết định xem một gói dữ liệu nên được chấp nhận hoặc từ chối dựa trên thông tin trong tiêu Một số tên hãng đề gói dữ liệu, không quan tâm đến trạng thái của kết nối.|Có trong các thiết bị Layer 3 của Cisco như Router, L3 Switch|
|Statefull Firewall|Có khả năng theo dõi trạng thái của mỗi kết nối (tương tác giữa 2 máy đang giao tiếp với nhau) và áp dụng quy tắc dựa trên trạng thái này.|Pfsense, Cisco ASA|
|Next-Generation Firewall (NGFW)|Cung cấp kiểm soát chi tiết hơn về ứng dụng, người dùng và đường dẫn. Được bổ sung cơ chế Deep Packet Inspection (DPI) nhằm quan sát nội dung của gói tin ở tầng thứ 7 (Application)|Palo Alto Firewall, Fortinet|
|Web Application Firewall (WAF)|Kiểm soát và giám sát lưu lượng HTTP giữa các ứng dụng web và người dùng. Đặc biệt là tập trung vào phát hiện tấn công trong top 10 OWASP.|AWS WAF, ModSecurity, Imperva SecureSphere |
|Database Firewall|Ngăn chặn các tấn công dựa trên cơ sở dữ liệu và kiểm soát truy cập đến dữ liệu nhạy cảm trong cơ sở dữ liệu.|Oracle Database Firewall, IBM Guardium|
