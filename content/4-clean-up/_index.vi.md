+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-14T22:33:19+07:00
weight = 5
chapter = false
pre = "<b>4. </b>"
+++

#### Dọn dẹp tài nguyên sau bài Lab

#### Mục đích
Hướng dẫn này giúp bạn dọn dẹp các tài nguyên được tạo trong quá trình thực hiện bài lab để tránh việc phát sinh chi phí không mong muốn và đảm bảo môi trường AWS được duy trì sạch sẽ.

#### Các bước thực hiện

#### 1. Truy cập vào **AWS SSO Management Console**
- Truy cập vào bảng điều khiển AWS Single Sign-On (SSO) bằng cách truy cập vào đường dẫn sau: [AWS SSO Console](https://console.aws.amazon.com/singlesignon).

#### 2. Xóa các **Groups** đã tạo
- Truy cập vào mục **Groups**.
- Chọn các group liên quan tới bài lab bằng cách tick vào checkbox tương ứng.
- Nhấn vào **Delete groups** để bắt đầu quá trình xóa.
- Trong hộp thoại **Delete groups**, nhập `DELETE` vào ô xác nhận và nhấn **Delete groups** để hoàn tất.

#### 3. Xóa các **Users** liên quan
- Truy cập vào mục **Users**.
- Chọn các user liên quan tới bài lab bằng cách tick vào checkbox tương ứng.
- Nhấn vào **Delete users** để bắt đầu quá trình xóa.
- Trong hộp thoại **Delete users**, nhập `DELETE` vào ô xác nhận và nhấn **Delete users** để hoàn tất.

#### 4. Gỡ bỏ quyền truy cập từ các tài khoản AWS
- Chuyển đến mục **AWS Accounts**.
- Chọn tên của một tài khoản AWS mà bạn muốn xóa quyền.
- Tại màn hình quản lý tài khoản, nhấp vào **Remove access** để xóa bỏ tất cả các quyền truy cập của tài khoản.
- Lặp lại quy trình này cho các tài khoản khác mà bạn muốn gỡ quyền truy cập.

![RemoveAccess](../../../images/3/3_RemoveAccess.png?width=90pc)

#### 5. Xóa các **Permission Sets**
- Chuyển đến mục **AWS Accounts** và chọn tab **Permission sets**.
- Chọn các permission sets liên quan đến bài lab này.
- Nhấn **Delete**.
- Trong hộp thoại xác nhận, nhập tên của **Permission Set** vào ô trống và nhấn **Delete** để hoàn tất.

::: note
**Lưu ý**: Hãy sao lưu dữ liệu nếu bạn cần sử dụng chúng trong tương lai. Việc xóa tài khoản sẽ khiến tất cả tài nguyên và dữ liệu thuộc tài khoản đó bị xóa vĩnh viễn và không thể khôi phục.
:::

#### 6. Xóa các **Tài khoản AWS**
- Bạn có thể giữ các tài khoản này để sử dụng cho các bài lab tiếp theo. Nếu không, làm theo các bước sau để xóa tài khoản:
  - Đăng nhập vào tài khoản bằng **Root User**:
    - Truy cập trang đăng nhập bảng điều khiển AWS tại [https://console.aws.amazon.com/](https://console.aws.amazon.com/).
    - Chọn đăng nhập bằng **Root user** và nhập email của tài khoản bạn muốn xóa (Ví dụ: `example+lab12Logging@amazon.com.vn`).
    - Vượt qua Security Check và chọn **Forgot Password?**.
    
    ![ForgotPassword](../../../images/3/3_ForgotPassword.png?width=90pc)

  - AWS sẽ gửi email xác nhận việc đặt lại mật khẩu về địa chỉ email đăng ký.
  - Đặt mật khẩu mới và đăng nhập lại bằng root user.
  
- Sau khi đăng nhập, chọn **My Account** từ menu ở góc trên bên phải.
- Cuộn xuống cuối trang và nhấp vào **Close Account**.
- Tick chọn các ô xác nhận và nhấn **Close Account** để hoàn tất việc xóa tài khoản.

::: info
**Lưu ý**: Khi bạn tạo mới một tài khoản AWS trong **AWS Organization**, một mật khẩu ngẫu nhiên sẽ được tự động tạo cho root user của tài khoản này. Nếu bạn không có quyền truy cập root user, bạn cần thực hiện quy trình **Forgot Password** để thiết lập lại mật khẩu.
:::

#### Kết luận
Hướng dẫn này giúp bạn dọn dẹp tất cả tài nguyên, nhóm, người dùng và tài khoản AWS liên quan đến bài lab. Việc thực hiện quy trình dọn dẹp thường xuyên là rất quan trọng để đảm bảo an ninh và tối ưu chi phí trong môi trường AWS của bạn.
