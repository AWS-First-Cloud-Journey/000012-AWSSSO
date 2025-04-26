+++
title = "Truy cập AWS CLI"
date = 2020
weight = 2
chapter = false
pre = "<b> 2. </b>"
+++

#### Truy cập AWS CLI

**ℹ️ Thông tin:** AWS Command Line Interface (CLI) cung cấp khả năng tương tác với các dịch vụ AWS thông qua dòng lệnh. Khi sử dụng IAM Identity Center, bạn có thể xác thực và truy cập các tài nguyên AWS một cách an toàn trên nhiều tài khoản.

#### Tổng quan về xác thực AWS CLI với IAM Identity Center

Khi sử dụng AWS IAM Identity Center, bạn có thể xác thực vào AWS CLI bằng:
- Thư mục tích hợp của IAM Identity Center
- Nhà cung cấp danh tính bên ngoài được kết nối với IAM Identity Center

Sau khi xác thực, IAM Identity Center sẽ ánh xạ thông tin đăng nhập của bạn tới IAM role tương ứng để thực thi các lệnh AWS CLI với quyền hạn phù hợp.

#### Phương pháp làm mới thông tin xác thực

**ℹ️ Thông tin:** Có hai phương pháp chính để lấy và làm mới thông tin xác thực tạm thời cho người dùng IAM Identity Center:

#### 1. Làm mới thông tin xác thực thủ công

Phương pháp này cho phép bạn lấy thông tin xác thực tạm thời cho một IAM role cụ thể liên kết với permission set trong một AWS account. Quy trình thực hiện:

1. Đăng nhập vào AWS access portal
2. Chọn AWS account và permission set cần truy cập
3. Sao chép các lệnh AWS CLI được cung cấp
4. Dán và thực thi các lệnh trong terminal để thiết lập thông tin xác thực

**⚠️ Cảnh báo:** Thông tin xác thực tạm thời có thời hạn giới hạn (thường là 1 giờ). Bạn cần lặp lại quy trình này khi thông tin xác thực hết hạn.

#### 2. Làm mới thông tin xác thực tự động (khuyến nghị)

**💡 Pro Tip:** Phương pháp này sử dụng tiêu chuẩn Open ID Connect (OIDC) với Device Code Authorization, cung cấp trải nghiệm xác thực liền mạch và an toàn hơn.

Quy trình thực hiện:
1. Cấu hình AWS CLI với lệnh `aws configure sso`
2. Cung cấp URL của IAM Identity Center và AWS Region
3. Xác thực thông qua trình duyệt web
4. Chọn AWS account và IAM role để truy cập
5. AWS CLI sẽ tự động làm mới thông tin xác thực khi cần

**🔒 Security Note:** Phương pháp làm mới tự động không chỉ cải thiện trải nghiệm người dùng mà còn tăng cường bảo mật bằng cách:
- Loại bỏ nhu cầu sao chép/dán thông tin xác thực nhạy cảm
- Tự động quản lý vòng đời thông tin xác thực
- Hỗ trợ xác thực đa yếu tố (MFA) tích hợp
- Tuân thủ các nguyên tắc Zero Trust với phiên truy cập ngắn hạn

**ℹ️ Thông tin:** Từ AWS CLI v2.9.0 trở lên, bạn có thể sử dụng tệp cấu hình SSO (`~/.aws/config`) để lưu trữ nhiều profile cho các AWS account và permission set khác nhau, cho phép chuyển đổi nhanh chóng giữa các vai trò khác nhau.