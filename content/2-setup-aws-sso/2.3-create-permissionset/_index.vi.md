+++
title = "Tạo Permission Set"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Permission Set

**Permission Set** xác định khả năng truy cập mà User và Group có đối với các tài khoản AWS trong AWS Organization. Các bộ quyền được lưu trữ trong AWS SSO và được cung cấp cho tài khoản AWS dưới dạng IAM roles. Bạn có thể gán nhiều quyền cho một User.

1. Mở AWS SSO Console.
   - Chọn *AWS accounts* ở thanh bên trái.
   - Chọn tab **Permission Sets**.
   - Chọn **Create permission set**.

![AWS Account](/images/7/0001.png?featherlight=false&width=90pc)

2. Tại trang *Create new permission set*:
   - Chọn **Permission set type**.

![AWS Account](/images/7/0002.png?featherlight=false&width=90pc)

3. Chọn **AdministratorAccess** để cung cấp quyền truy cập đầy đủ vào các tài nguyên và dịch vụ AWS.

![AWS Account](/images/7/0003.png?featherlight=false&width=90pc)

4. Nhập **AdministratorAccess** và chọn **Next**.

![AWS Account](/images/7/0004.png?featherlight=false&width=90pc)

5. Kiểm tra và chọn **Create**.

![AWS Account](/images/7/0005.png?featherlight=false&width=90pc)

6. Hoàn thành tạo **Permission set**.

![AWS Account](/images/7/0006.png?featherlight=false&width=90pc)

7. Lặp lại các bước trên để thiết lập Permission Set với quyền **SecurityAudit**. Bạn sẽ có kết quả như hình dưới đây.

![AWS Account](/images/7/0007.png?featherlight=false&width=90pc)
