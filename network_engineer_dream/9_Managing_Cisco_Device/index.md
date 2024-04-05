# CISCO DEVICE MANAGEMENT

Các loại bộ nhớ trong Cisco Router bao gồm:

- Central Processing Unit: thực hiện các phép tính tóan như tính đường đi tốt nhất cho thuật các thuật toán định tuyến.
- Flash Memory: thường dùng cho việc lưu trữ Cisco IOS image.
- Read-Only Memory: chứa bootstrap startup program và các POST (Power On Self Test) program
- Random Access Memory (RAM): bộ nhớ dùng trong quá trình vận hành của thiết bị, chứa trên đó bao gồm Cisco ISO image, running-configuration, bảng định tuyến,... Dữ liệu trên RAM sẽ bị mất đi nếu thiết bị tắt.
- Non-Volatile RAM: thường dùng cho việc lưu trữ startup-configuration.

Cisco router có hai tệp cấu hình: thứ nhất là cấu hình để cho router bắt đầu chạy được lưu trữ trong NVRAM và thứ là cấu hình cho quá trình vận hành của router được chứa ở RAM [[3]](https://www.sciencedirect.com/topics/computer-science/startup-configuration#:~:text=There%20are%20two%20configurations%20stored,while%20the%20router%20is%20operating.).

Quy trình boot router:

- Bước 1: Đầu tiên router sẽ thực thi chương trình POST để kiểm tra các phần cứng của thiết bị có khả dụng hay không.
- Bước 2: Kiểm tra Configuration Register để xác định cách thức boot router, cụ thể là cho biết là cho biết tệp phần mềm Cisco IOS nằm ở đâu (ở bộ nhớ Flash, FTP server hoặc ở ROM) và có thực hiện chạy start-up config hay không.

## REFERENCE

[1] <https://www.geeksforgeeks.org/router-boot-sequence/>

[2] <https://www.cisco.com/c/en/us/support/docs/routers/10000-series-routers/50421-config-register-use.html>

[3] <https://www.sciencedirect.com/topics/computer-science/startup-configuration>
