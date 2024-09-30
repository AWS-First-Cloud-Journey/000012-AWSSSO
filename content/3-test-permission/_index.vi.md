+++
title = "Kiểm tra AWS SSO User"
date = 2021-06-14T22:33:19+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Truy cập vào Tài khoản AWS trong AWS Organizations qua AWS SSO User

Ở phần này, bạn sẽ học cách truy cập vào các tài khoản AWS trong **AWS Organizations** thông qua **AWS SSO User**. Sau đó, bạn có thể tiến hành dọn dẹp tài nguyên nếu không cần đến chúng nữa.

#### Kiểm tra kết quả

Bạn sẽ thực hiện các bước sau để truy cập vào các tài khoản AWS trong **AWS Organizations** thông qua **AWS SSO User**:

1. **Mở trình duyệt ở chế độ ẩn danh** và truy cập đường dẫn **User portal URL** đã lưu khi bạn thiết lập **AWS SSO** ở phần trước.

    ![User Portal](../../../images/2/2_AddUserComplete.png?width=90pc)

    Hoặc, nếu bạn đã lưu **User portal URL** khi **cài đặt mật khẩu lần đầu**:

    ![User Portal URL](/images/9/0001.png?featherlight=false&width=90pc)

2. Trong **User Portal**, nhập **tên người dùng** và **mật khẩu** bạn đã lưu để đăng nhập.

3. Nếu đây là lần đầu bạn đăng nhập vào **AWS SSO User**, bạn sẽ cần thay đổi mật khẩu theo yêu cầu. Nhập **mật khẩu mới** theo hướng dẫn và chọn **Set new password**.

    ![Set New Password](/images/9/0002.png?featherlight=false&width=90pc)

4. Sau khi đăng nhập thành công, bạn sẽ thấy danh sách các tài khoản **AWS** và quyền truy cập tương ứng mà người dùng của bạn có thể sử dụng. Ví dụ, hình dưới đây thể hiện tài khoản và quyền truy cập mà **Security-User** có thể sử dụng. Nếu bạn đăng nhập bằng **Super-User**, bạn sẽ có quyền truy cập **AdministratorAccess** cho mỗi tài khoản.

    ![AWS Account Access](/images/9/0003.png?featherlight=false&width=90pc)

    ![AWS Account Access](/images/9/0004.png?featherlight=false&width=90pc)

5. Chọn **Management console** để truy cập bảng điều khiển **AWS Management Console** của tài khoản **Security**.

    ![Management Console Access](/images/9/0004.png?featherlight=false&width=90pc)

6. **Chúc mừng**, bạn đã truy cập thành công vào tài khoản AWS.

    ![Successful Login](/images/9/0005.png?featherlight=false&width=90pc)

7. Đối với truy cập **CLI**, bạn có thể chọn **Command line or programmatic access**. Thao tác này sẽ hiển thị các hướng dẫn cấu hình **SSO**.

    ![Command Line Access](/images/9/0006.png?featherlight=false&width=90pc)

8. Mở cửa sổ **dòng lệnh (CMD)** hoặc **PowerShell** theo hệ điều hành mà bạn đang sử dụng để cấu hình các tham số.

    ![Command Line Configuration](/images/9/0007.png?featherlight=false&width=90pc)

#### Dọn dẹp tài nguyên (Clean Up)

Sau khi hoàn thành kiểm tra, nếu bạn không cần các tài khoản hoặc quyền truy cập đã tạo, bạn có thể thực hiện các bước sau để dọn dẹp tài nguyên:

1. **Xóa người dùng AWS SSO** không còn cần thiết trong **AWS SSO Console**.
2. **Gỡ bỏ quyền truy cập** trong từng tài khoản AWS nếu không còn sử dụng.
3. **Kiểm tra và xóa các tài nguyên AWS** khác (nếu có) để đảm bảo không có tài nguyên dư thừa.

#### Kết luận

Trong phần này, bạn đã học cách truy cập vào các tài khoản trong **AWS Organizations** thông qua **AWS SSO User** và kiểm tra quyền truy cập thành công. Nếu bạn cần thêm quyền hạn hoặc gặp lỗi truy cập, hãy xem lại các **policy IAM** và thiết lập **AWS SSO** trong tài liệu AWS chính thức.

