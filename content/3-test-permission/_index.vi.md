+++
title = "Kiểm tra "
date = 2021-06-14T22:33:19+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Truy cập vào Tài khoản AWS trong AWS Organizations qua AWS SSO User

Ở phần này, bạn sẽ thử truy cập vào các tài khoản AWS trong AWS Organizations thông qua AWS SSO User. Sau đó, bạn có thể tiến hành dọn dẹp tài nguyên nếu bạn không cần đến chúng nữa.

#### Kiểm tra kết quả

Bạn sẽ thử truy cập vào các tài khoản AWS trong AWS Organizations thông qua AWS SSO User:

1. Mở trình duyệt của bạn trong chế độ ẩn danh và truy cập đường dẫn **User portal URL** bạn đã lưu ở phần trước.

![AddUserGroups](../../../images/2/2_AddUserComplete.png?width=90pc)

Hoặc, nếu bạn đã lưu trữ **User portal URL** khi **set password**:

![AWS Account](/images/9/0001.png?featherlight=false&width=90pc)

2. Trong **User Portal**, nhập tên người dùng và mật khẩu đã lưu để đăng nhập.

3. Nếu bạn truy cập vào AWS SSO User lần đầu tiên, bạn sẽ phải thay đổi mật khẩu đầu tiên như bạn đã thiết lập ở phần trước. Nhập mật khẩu mới theo hướng dẫn và chọn **Set new password**.

![AWS Account](/images/9/0002.png?featherlight=false&width=90pc)

4. Bạn sẽ được chọn tài khoản AWS và quyền truy cập đã được thiết lập ở phần trước. Ví dụ: hình dưới thể hiện tài khoản và quyền truy cập mà Security-User có thể sử dụng. Nếu bạn đăng nhập vào Super-User, bạn sẽ có quyền truy cập **AdministratorAccess** cho mỗi tài khoản.

![AWS Account](/images/9/0003.png?featherlight=false&width=90pc)

![AWS Account](/images/9/0004.png?featherlight=false&width=90pc)

5. Chọn **Management console** để truy cập bảng điều khiển AWS của tài khoản **Security**.

![AWS Account](/images/9/0004.png?featherlight=false&width=90pc)

6. Chúc mừng, bạn đã truy cập thành công vào tài khoản.

![AWS Account](/images/9/0005.png?featherlight=false&width=90pc)

7. Đối với **CLI**, bạn có thể chọn **Command line or programmatic access**. Hiển thị hướng dẫn cấu hình SSO.

![AWS Account](/images/9/0006.png?featherlight=false&width=90pc)

8. Mở cửa sổ dòng lệnh (CMD) hoặc PowerShell theo hệ điều hành để cấu hình.

![AWS Account](/images/9/0007.png?featherlight=false&width=90pc)
