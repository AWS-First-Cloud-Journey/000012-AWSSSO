+++
title = "Các bước chuẩn bị"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Bắt đầu

Trong phần chuẩn bị này, chúng ta sẽ tìm hiểu các điều kiện tiên quyết để thiết lập **AWS IAM Identity Center**.

#### Thiết lập AWS Account

**ℹ️ Thông tin:** Để bắt đầu, bạn cần một AWS account chưa tham gia vào AWS Organizations. AWS IAM Identity Center yêu cầu một tài khoản độc lập để thiết lập làm Management Account.

#### Điều kiện tiên quyết cho Identity Center

Để thiết lập AWS IAM Identity Center, bạn cần thực hiện các bước sau:

1. **Kích hoạt AWS Organizations**
   
   **⚠️ Warning:** Khi kích hoạt AWS Organizations, tài khoản hiện tại của bạn sẽ trở thành Management Account với quyền quản trị cao nhất. Management Account nên được bảo vệ đặc biệt và chỉ sử dụng cho mục đích quản trị.

2. **Kích hoạt AWS IAM Identity Center**
   
   **💡 Pro Tip:** AWS IAM Identity Center (trước đây là AWS SSO) cung cấp khả năng quản lý tập trung quyền truy cập vào nhiều AWS accounts và ứng dụng cloud. Sử dụng Identity Center giúp giảm thiểu việc quản lý nhiều IAM users và credentials riêng biệt.

3. **Chuẩn bị cấu trúc tổ chức**
   
   **ℹ️ Thông tin:** Trước khi triển khai, bạn nên lập kế hoạch cho cấu trúc Organizational Units (OUs) phù hợp với mô hình tổ chức của bạn để tối ưu hóa việc quản lý quyền truy cập.

**🔒 Security Note:** Việc thiết lập đúng cách AWS IAM Identity Center là nền tảng quan trọng để đảm bảo mô hình bảo mật mạnh mẽ theo nguyên tắc least privilege trong môi trường AWS của bạn. Identity Center hỗ trợ triển khai chiến lược Zero Trust bằng cách tập trung hóa quản lý định danh và quyền truy cập.
