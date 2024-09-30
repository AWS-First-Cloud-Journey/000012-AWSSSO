+++
title = "Thêm Users và Groups"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++

#### Thêm Users và Groups

Bạn cần tạo các User và Group như bảng dưới đây. User ở cột **User logon name** sẽ thuộc các Group ở cột **Group**.

| User logon name | Group |
|:---------------:|:-----:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only |

#### Tạo Group

1. **Bắt đầu tạo Group**:
   - Truy cập vào **AWS SSO Console**.
   - Trong thanh bên trái, chọn **Groups**, sau đó nhấn **Create group** để tạo các group được liệt kê trong bảng phía trên.

   ![AWS Account](/images/6/0001.png?featherlight=false&width=90pc)

2. **Điền thông tin cho Group**:
   - Tại cửa sổ tạo Group, điền tên và mô tả cho Group (VD: `AWS-Security-Admin`).
   - Nhấn **Create** để hoàn tất.

   ![AWS Account](/images/6/0002.png?featherlight=false&width=90pc)

3. **Lặp lại bước trên cho các Group khác**:
   - Tạo các Group khác theo danh sách: `AWS-Shared-Services-Admin`, `AWS-Shared-Services-Read-Only`, `AWS-Security-Read-Only`, `AWS-Logging-Admin`, `AWS-Logging-Read-Only`.

   ![AWS Account](/images/6/0003.png?featherlight=false&width=90pc)

#### Thêm User

1. **Truy cập AWS SSO Console**:
   - Chọn **Users** từ thanh điều hướng bên trái.
   - Nhấn **Add user** và cung cấp thông tin cơ bản cho User.

   ![AWS Account](/images/5/0001.png?featherlight=false&width=90pc)

2. **Điền thông tin người dùng**:
   - **Username**: Đây là tên sẽ được yêu cầu để đăng nhập vào cổng thông tin User (VD: Super-User).
   - **Password setup**:
     - Chọn cách thức gửi mật khẩu cho User:
       - **Send an email to the user with password setup instructions**: Gửi email chứa hướng dẫn thiết lập mật khẩu.
       - **Generate a one-time password**: Tạo mật khẩu tạm thời mà bạn có thể chia sẻ với User.
   - **Email address**: Nhập email của User.
   - **Confirm email address**: Xác nhận email.

   ![AWS Account](/images/5/0002.png?featherlight=false&width=90pc)

3. **Đặt tên hiển thị (Display name)**:
   - Để rõ ràng, bạn có thể sử dụng tiền tố của **User logon name** làm **First name** và hậu tố làm **Last name**. Ví dụ: Đối với `Super-User`, "Super" sẽ là **First name** và "User" sẽ là **Last name**.

4. **Chọn Next** để chuyển sang bước tiếp theo.

   ![AWS Account](/images/5/0003.png?featherlight=false&width=90pc)

5. **Chọn Group**:
   - Ở bước này, bạn chọn các Group mà User sẽ được thêm vào theo bảng đã định nghĩa (VD: `AWS-Security-Read-Only` cho `Security-User`).

   ![AWS Account](/images/5/0004.png?featherlight=false&width=90pc)

6. **Hoàn tất thêm User**:
   - Nhấn **Add user** để xác nhận việc thêm User vào các Group đã chọn.

   ![AWS Account](/images/5/0005.png?featherlight=false&width=90pc)

7. **Gửi thông tin xác thực cho User**:
   - Nếu bạn chọn **Send an email to this user with password setup instructions**, AWS sẽ gửi email hướng dẫn cho User. Thực hiện theo hướng dẫn để User có thể đăng nhập và cấu hình mật khẩu lần đầu tiên.

   ![AWS Account](/images/5/0007.png?featherlight=false&width=90pc)

8. **Hoàn tất thiết lập mật khẩu**:
   - Nếu bạn tự thiết lập mật khẩu, User sẽ nhận được đường dẫn đến cổng thông tin và có thể cấu hình mật khẩu ngay khi đăng nhập lần đầu.

   ![AWS Account](/images/5/00010.png?featherlight=false&width=90pc)

9. **Lưu lại thông tin đăng nhập và mật khẩu cho User** để đảm bảo User có thể đăng nhập vào hệ thống mà không gặp trở ngại.

   ![AWS Account](/images/5/00011.png?featherlight=false&width=90pc)
