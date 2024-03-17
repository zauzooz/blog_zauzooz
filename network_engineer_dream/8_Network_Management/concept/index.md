# NETWORK MANAGEMENT FUNDAMENTAL

Các giao thức để quản lý mạng (Network Management Protocol - NMP) có thể kể đến: ICMP, SNMP, SNMP traps, Syslog, WMI (Windows Management Instrumentation).

Có 2 loại giao thức quản lý mạng bao gồm *giao thức quản lý mạng dựa trên truy vấn* và *giao thức quản lý mạng dựa trên sự kiện*.

**Giao thức quản lý mạng dựa trên truy vấn (Query-based Network Management Protocol)**:

- Trong các giao thức dựa trên truy vấn, hệ thống quản lý gửi định kỳ các yêu cầu hoặc truy vấn đến các thiết bị mạng để thu thập thông tin về trạng thái, cấu hình và hiệu suất của chúng.
- Các truy vấn này có thể được *lên lịch định kỳ* hoặc được quản trị viên mạng kích hoạt theo cách thủ công.
- Ví dụ về các giao thức dựa trên truy vấn bao gồm [ICMP](../../2_OSI_model_and_Protocol/ICMP/index.md), [SNMP](../SNMP/index.md) và CLI command (Telnet, SSH) được sử dụng để quản lý thiết bị mạng.

- Điểm mạnh:

    - Truy xuất dữ liệu có kiểm soát: NMP dựa trên truy vấn cho phép quản trị viên truy xuất thông tin cụ thể từ các thiết bị mạng theo yêu cầu, cung cấp quyền kiểm soát quá trình thu thập dữ liệu.
    - Sử dụng tài nguyên hiệu quả: Bằng cách chỉ bắt đầu các truy vấn khi cần, NMP dựa trên truy vấn giúp tiết kiệm băng thông mạng và tài nguyên thiết bị so với các phương pháp giám sát liên tục.
    - Hiệu suất có thể dự đoán: Với các khoảng thời gian thăm dò theo lịch trình hoặc thủ công, NMP dựa trên truy vấn cung cấp hiệu suất có thể dự đoán được cho các nhiệm vụ giám sát và thu thập dữ liệu.
    - Hỗ trợ phân tích lịch sử: NMP dựa trên truy vấn tạo điều kiện thuận lợi cho việc thu thập dữ liệu lịch sử, cho phép phân tích xu hướng, lập kế hoạch năng lực và khắc phục sự cố dựa trên các số liệu hiệu suất lịch sử.

- Điểm yếu:

    - Khả năng hiển thị trong thời gian thực bị hạn chế: NMP dựa trên truy vấn có thể không cung cấp khả năng hiển thị theo thời gian thực đối với các sự kiện mạng hoặc biến động hiệu suất do quá trình truy xuất dữ liệu diễn ra theo các khoảng thời gian được xác định trước.
    - Phát hiện bị trì hoãn: Các sự kiện hoặc sự cố xảy ra giữa các khoảng thời gian bỏ phiếu có thể không được phát hiện kịp thời, dẫn đến sự chậm trễ trong việc xác định và giải quyết các sự cố mạng.
    - Những thách thức về khả năng mở rộng tiềm ẩn: Trong các mạng quy mô lớn có nhiều thiết bị và yêu cầu thăm dò tần số cao, NMP dựa trên truy vấn có thể gặp phải những thách thức về khả năng mở rộng, chẳng hạn như tăng chi phí mạng và độ phức tạp trong quản lý.

**Giao thức quản lý mạng dựa trên sự kiện (Event-based Network Management Protocol)**:

- Trong các giao thức dựa trên sự kiện, các thiết bị mạng tạo và gửi thông báo sự kiện đến hệ thống quản lý bất cứ khi nào đáp ứng các điều kiện hoặc ngưỡng nhất định được xác định trước.
- Những sự kiện này có thể bao gồm cảnh báo về lỗi thiết bị, suy giảm hiệu suất, vi phạm bảo mật hoặc những thay đổi quan trọng khác trong môi trường mạng.
- Hệ thống quản lý phản ứng với những sự kiện này bằng cách thực hiện các hành động được xác định trước, chẳng hạn như gửi thông báo cho quản trị viên, kích hoạt phản hồi tự động hoặc ghi lại các sự kiện để phân tích.
- Ví dụ về các giao thức dựa trên sự kiện bao gồm [SNMP trap](../SNMP_trap/index.md), [Syslog](../Syslog/index.md), [NetFlow](../Netflow/index.md) và [IPFIX](../IPFIX/index.md) để phân tích lưu lượng truy cập và phát hiện sự bất thường.

- Điểm mạnh:

    - Khả năng hiển thị theo thời gian thực: NMP dựa trên sự kiện cung cấp thông báo và cảnh báo theo thời gian thực cho các sự kiện mạng, cho phép quản trị viên phản hồi kịp thời các sự cố nghiêm trọng và sự bất thường về hiệu suất.
    - Hành động ngay lập tức: Bằng cách kích hoạt cảnh báo ngay khi các sự kiện được xác định trước xảy ra, NMP dựa trên sự kiện tạo điều kiện thuận lợi cho việc ứng phó sự cố và giải quyết vấn đề nhanh chóng, giảm thiểu thời gian ngừng hoạt động và gián đoạn dịch vụ.
    - Sử dụng tài nguyên hiệu quả: Giám sát dựa trên sự kiện tập trung vào việc nắm bắt và xử lý các sự kiện có liên quan, tối ưu hóa việc sử dụng tài nguyên so với các phương pháp thăm dò liên tục.
    - Ngưỡng và chính sách có thể tùy chỉnh: Quản trị viên có thể xác định các ngưỡng và chính sách tùy chỉnh để điều chỉnh việc phát hiện và cảnh báo sự kiện theo nhu cầu và ưu tiên cụ thể của tổ chức.

- Điểm yếu:

    - Tiềm ẩn cảnh báo mệt mỏi: Nếu không điều chỉnh và lọc thích hợp, NMP dựa trên sự kiện có thể tạo ra cảnh báo quá mức, dẫn đến quản trị viên cảm thấy mệt mỏi về cảnh báo và có khả năng bỏ qua các vấn đề quan trọng.
    - Tương quan sự kiện phức tạp: Việc quản lý một khối lượng lớn các sự kiện đa dạng từ nhiều nguồn có thể đặt ra thách thức cho việc tương quan sự kiện và phân tích nguyên nhân gốc rễ, đòi hỏi các công cụ và phương pháp phức tạp.
    - Rủi ro về các sự kiện bị bỏ lỡ: NMP dựa trên sự kiện dựa vào việc tạo và truyền sự kiện kịp thời và chính xác bằng các thiết bị mạng, đồng thời việc báo cáo sự kiện bị lỗi hoặc chậm trễ có thể dẫn đến cảnh báo bị bỏ lỡ và giảm khả năng hiển thị về hiệu suất mạng.
