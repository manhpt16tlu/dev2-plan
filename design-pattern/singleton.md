- [1. Khái niệm](#1-khái-niệm)
- [2. Cấu trúc](#2-cấu-trúc)
- [3. Thực hành](#3-thực-hành)
- [4. Kết luận](#4-kết-luận)

# 1. Khái niệm

- Singleton là một pattern thuộc nhóm Creational Patterns. Pattern này đảm bảo rằng một class chỉ có duy nhất một instance trong suốt vòng đời của ứng dụng.
- Điều này hữu ích khi cần một trạng thái hoặc tài nguyên dùng chung mà không muốn tạo nhiều bản sao.
  - Quản lý cấu hình hệ thống
  - Quản lý kết nối CSDL: Tránh mở nhiều kết nối không cần thiết, tiết kiệm tài nguyên.
  - Ghi log: Ghi nhật ký ứng dụng từ nhiều nơi nhưng chỉ dùng một instance duy nhất.

# 2. Cấu trúc

![alt](/design-pattern/img/Singleton.png)

- Tạo một biến static để lưu trữ instance duy nhất của 1 lớp
- Ẩn contractor để ngăn việc tạo instance từ bên ngoài class
- Tạo một static method để trả về instance duy nhất

# 3. Thực hành

![Alt](/design-pattern/img/2025-03-09_173547.png)

==> Dễ triển khai, nhưng không an toàn khi chạy đa luồng. Nếu hai thread cùng gọi `GetInstance()` cùng lúc, có thể tạo ra hai instance riêng biệt.

![alt](/design-pattern/img/2025-03-09_174350.png)

==> An toàn với đa luồng nhưng ảnh hưởng hiệu suất do dùng lock

![alt](/design-pattern/img/2025-03-09_174537.png)

==> Dùng lazy là cách tối ưu nhất để triển khai singleton trong c#

![alt](/design-pattern/img/2025-03-09_175103.png)

# 4. Kết luận

- Ưu điểm:
  - Tiết kiệm tài nguyên, tối ưu hiệu suất
  - Kiểm soát trạng thái global ==> Các phần khác nhau của ứng dụng có thể truy cập vào cùng một cấu hình mà không cần khởi tạo lại.
- Nhược điểm:
  - Gây khó khăn trong Unit Testing ==> Singleton giữ nguyên trạng thái trong suốt vòng đời ứng dụng, làm cho việc mock và kiểm thử khó khăn. Nếu một test case thay đổi trạng thái của Singleton, các test khác có thể bị ảnh hưởng.
  - Nếu Singleton quản lý quá nhiều logic ==> Vi phạm nguyên tắc Single Responsibility Principle ==> khó bảo trì
