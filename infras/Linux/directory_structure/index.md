# LINUX DIRECTORY STRUCTURE

Trong hệ điều hành Linux, thư mục gốc (`/`) chứa toàn bộ các thư mục con cấu thành hệ thống. Mỗi thư mục có một chức năng cụ thể. Dưới đây là một số thư mục quan trọng và chức năng của chúng:

- **`/` (Thư mục gốc)**  
  Đây là thư mục gốc của toàn bộ hệ thống. Tất cả các tập tin và thư mục khác đều nằm dưới `/`. Không giống như Windows với ổ đĩa C, D, mọi thứ trong Linux đều bắt đầu từ `/`.

- **`/bin` (Binaries)**  
  Chứa các file thực thi cần thiết để khởi động hệ thống và sử dụng cho các hoạt động cơ bản của hệ thống. Ví dụ: các lệnh như `ls`, `cat`, `cp`, `mv` đều nằm trong `/bin`.

- **`/boot`**  
  Chứa các file cần thiết để khởi động hệ điều hành, bao gồm kernel (hạt nhân của hệ điều hành) và boot loader (GRUB). Ví dụ: file `vmlinuz`, `initrd.img`.

- **`/dev` (Devices)**  
  Chứa các tệp đại diện cho các thiết bị phần cứng trên hệ thống. Ví dụ: ổ cứng được biểu diễn dưới dạng các file như `/dev/sda`, `/dev/sdb`, các thiết bị đầu cuối như `/dev/tty`.

- **`/etc` (Configuration Files)**  
  Chứa các file cấu hình của hệ thống và các ứng dụng. Đây là nơi lưu trữ cấu hình của hệ điều hành, chẳng hạn như file `passwd`, `hosts`, `resolv.conf`, `fstab`, v.v.

- **`/home`**  
  Chứa các thư mục cá nhân của mỗi người dùng. Mỗi tài khoản người dùng sẽ có một thư mục riêng trong `/home`, ví dụ `/home/john` cho người dùng `john`. Các tệp và tài liệu cá nhân của người dùng được lưu ở đây.

- **`/lib`**  
  Chứa các thư viện chia sẻ cần thiết cho các file thực thi trong `/bin` và `/sbin`. Ví dụ: các thư viện `glibc`.

- **`/media`**  
  Thư mục này thường được sử dụng để tự động gắn kết (mount) các thiết bị lưu trữ bên ngoài như USB, CD-ROM khi chúng được kết nối.

- **`/mnt`**  
  Thư mục này thường được sử dụng cho các gắn kết tạm thời (manual mount) của các hệ thống tập tin khác, ví dụ khi gắn kết một ổ đĩa mạng hoặc một hệ thống file từ máy khác.

- **`/opt`**  
  Chứa các ứng dụng bên thứ ba được cài đặt theo gói (packages), không phải mặc định của hệ thống. Các ứng dụng lớn, độc lập thường được cài ở đây, chẳng hạn như `google/chrome`, `vscode`.

- **`/proc`**  
  Thư mục ảo chứa các thông tin về tiến trình đang chạy và hệ thống. Nó không lưu trữ dữ liệu thực mà chỉ là các file ảo cung cấp thông tin về trạng thái của hệ thống, như `cpuinfo`, `meminfo`, v.v.

- **`/root`**  
  Thư mục chính (home directory) của người dùng `root` (quản trị viên của hệ thống). Đây là thư mục riêng của root thay vì nằm trong `/home`.

- **`/run`**  
  Chứa các tệp chạy tạm thời (runtime) như PID, socket, lock của hệ thống và ứng dụng. Các dữ liệu trong `/run` thường không được lưu lại sau khi hệ thống khởi động lại.

- **`/sbin` (System Binaries)**  
  Chứa các chương trình hệ thống mà chỉ có quyền root hoặc quản trị viên mới có quyền chạy. Ví dụ: `fdisk`, `mkfs`, `reboot`, `ifconfig`.

- **`/srv`**  
  Chứa dữ liệu liên quan đến các dịch vụ mà máy chủ cung cấp. Ví dụ: dữ liệu trang web được phục vụ bởi HTTPD, dữ liệu FTP server, v.v.

- **`/sys`**  
  Giống như `/proc`, đây là thư mục ảo chứa thông tin về các thiết bị phần cứng và driver của hệ thống.

- **`/tmp` (Temporary Files)**  
  Chứa các file tạm thời được tạo ra bởi người dùng hoặc ứng dụng. Các file này thường bị xóa tự động sau khi hệ thống khởi động lại hoặc sau một khoảng thời gian.

- **`/usr` (User System Resources)**  
  Chứa các file nhị phân, thư viện và tài liệu dùng chung bởi người dùng và hệ thống. Các thư mục con quan trọng của `/usr` bao gồm:
  - `/usr/bin`: chứa các file thực thi cho người dùng.
  - `/usr/sbin`: chứa các file thực thi cho quản trị viên hệ thống.
  - `/usr/lib`: chứa các thư viện dùng chung.
  - `/usr/local`: chứa các phần mềm cài đặt thủ công từ nguồn mà không thông qua quản lý gói của hệ thống.

- **`/var` (Variable Files)**  
  Chứa các file có dữ liệu thay đổi thường xuyên trong quá trình hoạt động của hệ thống. Ví dụ: file log của ứng dụng trong `/var/log`, file tạm của các dịch vụ như web server trong `/var/www`, ...

Cấu trúc này giúp tổ chức hệ thống file một cách rõ ràng, dễ quản lý và duy trì.
