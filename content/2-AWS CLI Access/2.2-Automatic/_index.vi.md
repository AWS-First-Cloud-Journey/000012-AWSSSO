+++
title = "Làm mới thông tin xác thực tự động"
date = 2020
weight = 2
chapter = false
pre = "<b> 2.2 </b>"
+++

#### Cấu hình AWS CLI - Làm mới thông tin xác thực tự động

**ℹ️ Thông tin:** Phần này hướng dẫn cách cấu hình AWS CLI với tính năng tự động làm mới thông tin xác thực để xác thực người dùng với AWS IAM Identity Center. Phương pháp này sử dụng chuẩn Open ID Connect (OIDC) với Device Code Authorization, cho phép bạn khởi tạo quyền truy cập trực tiếp thông qua lệnh `aws configure sso` trong AWS CLI.

#### Cấu hình hồ sơ người dùng

**ℹ️ Thông tin:** Sử dụng phương pháp tự động làm mới thông tin xác thực, chúng ta sẽ cấu hình hai hồ sơ:
- `adminUser` - Hồ sơ với quyền quản trị
- `readOnlyUser` - Hồ sơ chỉ có quyền đọc

#### Cấu hình hồ sơ adminUser

1. Mở cửa sổ terminal và chạy lệnh sau:
   ```bash
   aws configure sso --profile adminUser
   ```

2. Cung cấp tên phiên SSO:
   ```
   sso-session-adminUser
   ```

3. Nhập URL cổng truy cập AWS và chọn vùng SSO:
   ```
   us-east-1
   ```

4. Đối với phạm vi đăng ký SSO, cung cấp giá trị:
   ```
   sso:account:access
   ```

5. Một cửa sổ trình duyệt mới sẽ mở ra. Đăng nhập với tư cách adminUser và làm theo các bước xác thực.

6. Sau khi hoàn tất, kiểm tra cấu hình bằng lệnh:
   ```bash
   aws s3 ls --profile adminUser
   ```

**💡 Pro Tip:** Sử dụng hồ sơ có quyền quản trị (`adminUser`) chỉ khi cần thực hiện các thao tác yêu cầu quyền quản trị như khởi động/dừng EC2, tạo/xóa tài nguyên AWS. Điều này tuân theo nguyên tắc đặc quyền tối thiểu (least privilege principle).

#### Kiểm tra quyền adminUser

Sử dụng hồ sơ adminUser để dừng một EC2 instance:

1. Lấy ID EC2 instance từ AWS Management Console
2. Chạy lệnh sau (thay thế [instance-id] bằng ID EC2 thực tế):
   ```bash
   aws ec2 stop-instances --instance-ids [instance-id] --profile adminUser
   ```

**ℹ️ Thông tin:** Với hồ sơ adminUser, bạn có thể thực hiện các thao tác quản trị thông qua CLI tương tự như khi thực hiện thông qua AWS Management Console.

#### Cấu hình hồ sơ readOnlyUser

1. Mở cửa sổ terminal và chạy lệnh sau:
   ```bash
   aws configure sso --profile readOnlyUser
   ```

2. Cung cấp tên phiên SSO:
   ```
   sso-session-readOnlyUser
   ```

3. Nhập URL cổng truy cập AWS và chọn vùng SSO:
   ```
   us-east-1
   ```

4. Đối với phạm vi đăng ký SSO, cung cấp giá trị:
   ```
   sso:account:access
   ```

5. Làm theo các bước xác thực trong cửa sổ trình duyệt mới.

**🔒 Security Note:** Việc sử dụng hồ sơ với các quyền hạn phù hợp (ví dụ: readOnlyUser) là một phần quan trọng của mô hình bảo mật theo nguyên tắc đặc quyền tối thiểu, giúp giảm thiểu rủi ro từ việc sử dụng sai hoặc truy cập trái phép.

#### Kiểm tra quyền readOnlyUser

Thử dừng EC2 instance với hồ sơ readOnlyUser:

1. Lấy ID EC2 instance từ AWS Management Console
2. Chạy lệnh sau (thay thế [instance-id] bằng ID EC2 thực tế):
   ```bash
   aws ec2 stop-instances --instance-ids [instance-id] --profile readOnlyUser
   ```

**⚠️ Cảnh báo:** Lệnh này sẽ thất bại vì readOnlyUser không có quyền thực hiện thao tác dừng EC2. Điều này minh họa việc cấu hình phân quyền đang hoạt động chính xác, đảm bảo người dùng chỉ có thể thực hiện các hành động phù hợp với vai trò của họ.

#### Lợi ích của việc tích hợp IAM Identity Center với AWS CLI

**ℹ️ Thông tin:** Tích hợp IAM Identity Center với AWS CLI mang lại nhiều lợi ích:
- Linh hoạt chuyển đổi giữa các tài khoản và vai trò
- Không cần quản lý thủ công thông tin xác thực hoặc hồ sơ
- Tự động làm mới thông tin xác thực
- Tối ưu hóa quy trình phát triển và quản trị khi làm việc trên nhiều môi trường AWS

#### Quản lý phiên IAM Identity Center

Khi bạn đã hoàn tất việc sử dụng hồ sơ IAM Identity Center, bạn có thể:
- Không làm gì và để thông tin xác thực tạm thời AWS và thông tin xác thực IAM Identity Center tự động hết hạn
- Hoặc chạy lệnh sau để xóa ngay lập tức tất cả thông tin xác thực được lưu trong bộ nhớ cache:
   ```bash
   aws sso logout
   ```

**💡 Pro Tip:** Sử dụng lệnh `aws sso logout` khi bạn cần đảm bảo an toàn bằng cách xóa tất cả thông tin xác thực đã lưu trong bộ nhớ cache, đặc biệt là khi làm việc trên máy tính dùng chung hoặc trong môi trường nhạy cảm về bảo mật.

**ℹ️ Thông tin:** Để sử dụng lại hồ sơ IAM Identity Center sau khi đăng xuất, bạn chỉ cần chạy lệnh AWS CLI với tham số `--profile` tương ứng, và hệ thống sẽ tự động yêu cầu bạn xác thực lại.