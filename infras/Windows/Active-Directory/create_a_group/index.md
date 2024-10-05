# TẠO MỘT GROUP TRONG MỘT MẠNG TÊN MIỀN

## TẠO MỘT NHÓM

Đầu tiên mở `Server Manager`, phía trên cùng bên trái chọn `Tools > Active Directory User and Computers`.

Ví dụ tên miền là `zauzooz.vn`, có nhiều nhóm đối tượng (`container`) bao gồm: `Builtin`, `Computers`, `Domain Controllers`, `ForeignSecurityPrincipals`, `Managed Service Account` và `Users`.

```
zauzooz.vn
|-- Builtin
|-- Computers
|-- Domain Controllers
|-- ForeignSecurityPrincipals
|-- Managed Service Account
|-- Users
```

Để tạo hai Groups là `Dev` và `Red`, nhấn vào container `User`, nhấn chuột phải vào vùng trống chọn `New > Groups`, một cửa sổ `New Object - Group` hiện lên để ta nhập thông tin:

- Tại `Group name`, ta nhập tên của group, ví dụ `Dev`.
- Tại `Group scope` có ba option bao gồm `Domain local`, `Global` và `Universial`. Chọn loại mà bạn muốn, ví dụ chọn `Global` (mặc định).
- Tại `Group Type` có hai option là `Security` và `Distribution`, chọn loại mà bạn mong muốn, ví dụ chọn `Security` (mặc định).

Như vậy một Group đã được tạo.

## GÁN MỘT TÀI NGUYÊN TRUY CẬP CỦA MỘT NHÓM

Giả sử ta tạo một thư mục `ZAUZOOZ` bên trong ổ đĩa `C`, bên trong thư mục này chứa ba thư mục con bao gồm `Dev`, `Red` và `Global`:

```
C:
|-- ZAUZOOZ
|   |-- Dev
|   |-- Global
|   |-- Red
```

Ta có quyền truy cập mỗi Group đến một Folder được thể hiện ở bảng bên dưới, với dâu 'x' là có thể truy cập đến:

||`Dev` Folder|`Global` Folder|`Red` Folder|
|:--|:-:|:-:|:-|
|`Dev` Group|x|x||
|`Red` Group||x|x|

### Cách 1: Gán thủ công

Tại mỗi thư mục, ví dụ `Dev` ta nhấn chuột phải nào nó, sau đó chọn `Properties`. Một cửa sổ `Dev Properties` sẽ hiện ra.

Ta chọn tab `Security` ta nhấn `Edit...`. Một cửa sổ `Permission of Dev` sẽ hiện ra.

Ta nhấn `Add..`, một cửa sổ `Select Users, Computers, Service Accounts, or Groups` sẽ hiện ra.

Ta nhấn `Advanced...`, cửa sổ `Select Users, Computers, Service Accounts, or Groups` sẽ được mở rộng. Nhấn `Find Now`. Tìm và nhấn Group `Dev` rồi nhấn `OK`.

Sau đó cửa sổ `Select Users, Computers, Service Accounts, or Groups` sẽ thu gọn lại, ở mục `Enter the object names to select` có hiện `Dev` mà ta đã chọn. Nhấn `OK`.

Tiếp theo ta lại trở về với cửa sổ `Permission of Dev`, ta nhấn `Apply` rồi nhấn `OK` để hoàn tất.

### Cách 2: Dùng Powershell để tự động hóa


