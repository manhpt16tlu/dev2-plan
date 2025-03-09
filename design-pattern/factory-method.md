- [1. Khái niệm](#1-khái-niệm)
- [2. Cấu trúc](#2-cấu-trúc)
- [3. Thực hành](#3-thực-hành)
- [4. Kết luận](#4-kết-luận)

# 1. Khái niệm

- factory method là một pattern trong nhóm khởi tạo
- Cung cấp một cách để khởi tạo đói tượng mà không cần chỉ rõ lớp cụ thể của đối tượng sẽ được tạo. Thay vì trực tiếp khởi tạo đối tượng bằng từ khóa `new`, factory method sẽ ủy quyền việc tạo đối tượng cho các lớp con thông qua một phương thức chung.

# 2. Cấu trúc

- bao gồm các phần chính

  - `Product`: Interface, hoặc abstract class để xác định loại đối tượng được tạo
  - `Concrete Product`: Các class implement Product
  - `Creator`: Abstract class chứa phương thức `factoryMethod()`, return 1 object kiểu Product, phương thức này sẽ được các class con override
  - `Concrete Creator`: các class con override `factoryMethod()` để return 1 đối tượng `Concrete Product`

- ![alt](/design-pattern/img/factory.png)

# 3. Thực hành

- Tạo các lớp theo đúng cấu trúc của factory pattern

  ![alt](/design-pattern/img/2025-03-09_161910.png)

- Giải thích:

  - Interface `INotification` đóng vai trò là `Product`.
  - Các lớp con `EmailNotification` và `FacebookNotification` là các `ConcreteProduct`.
  - Abtract class `NotificationFactory` là `Creator`.
  - Các lớp con `EmailNotificationFactory` và `FacebookNotificationFactory` là `ConcreteCreator`
  - Khi gọi `CreateNotification()`, Factory Method sẽ tạo ra đối tượng tương ứng mà không cần chỉ rõ lớp cụ thể.

  ![alt](/design-pattern/img/2025-03-09_162310.png)
  ![alt](/design-pattern/img/2025-03-09_162325.png)
  ![alt](/design-pattern/img/2025-03-09_162335.png)
  ![alt](/design-pattern/img/2025-03-09_162352.png)
  ![alt](/design-pattern/img/2025-03-09_163042.png)
  ![alt](/design-pattern/img/2025-03-09_163056.png)
  ![alt](/design-pattern/img/2025-03-09_163626.png)

# 4. Kết luận

- Ưu điểm:

  - Giảm sự phụ thuộc (coupling) giữa các lớp
  - Dễ mở rộng và bảo trì
  - Tránh việc sửa code logic cũ

  - Ví dụ:

  ![alt](/design-pattern/img/2025-03-09_164447.png)

  ==> phụ thuộc quá chặt trẽ vào EmailNotification, nếu muốn đổi sang dạng Notification mới, cần sửa logic service

  ![alt](/design-pattern/img/2025-03-09_164900.png)

  ==> vi phạm solid

  ![alt](/design-pattern/img/2025-03-09_165034.png)

  ==> dùng factory method pattern sẽ tốt hơn

- Nhược điểm:
  - Tăng số lượng lớp
  - Tăng độ phức tạp nếu hệ thống nhỏ
