+++
title = "Kiểm tra "
date = 2021-06-14T22:33:19+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

Ở phần này, bạn sẽ thử truy cập vào các tài khoản AWS trong AWS Organizations thông qua AWS SSO User. Sau đó, bạn có thể tiến hành dọn dẹp tài nguyên nếu bạn không cần đến chúng nữa.

#### Kiếm tra kết quả
Bạn sẽ thử truy cập vào các tài khoản AWS trong AWS Organizations thông qua AWS SSO User
1. Mở browser của bạn trong chế độ ẩn danh và truy cập tới đường link **User portal URL** bạn đã lưu ở phần trước.
![AddUserGroups](../../../images/2/2_AddUserComplete.png?width=90pc)
2. Trong **User Portal**, nhập username và password đã lưu để đăng nhập.
3. Nếu bạn truy cập vào AWWS SSO User lần đầu tiên, bạn sẽ phải thay đổi mật khẩu đầu tiên như bạn đã thiết lập ở phần trước. Nhập mật khẩu mới theo đúng chỉ dẫn và chọn **Set new password**.
![AddUserComplete](../../../images/3/3_NewPassword.png?width=90pc)
4. Bạn sẽ được chọn tài khoản AWS và quyền truy cập đã được thiết lập ở phần trước. (Ví dụ: hình dưới thể hiện tài khoản và quyền truy cập mà Security-User có thể sử dụng. Nếu bạn đăng nhập vào Super-User, bạn sẽ có thể quyền truy cập **AdministratorAccess** cho mỗi tài khoản)
5. Chọn **Management console** để truy cập vào bảng điều khiển AWS của tài khoản **Security**.
![Login](../../../images/3/3_Login.png?width=90pc)
6. Chúc mừng, bạn đã truy cập thành công vào tải khoản **Security** với quyền **SecurityAudit**.
![Success](../../../images/3/3_Success.png?width=90pc)
