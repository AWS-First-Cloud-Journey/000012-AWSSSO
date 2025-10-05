+++
title = "Điều kiện tiên quyết cho IAM Identity Center"
date = 2025
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

#### Điều kiện tiên quyết cho IAM Identity Center

**ℹ️ Thông tin:** Bạn có thể bỏ qua phần này nếu bạn đã kích hoạt IAM Identity Center trong AWS Account mà bạn đang sử dụng cho Workshop này.

#### Yêu cầu cơ bản

Trước khi thiết lập IAM Identity Center, bạn cần:

1. Có một AWS account với quyền Administrator. Nếu bạn chưa có, hãy tạo một tài khoản ngay bây giờ.

2. Thiết lập dịch vụ AWS Organizations và kích hoạt tính năng "All features". Để biết thêm thông tin về cài đặt này, xem "Enabling All Features in Your Organization" trong AWS Organizations User Guide.

#### Kích hoạt AWS Organizations

**ℹ️ Thông tin:** AWS Organizations là dịch vụ quản lý tài khoản cho phép bạn hợp nhất nhiều AWS accounts vào một tổ chức do bạn tạo và quản lý tập trung. Đây là điều kiện tiên quyết để sử dụng IAM Identity Center.

1. Trong AWS Management Console, ở góc trên bên trái cạnh Services, nhấp vào ô tìm kiếm và nhập "AWS Organizations", sau đó chọn dịch vụ này.

2. Nhấp vào **Create Organization**. Theo mặc định, tổ chức được tạo với tất cả các tính năng được kích hoạt.

![3.4.11](/images/0001/image05.png)

3. Tổ chức được tạo và trang AWS accounts xuất hiện. Tài khoản duy nhất hiện có là management account của bạn, và hiện đang nằm dưới root organizational unit (OU).

**💡 Pro Tip:** AWS Organizations cho phép bạn quản lý tập trung nhiều AWS accounts, giúp đơn giản hóa việc quản lý hóa đơn, kiểm soát truy cập và tuân thủ chính sách bảo mật. Bạn nên thiết kế cấu trúc OU phù hợp với mô hình tổ chức của bạn để tối ưu hóa việc quản lý quyền truy cập.

#### Kích hoạt IAM Identity Center

**ℹ️ Thông tin:** IAM Identity Center (trước đây là AWS SSO) là dịch vụ quản lý định danh và quyền truy cập tập trung cho AWS accounts và ứng dụng cloud. Dịch vụ này giúp đơn giản hóa việc quản lý quyền truy cập và cung cấp trải nghiệm đăng nhập một lần (SSO) cho người dùng.

Khi bạn mở IAM Identity Center lần đầu tiên, bạn sẽ được nhắc kích hoạt Identity Center trước khi bắt đầu quản lý nó:

1. Trong AWS Management Console, nhấp vào **Services** ở góc trên bên trái.
2. Mở IAM Identity Center console.
3. Chọn **Enable**.

![3.4.11](/images/0001/0004.png)

**ℹ️ Thông tin:** Sau khi kích hoạt, IAM Identity Center tạo một service-linked role trong tất cả các tài khoản trong tổ chức AWS Organizations. IAM Identity Center cũng tạo cùng một service-linked role trong mọi tài khoản được thêm vào tổ chức của bạn sau này. Role này cho phép IAM Identity Center truy cập vào tài nguyên của mỗi tài khoản thay mặt bạn.

#### Quản trị ủy quyền (Delegated Administration)

**🔒 Security Note:** IAM Identity Center cho phép bạn chỉ định một member account khác trong AWS Organization của bạn ngoài Organization Management Account để thực hiện các tác vụ quản trị Identity Center. Việc này giúp tuân thủ nguyên tắc least privilege bằng cách hạn chế quyền truy cập vào Management Account. Trong môi trường sản xuất, bạn nên cấu hình delegated administration để giảm thiểu rủi ro bảo mật liên quan đến việc sử dụng Management Account cho các tác vụ hàng ngày.

**💡 Pro Tip:** Khi thiết lập IAM Identity Center, hãy xem xét chiến lược định danh phù hợp với tổ chức của bạn. Bạn có thể chọn sử dụng Identity Center Directory, kết nối với Microsoft Active Directory thông qua AWS Directory Service, hoặc kết nối với nhà cung cấp định danh bên ngoài (IdP) tương thích với SAML 2.0 như Okta, Azure AD, hoặc Google Workspace.





