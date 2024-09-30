+++  
title = "AWS Single Sign-On: Quản lý truy cập trong AWS Organization"  
date = 2024  
weight = 1  
chapter = false  
+++  

# AWS Single Sign-On (SSO) cho Organization  

Trong bài viết này, chúng ta sẽ khám phá cách sử dụng dịch vụ AWS Single Sign-On (SSO) để quản lý việc truy cập và ủy quyền cho người dùng trong các tài khoản AWS của bạn một cách hiệu quả. Bằng cách tận dụng AWS SSO, bạn có thể quản lý quyền truy cập cho toàn bộ các tài khoản thuộc AWS Organization từ một điểm kiểm soát trung tâm.

#### Tổng quan về AWS Single Sign-On (SSO)  

AWS Single Sign-On (AWS SSO) là một dịch vụ cung cấp khả năng quản lý xác thực và ủy quyền truy cập cho người dùng vào các tài khoản AWS, ứng dụng dựa trên đám mây (SaaS), và các ứng dụng tùy chỉnh. Thay vì sử dụng thông tin đăng nhập riêng lẻ cho từng tài khoản hoặc dịch vụ, AWS SSO cho phép bạn định cấu hình và kiểm soát quyền truy cập từ một nơi duy nhất, đảm bảo bảo mật và tuân thủ quy định trong tổ chức.

#### Các lợi ích chính của AWS SSO:

- **Quản lý tập trung:** Dễ dàng quản lý người dùng và quyền truy cập cho toàn bộ các tài khoản AWS từ một giao diện duy nhất.
- **Single Sign-On:** Người dùng chỉ cần đăng nhập một lần để truy cập tất cả các tài nguyên mà họ được cấp quyền.
- **Tích hợp với AWS IAM:** Hỗ trợ tích hợp chặt chẽ với AWS Identity and Access Management (IAM) và AWS Organizations để quản lý quyền truy cập một cách chính xác.
- **Khả năng mở rộng:** Hỗ trợ tích hợp với các nguồn danh tính doanh nghiệp như Microsoft Active Directory hoặc các IdP (Identity Provider) bên ngoài khác.

#### Cách AWS SSO hoạt động trong AWS Organization  

AWS SSO tích hợp chặt chẽ với **AWS Organizations** để giúp quản lý quyền truy cập cho các tài khoản AWS thành viên. Một số thuật ngữ và thành phần quan trọng mà bạn cần hiểu rõ:

- **AWS Organization:** Là tập hợp các tài khoản AWS được quản lý tập trung, cho phép bạn quản lý các tài khoản thành viên dưới một cấu trúc có tổ chức.
  
- **Organizational Unit (OU):** Một nhóm tài khoản AWS trong AWS Organization. OU giúp bạn phân nhóm tài khoản theo chức năng, môi trường (như Dev, Test, Prod), hoặc theo nhu cầu bảo mật.
  
- **Management Account:** Tài khoản quản lý có quyền cao nhất trong AWS Organization. Đây là tài khoản duy nhất có quyền cấu hình và thiết lập AWS SSO cho toàn bộ tổ chức.

- **Permission Set:** Các tập hợp quyền được định nghĩa sẵn (tương tự như IAM Policies) được gán cho người dùng hoặc nhóm người dùng để xác định quyền truy cập vào từng tài khoản AWS cụ thể.

- **AWS SSO Directory:** Là nguồn danh tính mặc định để quản lý người dùng và nhóm. Bạn có thể tích hợp AWS SSO với các nguồn danh tính khác như AWS Managed Microsoft AD, AD Connector, hoặc IdP bên thứ ba như Okta, OneLogin.

#### Hướng dẫn từng bước thiết lập AWS SSO

#### Bước 1: Kích hoạt AWS Single Sign-On cho Organization

1. Truy cập vào [AWS Management Console](https://aws.amazon.com/console/).
2. Mở **AWS Single Sign-On**.
3. Nếu đây là lần đầu bạn sử dụng AWS SSO, chọn **Enable AWS SSO**.
4. Chọn **Management Account** và đảm bảo rằng tài khoản này đã được kết nối với AWS Organizations.

#### Bước 2: Cấu hình danh tính người dùng

1. Chọn **AWS SSO Settings**.
2. Ở mục **Identity Source**, chọn một trong các tùy chọn sau:
   - **AWS SSO Directory:** Sử dụng thư mục người dùng mặc định của AWS SSO.
   - **External Identity Provider (IdP):** Sử dụng IdP bên ngoài như Okta hoặc OneLogin.
   - **AWS Managed Microsoft AD:** Tích hợp với Active Directory do AWS quản lý.
3. Cấu hình kết nối theo hướng dẫn từ dịch vụ mà bạn chọn.

#### Bước 3: Tạo và gán Permission Sets

1. Chọn **AWS Accounts** trong bảng điều khiển AWS SSO.
2. Chọn tài khoản AWS bạn muốn quản lý.
3. Chọn **Assign Users** và sau đó chọn **Create New Permission Set**.
4. Tạo một Permission Set với quyền như **AdministratorAccess** hoặc tùy chỉnh dựa trên yêu cầu bảo mật của tổ chức.
5. Gán Permission Set này cho người dùng hoặc nhóm người dùng.

#### Bước 4: Thiết lập quyền truy cập vào tài khoản AWS

1. Quay lại mục **AWS Accounts**, chọn tài khoản bạn muốn cấp quyền.
2. Gán Permission Sets đã tạo ở trên cho các người dùng hoặc nhóm.
3. Nhấn **Finish** để hoàn tất quá trình cấu hình quyền truy cập.

#### Bước 5: Kiểm tra và xác minh quyền truy cập

1. Đăng nhập vào AWS SSO User Portal với tài khoản người dùng mà bạn đã cấu hình.
2. Kiểm tra danh sách các tài khoản AWS và xác minh quyền truy cập của người dùng.
3. Thực hiện một số tác vụ như tạo S3 bucket, chạy Lambda function, hoặc kiểm tra log để đảm bảo các quyền đã được áp dụng đúng.

#### Kiểm tra kết quả & Dọn dẹp tài nguyên

#### Kiểm tra kết quả:
1. Đảm bảo rằng người dùng có thể truy cập vào các tài khoản AWS theo quyền hạn đã cấu hình.
2. Xác minh rằng việc đăng nhập SSO hoạt động như mong đợi từ giao diện **AWS SSO User Portal**.

#### Dọn dẹp tài nguyên:
1. Gỡ bỏ các tài khoản thử nghiệm hoặc người dùng không còn cần thiết.
2. Xóa các Permission Sets không còn sử dụng.
3. Nếu không còn nhu cầu sử dụng AWS SSO, hãy vào **Settings** và chọn **Disable AWS SSO**.

#### Tổng kết
AWS Single Sign-On cung cấp một phương thức quản lý truy cập tập trung và bảo mật cho toàn bộ các tài khoản AWS trong tổ chức của bạn. Với việc thiết lập và cấu hình đúng, bạn có thể quản lý việc xác thực và ủy quyền cho hàng ngàn người dùng một cách hiệu quả, giảm thiểu rủi ro bảo mật và tối ưu hóa quy trình quản lý quyền truy cập.

Chúc bạn thành công trong việc triển khai AWS SSO cho tổ chức của mình!
