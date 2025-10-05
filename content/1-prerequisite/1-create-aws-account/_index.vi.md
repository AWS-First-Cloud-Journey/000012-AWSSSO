+++
title = "Tạo AWS Account trong AWS Organizations"
date = 2025
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

#### Thiết lập AWS Account

#### Lựa chọn AWS Account cho bài thực hành

**ℹ️ Thông tin:** Để thực hiện workshop này, bạn cần một AWS account độc lập chưa tham gia vào AWS Organizations. AWS IAM Identity Center (trước đây là AWS Single Sign-On) yêu cầu một tài khoản độc lập để thiết lập làm Management Account.

#### Sử dụng AWS account hiện có

**ℹ️ Thông tin:** Nếu bạn đang sử dụng một tài khoản hiện có, dù là tài khoản cá nhân hay tài khoản công ty, hãy đảm bảo bạn hiểu rõ các tác động và chính sách của tổ chức liên quan đến việc cung cấp tài nguyên trong tài khoản này.

**💡 Pro Tip:** Nếu bạn đã có AWS account không thuộc AWS Organizations và đang sử dụng IAM User hoặc IAM Role với quyền Administrator, bạn có thể bỏ qua phần còn lại của nhiệm vụ này và chuyển sang nhiệm vụ tiếp theo.

**ℹ️ Thông tin 2025:** AWS IAM Identity Center hiện hỗ trợ tích hợp với Amazon Q Developer, Amazon QuickSight, và các dịch vụ AWS hiện đại khác. Dịch vụ hoàn toàn miễn phí, bạn chỉ trả phí cho các tài nguyên AWS cơ bản bên dưới.

#### Tạo AWS account mới

Nếu bạn chưa có AWS account, bạn có thể tạo AWS account của riêng mình [tại đây](https://portal.aws.amazon.com/billing/signup). Một phương thức thanh toán, thường là thẻ tín dụng, sẽ cần thiết để kích hoạt tài khoản cho các bài thực hành này. Quy trình đăng ký bao gồm việc nhận cuộc gọi điện thoại và nhập mã xác minh bằng bàn phím điện thoại.

**⚠️ Warning:** Nếu bạn hiện đang đăng nhập vào AWS Management Console, bạn sẽ cần đăng xuất trước khi [nhấp vào đây](https://portal.aws.amazon.com/billing/signup) để tạo AWS account mới.

#### Chuẩn bị IAM User cho bài thực hành

**🔒 Security Note:** Việc hạn chế nghiêm ngặt việc sử dụng tài khoản root mặc định đi kèm với mỗi AWS account được coi là best practice theo nguyên tắc least privilege. Nếu bạn có AWS account nhưng không có IAM User hoặc Role để làm việc, hãy làm theo các bước dưới đây để chuẩn bị cho bài thực hành.

1. Đăng nhập vào AWS account của bạn 
## Tạo User trong AWS IAM
- Vào **IAM → Users → Create user**
![3.4.11](/images/0001/image02.png)

2. Điền thông tin như hình bên dưới: 
- **User name**: Đặt tên dễ nhớ, ví dụ `adminUser`.    
- **Are you providing console access to a person?** → Chọn  
  - Chọn *I want to create an IAM user* (tạo user IAM truyền thống).  
- **Console password**:  
  - Chọn *Custom password* để tự đặt mật khẩu.    
- Nhấn **Next** để qua bước phân quyền.  
![3.4.11](/images/0001/image01.png)

3. Gán quyền cho User

- Ở ô tìm kiếm, gõ **AdministratorAccess**.  
- Chọn **AdministratorAccess** (policy do AWS quản lý sẵn).  
  - Policy này cấp toàn quyền quản trị cho user, thích hợp khi bạn cần user có quyền cao nhất (giống tài khoản admin).  
- Nhấn **Attach policies** để gán quyền cho user. 
![3.4.11](/images/0001/image03.png)

4. Tiếp tục nhấn **Create user** để hoàn thành. 
![3.4.11](/images/0001/image04.png)
⚠️ Lưu ý: Nếu không muốn user có toàn quyền, bạn có thể chọn các policy hạn chế hơn (ví dụ chỉ cho phép S3, EC2...).  

**💡 Pro Tip:** Khi thiết lập IAM User với quyền Administrator, hãy đảm bảo bạn lưu trữ thông tin đăng nhập một cách an toàn và kích hoạt xác thực đa yếu tố (MFA) để tăng cường bảo mật cho tài khoản của bạn. MFA là một lớp bảo mật bổ sung quan trọng trong mô hình Zero Trust.

**🔒 Security Note:** Trong môi trường sản xuất thực tế, bạn nên áp dụng nguyên tắc least privilege bằng cách chỉ cấp quyền tối thiểu cần thiết cho mỗi IAM User thay vì cấp quyền AdministratorAccess. AWS IAM Identity Center hỗ trợ triển khai chiến lược Zero Trust với các tính năng như Attribute-Based Access Control (ABAC), tích hợp Identity Providers (Microsoft Entra ID, Okta), và quản lý session tự động. Tuy nhiên, cho mục đích của workshop này, quyền Administrator là cần thiết để thiết lập AWS IAM Identity Center.