+++
title = "Làm mới thông tin xác thực thủ công"
date = 2020
weight = 1
chapter = false
pre = "<b> 2.1 </b>"
+++

#### Cấu hình AWS CLI - Làm mới thông tin xác thực thủ công

**ℹ️ Thông tin:** Trong phần này, chúng tôi sẽ hướng dẫn bạn cách cấu hình AWS CLI theo cách thủ công để xác thực người dùng với AWS IAM Identity Center. Với phương pháp này, bạn phải làm mới thông tin xác thực tạm thời theo cách thủ công khi chúng hết hạn.

#### Điều kiện tiên quyết

1. Cài đặt AWS CLI phiên bản mới nhất. Để biết thêm thông tin, xem [Cài đặt hoặc cập nhật lên phiên bản mới nhất của AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
2. Bạn phải có quyền truy cập xác thực SSO trong IAM Identity Center.

#### Quy trình cấu hình thủ công

1. Đăng nhập vào AWS Access Portal bằng cách sử dụng URL đăng nhập được cung cấp cho tổ chức của bạn.
2. Trong tab **Accounts** hoặc bằng cách chọn biểu tượng AWS account, xác định AWS account mà bạn muốn truy cập.
3. Mở rộng account để hiển thị các IAM role có sẵn (ví dụ: AdministratorAccess, readOnly).
4. Bên cạnh IAM role mong muốn, chọn **Access keys** để lấy thông tin xác thực tạm thời.

**ℹ️ Thông tin:** AWS Access Portal là giao diện tập trung để quản lý quyền truy cập vào tất cả AWS accounts trong tổ chức của bạn thông qua IAM Identity Center.

![SSO Access Portal](/images/sso-access-portal.png)

#### Sử dụng thông tin xác thực tạm thời

Trong hộp thoại **Get credentials**, bạn có ba tùy chọn để sử dụng thông tin xác thực:

**Tùy chọn 1: Thiết lập biến môi trường AWS**
- Chọn hệ điều hành của bạn (MacOS and Linux, Windows, hoặc PowerShell)
- Sao chép các lệnh được cung cấp vào clipboard
- Dán và thực thi các lệnh trong terminal để thiết lập biến môi trường
- Các biến này sẽ ghi đè tất cả cài đặt thông tin xác thực hiện có trong phiên terminal hiện tại

**💡 Pro Tip:** Sử dụng tùy chọn này khi bạn cần nhanh chóng chuyển đổi giữa các vai trò khác nhau trong cùng một phiên làm việc.

**Tùy chọn 2: Thêm profile vào tệp AWS credentials**
- Sao chép các lệnh được cung cấp
- Dán vào tệp `~/.aws/credentials` để tạo một named profile mới
- Sử dụng profile này với tùy chọn `--profile` trong lệnh AWS CLI
- Ví dụ: `aws s3 ls --profile sso-admin-profile`

**🔒 Security Note:** Named profiles cho phép bạn duy trì nhiều bộ thông tin xác thực cùng lúc và giảm thiểu rủi ro sử dụng nhầm quyền hạn khi thực hiện các thao tác AWS CLI.

**Tùy chọn 3: Sử dụng các giá trị riêng lẻ trong AWS service client**
- Sao chép các giá trị thông tin xác thực riêng lẻ (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_SESSION_TOKEN)
- Tích hợp các giá trị này vào mã ứng dụng của bạn khi sử dụng AWS SDK

![SSO Credentials](/images/sso-credentials.png)

**⚠️ Cảnh báo:** Thông tin xác thực tạm thời có thời hạn giới hạn, thường là 1 giờ. Khi hết hạn, bạn cần lặp lại quy trình để lấy thông tin xác thực mới. Không nên lưu trữ thông tin xác thực tạm thời trong các tệp cấu hình dài hạn hoặc hệ thống kiểm soát phiên bản.

