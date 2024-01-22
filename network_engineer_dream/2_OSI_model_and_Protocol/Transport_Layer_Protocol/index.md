# TRANSPORT LAYER PROTOCOLS

## Các vấn đề của gói tin trên đường truyền mạng

Một số vấn đề của các gói tin trên đường truyền từ máy nguồn đến máy đích:

- Gói tin có đến được đích hay không (bị mất trên đường truyền do mạng hoạt động quá bận rộn, ...).
- Gói tin bị lỗi trên đường truyền (tín hiệu bị suy yếu,...).
- Thứ tự nhận gói có đúng hay không.

## User Diagram Protocol (UDP)

[UDP](./UDP/index.md) là giao thức connection less nằm ở tầng 4 trong mô hình OSI. UDP cung cấp về tốc độ cao hơn giao thức TCP ở truyền nhận gói tin tuy nhiên lại không cung cấp độ tin cậy và thứ tự truyền nhận của gói tin.

UDP được sử dụng ở các ứng dụng như DNS, VoIP và Streamming media.

## Transmission Control Protocol (TCP)

[TCP](./TCP/index.md) là giao thức connection oriented nằm ở tầng 4 trong mô hình OSI. TCP cung cấp cơ chế tin cậy và đảm bảo thứ tự trong truyền nhận tin.

Session Mutiplexing: một máy trạm có thể có nhiều kết nối mạng với nhiều máy chủ. Đối với giao thức TCP, cần thực hiện [bắt tay ba bước](./TCP/index.md#bắt-tay-3-bước-three-way-handshake) trước khi thực hiện truyền nhận dữ liệu.

Segmented:

- Phân đoạn gói tin trở nên vừa với MTU (Maximum Transmission Unit - kích thước tối của một thiết bị mạng).
- Giao thức TCP hỗ trợ tính năng này, trong khi đó UDP cần giao thức tầng cao hơn để hỗ trợ xử lý.

Full dumplex:

-...

Flow Control:

- TCP có sliding WINDOW sử dụng cơ chế Flow Control thực hiện kiểm soát luồng để tránh gói tin được gửi quá nhanh (nếu như dữ liệu được gửi đến nhanh hơn khả năng xử lý của máy nhận thì máy nhận sẽ vứt gói tin đó và yêu cầu gửi lại).
- UDP không sử dụng Flow Control. Cần giao thức tầng cao hơn để có được cơ chế này.

Error Control:

-...

Retransmission:

-...

Conguestion Control:

-...

Conection Oriented:

- TCP sử dụng connection oriented, yêu cầu thực hiện bắt tay ba bước để hình thành kết nối cũng như ngắt kết nối.
- UDP sử dụng connection less.

Reliability:

- Ở TCP, mỗi gói tin sẽ có có ACK và Seqence number để đảm bảo cơ chế tin cậy bao gồm thứ tự và đầy đủ gói tin.
- Ở UDP không có cơ chế Reliability, để có được cơ chế này cần giao thức ở tầng cao hơn.

## PORT

Giá trị dùng để xác định dịch vụ mạng và cổng giao tiếp của máy.

## SOCKET

Socket là sự kết hợp của 3 thông tin (địa chỉ IP, port và dịch vụ tầng transport) để xác định điểm kết nối của máy.

## So sánh sự khác biệt giữa TCP và UDP
