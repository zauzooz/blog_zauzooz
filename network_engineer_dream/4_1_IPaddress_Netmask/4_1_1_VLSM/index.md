# VARIABLE LENGHT SUBNET MASK

VLSM là một kỹ thuật được sử dụng trong mạng IP để tạo ra các subnet với các độ dài subnet mask khác nhau **trong cùng một mạng**. VLSM cho phép tận dụng địa chỉ IP một cách hiệu quả bằng cách lấy một subnet lớp hơn cho mạng có nhiều máy hoặc các subnet nhỏ hơn cho mạng có vài máy.

Ví dụ [[2]](https://datatracker.ietf.org/doc/html/rfc1878):

|Netmask|Stealed Bit|Number of Nets|Network Address|Host Addresss|Broadcast Address|
|:-----:|:---------:|:------------:|--------------:|:-----------:|:---------------:|
|255.255.128.0|1|2^1=2|N.N.0.0|N.N.0-127.N|N.0.127.255|
|*|*|*|N.N.128.0|N.N.128-254.N|N.N.254.255|

## REFERENCE

[1] <https://www.geeksforgeeks.org/introduction-of-variable-length-subnet-mask-vlsm/>

[2] <https://datatracker.ietf.org/doc/html/rfc1878>
