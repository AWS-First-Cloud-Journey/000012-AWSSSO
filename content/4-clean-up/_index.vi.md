+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-14T22:33:19+07:00
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

#### Dọn dẹp tài nguyên

1. Truy cập vào **AWS SSO Mangement Console**
2. **Xóa Groups**:
    - Chọn **Groups**, tick vào các group liên quan tới bài lab này, và chọn **Delete groups**.
    - Tại prompt **Delete groups**, gõ DELETE vào ô, và chọn **Delete groups**
3. **Xóa Users**: 
    - Chọn **Users**, tick vào các user liên quan tới bài lab này, và chọn **Delete users**.
    - Tại prompt **Delete users**, gõ DELETE vào ô, và chọn **Delete users**
4. **Xóa quyền truy cập** tại các tài khoản AWS:
    - Chọn **AWS Accounts** và nhấp vào tên của một tài khoản AWS.
    - Remove access với tất cả các quyền truy cập của tài khoản.
    - Lặp lại với các tài khoản đang được gán quyền truy cập cần xóa.
    ![RemoveAccess](../../../images/3/3_RemoveAccess.png?width=90pc)
5. **Xóa các Permission Sets**
    - Chọn **AWS accounts**, chọn tab **Permission sets**, và chọn các permission sets liên quan
    - Nhấn **Delete**. Tại prompt, gõ tên của permission set vào ô trống và nhấn **Delete**.

{{% notice note %}}
Lưu ý: Hãy sao lưu các dữ liệu trong các tài khoản này nếu bạn cần chúng trong tương lai vì xóa tài khoản đồng nghĩa với việc mọi tài nguyên và dữ liệu thuộc tài khoản ấy sẽ bị xóa vĩnh viễn
{{% /notice %}}

6. **Xóa các tải khoản AWS**. Tuy nhiên, Bạn có thể giữ các tài khoản này cho các phần lab tiếp theo.
    - Để xóa một tài khoản AWS, bạn cần đăng nhập vào tài khoản bằng root user
        - Truy cập vào trang đăng nhập vào bảng điều khiển AWS tại https://console.aws.amazon.com/
        - Khi trang **Sign in** hiện lên, chọn đăng nhập bằng **Root user** và nhập email của tài khoản bạn muốn xóa. (Ví dụ: example+lab12Logging@amazon.com.vn)
        - Vượt qua Security Check và chọn **Forgot Password?**
        ![ForgotPassword](../../../images/3/3_ForgotPassword.png?width=90pc)
        - AWS sẽ gửi email xác nhận quên mật khẩu vào email được đăng ký (ví dụ: nếu email của bạn là example+lab12Logging@amazon.com.vn, thì email của AWS sẽ được gửi về example@amazon.com.vn). Bạn hãy đổi mật khẩu mới qua email đó và đăng nhập vào tài khoản AWS.
    - Sau khi đăng nhập bằng root user, chọn vào tên tài khoản ở góc trên bên phải, chọn **My Account**, cuộn xuống cuối trang để thấy mục **Close Account**. Tick hết vào các ô và chọn **Close Account**

{{% notice info %}}
Khi bạn tạo mới một tài khoản AWS trong AWS Organization, AWS Organization đã tự động tạo một mật khẩu ngẫu nhiên cho root user của tài khoản ấy, và bạn không thể tiếp cận được với chúng. Do đó, bạn sẽ truy cập vào root user của tài khoản ấy bằng cách lấy lại mật khẩu đã quên (*forgot password*)
{{% /notice %}}


