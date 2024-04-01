# SYSLOG PROTOCOL

Là giao thức một giao thức quản lý mạng dựa trên sự kiện (Query based).

Syslog thông thường sử dụng giao thức UDP ở Transport Layer.

## Các định nghĩa

Syslog hoạt động với 3 lớp bao gồm content, application và transport:

- Syslog Content: là thông tin quản lý chứa trong thông điệp syslog.
- Syslog Application: thực hiện việc sinh (generation), diễn giải (interpretation), định tuyến (routing) và lưu trữ (storage) các thông điệp syslog.
- Syslog Transport: đưa thông điệp lên đường truyền và lấy thông điệp từ đường truyền.

Một số chức năng hoạt động ở mỗi lớp khái niệm đó:

- Originator: tạo ra các nội dung syslog chứa trong thông điệp.
- Collector: thu thập các nội dung syslog cho việc phân tích trong tương lai.
- Relay: chuyển tiếp thông điệp, chấp nhận thông điệp từ một Originator hoặc các Relay khác và gửi chúng đến các Collector hoặc các Relay khác.
- Transport Sender: gửi thông điệp syslog bằng một giao thức tầng Transport cụ thể.
- Transport Reciver: nhận thông điệp syslog bằng một giao thức tầng Transport cụ thể.

## Logging Level - Serverity (Mức dộ nghiêm trọng)

Logging level thể hiện mức độ nghiêm trọng của thông điệp:

|Logging Level|Serverity|Ý nghĩa|
|:-----------:|:-------:|:------|
|0|Emergency (Khẩn cấp)|...|
|1|Alert (Cảnh báo)|...|
|2|Critical (Nghiêm trọng)|...|
|3|Error (Lỗi)|...|
|4|Warning (Cảnh báo)|...|
|5|Notice (Thông báo)|...|
|6|Informational (Chi tiết)|...|
|7|Debug (Gỡ lỗi)|...|

## Syslog Facility Code

Facility code dùng để xác định nguồn của thông điệp syslog:

|Code|Facility                           |
|:--:|:---------------------------------:|
| 0  | kernel messages                   |
| 1  | user-level messages               |
| 2  | mail system                       |
| 3  | system daemons                    |
| 4  | security/authorization messages   |
| 5  | messages generated internally by syslogd |
| 6  | line printer subsystem            |
| 7  | network news subsystem            |
| 8  | UUCP subsystem                    |
| 9  | clock daemon                      |
| 10 | security/authorization messages   |
| 11 | FTP daemon                        |
| 12 | NTP subsystem                     |
| 13 | log audit                         |
| 14 | log alert                         |
| 15 | clock daemon (note 2)             |
| 16 | local use 0 (local0)              |
| 17 | local use 1 (local1)              |
| 18 | local use 2 (local2)              |
| 19 | local use 3 (local3)              |
| 20 | local use 4 (local4)              |
| 21 | local use 5 (local5)              |
| 22 | local use 6 (local6)              |
| 23 | local use 7 (local7)              |


## REFERENCE

[1] <https://datatracker.ietf.org/doc/html/rfc5424>
