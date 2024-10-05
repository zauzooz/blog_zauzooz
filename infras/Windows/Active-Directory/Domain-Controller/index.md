# TRIỂN KHAI DOMAIN CONTROLLER

## 1. Thiết lập Domain Controller

> Domain Controller (DC) là một máy chủ trong mạng máy tính mà có nhiệm vụ quản lý và xác thực các tài khoản người dùng và tài nguyên trong một domain. Nó là một thành phần quan trọng trong hạ tầng mạng, đặc biệt trong môi trường Windows.

> Một thiết bị có role **Actvice Directory Domain Service** là một DC.

Thực hiện từng bước một bên dưới theo thứ tự để tạo ra một Domain Controller.

Tại `Server Manager`, nhìn góc trái và chọn `Dashboard`. Tại mục `WELCOME TO SERVER MANAGER`, ta chọn mục 2 `Add role and features`.

Sau khi thực hiện `Add role and features`, `Add Roles and Feature Wizards` sẽ hiện ra. Đây là một công cụ trong hệ điều hành Windows Server giúp người dùng thêm các vai trò (`Role`) và tính năng vào máy chủ, chẳng hạn như cài đặt các dịch vụ mạng, dịch vụ web, hoặc các dịch vụ máy chủ khác.

Tại `Before You Begin`, chọn `Next >`.

Tại `Installation Type`, có hai lựa chọn: `Role-based or Feature-based installation` và `Remote Destop Service installation`. Ta click chọn `Role-based or Feature-based installation` và nhấn `Next >`.

Tại `Server Selection`, chọn mục `Select a server from the server pool`. Trong `Server Pool`, chọn tên thiết bị của máy AD, ví dụ `WIN-ABCXYZ1234` rồi nhấn `Next >`.

Tại `Server Role`, chọn hai role `Active Directory Domain Service` và `DNS Server`. Sau đó nhấn `Next >`.

Tại `Features`, ta chưa cần bổ sung tính năng nào nên ta chọn `Next >`.

Tại `DNS Server`, ta chọn `Next >`.

Tại `AD DS`, ta chọn `Next >`.

Tại `Confirmation`, đánh dấu chọn `Restart destination server automatically if required` và nhấn `Install`.

Chờ đợi cho đến khi cài đặt hoàn tất, nhấn `Close`.

## 2. Tạo Root Forest mới

Chọn vào biểu tượng ![anhdadenroiday](image.png), nhấn vào `Promote this server to a domain contoller`.

Tại bước `Deployment Configuration`, chọn mục `Add a new forest`. Tại ô nhập `Root domain name`, ta nhập tên domain mong muốn. Ví dụ `zauzooz.vn`. Sau đó nhấn `Next >`.

Tại bước `Domain Controller Options`, ta có hai ô nhập `Password` và `Confirm Password`, nhập vào chúng mật khẩu mà bạn muốn. Khi hai mật khẩu nhập vào trùng nhau nhấn `Next >`.

Tại bước con `DNS Options`, ta chọn `Next >`.

Tại bước `Additional Options`, ta nhập NetBIOS name là `ZAUZOOZ` và ta chọn `Next >`.

Tại bước `Paths`, ta giữ nguyên các cấu hình và chọn `Next >`.

Tại bước `Review Options`, ta chọn `Next >`.

Tại bước `Prerequire Checks`, chờ đợi hệ thống đã kiểm tra, nhấn `Install`.

Sau khi cài đặt hoàn tất, nhấn `Close` và chờ đợi máy khởi động lại.

