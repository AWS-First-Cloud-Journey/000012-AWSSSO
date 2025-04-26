+++  
title = "Sử dụng AWS IAM Identity Center để quản lý định danh mạnh mẽ"  
date = 2024  
weight = 1  
chapter = false  
+++  

# Sử dụng AWS IAM Identity Center để quản lý định danh mạnh mẽ

#### Giới thiệu

**ℹ️ Thông tin:** Workshop này được thiết kế để giúp bạn làm quen với AWS IAM Identity Center (trước đây là AWS Single Sign-On) để quản lý định danh nhân viên của tổ chức một cách hiệu quả trên nhiều AWS accounts.

#### Kịch bản

Công ty của bạn mới bắt đầu sử dụng cloud computing và đang lên kế hoạch xây dựng hệ thống trên AWS. Công ty muốn thực thi security access controls mạnh mẽ một cách tập trung và có khả năng mở rộng.

Với vai trò là cloud administrator, bạn được giao nhiệm vụ thiết lập quyền truy cập vào các AWS accounts cho nhân viên công ty theo nguyên tắc least privilege. Trong quá trình configuration, bạn chịu trách nhiệm thiết lập IAM Identity Center và cung cấp quyền truy cập vào các AWS accounts dựa trên group membership và project/team roles của người dùng.

#### Tổng quan

- **Cấp độ:** Intermediate
- **Thời lượng:** 1-3 giờ
- **Chức năng NIST Cybersecurity Framework (CSF):** Identify
- **Thành phần AWS Cloud Adoption Framework (CAF):** Directive
- **Chi phí:** 

**💡 Pro Tip:** Không có chi phí liên quan đến IAM Identity Center và AWS Organizations. Đối với các services khác, phần lớn chi phí phát sinh trong workshop này được bao gồm trong free tier cho các services cụ thể trong AWS account (ví dụ: Amazon EC2). Tuy nhiên, có thể phát sinh một số chi phí liên quan đến data storage (ví dụ: AWS CloudTrail logs). Bạn nên cleanup môi trường bằng cách làm theo hướng dẫn trong phần Cleanup sau khi hoàn thành workshop để tránh phát sinh thêm chi phí.

- **Supported Regions:** 

**ℹ️ Thông tin:** Khuyến nghị chạy workshop này trong Region us-east-1.

- **Đối tượng mục tiêu:** Cloud and IT Administrators
- **Prerequisites:**
  - AWS account chưa tham gia AWS Organizations
  - IAM user có administrative permissions cho tài khoản đó

**⚠️ Warning:** Vui lòng launch một Amazon EC2 instance trong tài khoản mới của bạn trong vài giờ trước khi bắt đầu workshop này để đảm bảo tài khoản của bạn đang hoạt động và sẵn sàng cho workshop. Nếu bạn đang tham gia workshop này tại AWS event như re:Invent hoặc re:Inforce, bạn sẽ được cung cấp AWS credits để trang trải chi phí liên quan đến workshop.

**🔒 Security Note:** IAM Identity Center cung cấp centralized access management, giúp giảm thiểu security risks liên quan đến việc quản lý nhiều credentials trên nhiều AWS accounts. Việc triển khai IAM Identity Center là một phần quan trọng trong chiến lược Zero Trust và tuân thủ nguyên tắc least privilege.