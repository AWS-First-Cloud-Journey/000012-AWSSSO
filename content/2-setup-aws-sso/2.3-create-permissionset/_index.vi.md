+++
title = "Tạo Permission Set"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Tạo Permission Set

**Permission Set** xác định khả năng truy cập mà **Người dùng (User)** và **Nhóm (Group)** có đối với các tài khoản AWS trong **AWS Organization**. Các Permission Set được lưu trữ trong AWS SSO và được cung cấp cho tài khoản AWS dưới dạng IAM roles. Bạn có thể gán nhiều quyền cho một User hoặc Group, giúp đơn giản hóa việc quản lý truy cập trên nhiều tài khoản trong tổ chức của bạn.

#### Các bước thực hiện

#### Bước 1: Mở AWS SSO Console
1. Truy cập **AWS SSO Console**.
2. Chọn **AWS accounts** ở thanh điều hướng bên trái.
3. Chuyển sang tab **Permission Sets**.
4. Chọn **Create permission set** để bắt đầu tạo bộ quyền mới.

![AWS SSO Console](/images/7/0001.png?featherlight=false&width=90pc)

#### Bước 2: Chọn loại Permission Set
1. Tại trang **Create new permission set**, chọn **Permission set type**.

![Permission Set Type](/images/7/0002.png?featherlight=false&width=90pc)

#### Bước 3: Chọn chính sách quyền cho Permission Set
1. Chọn **AdministratorAccess** để cung cấp quyền truy cập đầy đủ vào tất cả các tài nguyên và dịch vụ AWS.
   
![Chọn Administrator Access](/images/7/0003.png?featherlight=false&width=90pc)

#### Bước 4: Đặt tên cho Permission Set
1. Nhập tên cho Permission Set là **AdministratorAccess**.
2. Chọn **Next** để tiếp tục.

![Đặt tên Permission Set](/images/7/0004.png?featherlight=false&width=90pc)

#### Bước 5: Xác nhận và tạo Permission Set
1. Xem lại thông tin chi tiết của Permission Set vừa thiết lập.
2. Chọn **Create** để tạo mới Permission Set này.

![Xác nhận tạo Permission Set](/images/7/0005.png?featherlight=false&width=90pc)

#### Bước 6: Hoàn thành tạo Permission Set
1. Bạn sẽ thấy thông báo thành công khi Permission Set đã được tạo.

![Hoàn thành tạo Permission Set](/images/7/0006.png?featherlight=false&width=90pc)

#### Bước 7: Tạo thêm Permission Set với quyền khác
1. Lặp lại các bước trên để thiết lập một Permission Set với quyền **SecurityAudit** nhằm cung cấp quyền chỉ đọc cho tài khoản AWS.
2. Sau khi hoàn thành, bạn sẽ có kết quả tương tự như hình dưới đây.

![Kết quả tạo Permission Set](/images/7/0007.png?featherlight=false&width=90pc)

#### Kết luận
- Bạn đã hoàn thành việc tạo Permission Set với hai loại quyền khác nhau:
  - **AdministratorAccess**: Cung cấp quyền quản trị đầy đủ.
  - **SecurityAudit**: Cung cấp quyền đọc các tài nguyên trong tài khoản để giám sát và kiểm tra bảo mật.

#### Chú ý
- Hãy đảm bảo rằng bạn chỉ cung cấp quyền **AdministratorAccess** cho các tài khoản hoặc người dùng cần thiết để tránh rủi ro bảo mật.
- Với các tài khoản hoặc nhóm khác, sử dụng quyền **SecurityAudit** để thực hiện giám sát mà không ảnh hưởng đến cấu hình tài nguyên.

