# CREATE A SUBDOMAIN

## CẤU HÌNH

Tại Bước `Deployment Configuration`, chọn `Add new domain to an existing forest`.

- Tại `Select domain type` có hai loại bao gồm `Child Domain` và `Tree Domain`. Chọn `Child Domain`.
- Tại `Supply the credentials to perform this operation`, nhấn `Change...` sẽ hiện lên một cửa sổ yêu cầu nhập username password. Ta sẽ thực hiện đăng nhập username password của parent domain là `ZAUZOOZ`, ví dụ
    - Username: `ZAUZOOZ\Administrator`
    - Password: `ChiTuongTuMinhEmThoi`
- Sau khi nhập xong, `Parent Domain Name` sẽ xác định được parent domain. Nếu thất bại, hãy kiểm tra cấu hình DNS xem có trỏ đến Domain Controller (đang nắm parent domain) hay không.
- Tại `New domain name` nhập tên child domain, ví dụ `child`.

Các bước còn lại thực hiện tương tự như cách tạo [root forest](../Domain-Controller/index.md#2-tạo-root-forest-mới).

## KIỂM TRA CẤU HÌNH

Để kiểm tra, ta có thẻ dùng một máy tính đã join domain và ping đến domain `child.zauzooz.vn`, nếu trả về kết quả tức là settup thành công.
