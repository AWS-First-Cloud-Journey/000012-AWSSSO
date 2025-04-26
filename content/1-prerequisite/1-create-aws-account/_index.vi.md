+++
title = "Tạo AWS Account trong AWS Organizations"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

#### Thiết lập AWS Account

#### Lựa chọn AWS Account cho bài thực hành

**ℹ️ Thông tin:** Để thực hiện workshop này, bạn cần một AWS account độc lập chưa tham gia vào AWS Organizations. AWS IAM Identity Center yêu cầu một tài khoản độc lập để thiết lập làm Management Account.

#### Sử dụng AWS account hiện có

**ℹ️ Thông tin:** Nếu bạn đang sử dụng một tài khoản hiện có, dù là tài khoản cá nhân hay tài khoản công ty, hãy đảm bảo bạn hiểu rõ các tác động và chính sách của tổ chức liên quan đến việc cung cấp tài nguyên trong tài khoản này.

**💡 Pro Tip:** Nếu bạn đã có AWS account không thuộc AWS Organizations và đang sử dụng IAM User hoặc IAM Role với quyền Administrator, bạn có thể bỏ qua phần còn lại của nhiệm vụ này và chuyển sang nhiệm vụ tiếp theo.

#### Tạo AWS account mới

Nếu bạn chưa có AWS account, bạn có thể tạo AWS account của riêng mình [tại đây](https://portal.aws.amazon.com/billing/signup). Một phương thức thanh toán, thường là thẻ tín dụng, sẽ cần thiết để kích hoạt tài khoản cho các bài thực hành này. Quy trình đăng ký bao gồm việc nhận cuộc gọi điện thoại và nhập mã xác minh bằng bàn phím điện thoại.

**⚠️ Warning:** Nếu bạn hiện đang đăng nhập vào AWS Management Console, bạn sẽ cần đăng xuất trước khi [nhấp vào đây](https://portal.aws.amazon.com/billing/signup) để tạo AWS account mới.

#### Chuẩn bị IAM User cho bài thực hành

**🔒 Security Note:** Việc hạn chế nghiêm ngặt việc sử dụng tài khoản root mặc định đi kèm với mỗi AWS account được coi là best practice theo nguyên tắc least privilege. Nếu bạn có AWS account nhưng không có IAM User hoặc Role để làm việc, hãy làm theo các bước dưới đây để chuẩn bị cho bài thực hành.

1. Đăng nhập vào AWS account của bạn với tài khoản root.
2. Truy cập AWS IAM console và tạo user mới.
3. Nhập tên cho user của bạn (ví dụ: admin) và chọn "AWS Management Console access", sau đó nhập mật khẩu mạnh.
4. Nhấp vào **Next: Permissions** để tiếp tục bước tiếp theo.

![3.4.11](/images/0001/0001.png)

5. Nhấp vào **Attach existing policies directly** và chọn **AdministratorAccess**.

![3.4.11](/images/0001/0002.png)

6. Nhấp vào **Next: Tags**.
7. Nhấp vào **Next: Review**.
8. Nhấp vào **Create User**.
9. Nhấp vào liên kết **Send email** để nhận đường dẫn đăng nhập duy nhất cho tài khoản của bạn.

**💡 Pro Tip:** Khi thiết lập IAM User với quyền Administrator, hãy đảm bảo bạn lưu trữ thông tin đăng nhập một cách an toàn và kích hoạt xác thực đa yếu tố (MFA) để tăng cường bảo mật cho tài khoản của bạn. MFA là một lớp bảo mật bổ sung quan trọng trong mô hình Zero Trust.

**🔒 Security Note:** Trong môi trường sản xuất thực tế, bạn nên áp dụng nguyên tắc least privilege bằng cách chỉ cấp quyền tối thiểu cần thiết cho mỗi IAM User thay vì cấp quyền AdministratorAccess. Tuy nhiên, cho mục đích của workshop này, quyền Administrator là cần thiết để thiết lập AWS IAM Identity Center.
