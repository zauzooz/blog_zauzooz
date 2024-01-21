# KHÁI NIỆM CƠ BẢN VỀ CÁC THIẾT BỊ MẠNG

## Hub

Hub là một thiết bị hoạt động ở [tầng 1 (Layer 1) trong mô hình OSI](/network_engineer_dream/2_OSI_model_and_Protocol/index.md).

Cơ chế của Hub khá đơn giản, khi nhận một frame ở một cổng, sẽ thực hiện gửi frame đó ra toàn bộ cổng còn lại (trừ cổng mà frame đến).

## Bridge

Bridge là một thiết bị hoạt động ở [tầng 2 (Layer 2) trong mô hình OSI](/network_engineer_dream/2_OSI_model_and_Protocol/index.md).

Bride có một thành phần đặc biệt là bảng địa chỉ MAC (MAC address table) giúp nó ghi lại địa chỉ MAC tương ứng với cổng nào. Cơ chế hoạt động của Bride tuân theo 2 nguyên tắc:

- Nếu một frame có địa chỉ A đến port x của Bridge thì nó sẽ thêm cặp (A, x) nếu cặp này không có trong bảng địa chỉ MAC.
- Tiếp theo xét địa chỉ đích của frame này là B, nếu trong bảng địa chỉ MAC không có cặp (B, y) nào thì Bridge sẽ thực hiện gửi frame này cho toàn bộ các cổng trừ cổng nhận frame, nếu có cặp (B, y) thì sẽ chỉ gửi frame này đi ra cổng y.

## Switch

**Switch vs Bridge**?

## Router

## Wireless Access Point

## Network Interface

## Network Adapter

## REFERENCE
