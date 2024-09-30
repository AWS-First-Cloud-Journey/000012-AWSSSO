+++
title = "Các bước chuẩn bị"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Tổng quan

Bài thực hành này là một phần của bài thực hành **Landing Zone**.

Để chuẩn bị các tài nguyên cần thiết, bạn sẽ thiết lập **AWS Organizations** với cấu trúc bao gồm 4 **Organizational Units (OUs)** nhằm phân nhóm các tài khoản. Mỗi **AWS Account** sẽ có vai trò và chức năng cụ thể, với các tên như sau: **Security**, **Shared Services**, **Logging**, và **Application**. Sau khi tạo các tài khoản, bạn sẽ thêm chúng vào các OU tương ứng.

Các tài khoản được tạo sẽ được phân bổ tài nguyên theo cấu trúc sau (*Lưu ý: Đây là thông tin tham khảo và không nằm trong phạm vi của bài thực hành này*):
- **Tài khoản Logging:** Tập trung để lưu trữ các logs từ Amazon VPC Flow Logs, CloudTrail logs, và AWS Config logs.
- **Tài khoản Security:** Quản lý các dịch vụ bảo mật bao gồm AWS Config, Amazon GuardDuty master account, và các cảnh báo liên quan đến bảo mật.
- **Tài khoản Shared Services (Network/Shared Services):** Đóng vai trò như một VPC trung tâm cho các kết nối từ xa, quản lý các tài nguyên chia sẻ như AWS Transit Gateway, AWS Direct Connect, nhằm giao tiếp với các VPC khác trong cùng **AWS Organization**.
- **Tài khoản dành cho Business Unit:** Đây là tài khoản dành riêng cho các môi trường khác nhau như **Analytics-Prod**, **Analytics-non-prod**, hoặc các ứng dụng sản xuất.

#### Mô hình triển khai (Lab Diagram)
![Lab Diagram](/images/1/1.png?width=70pc)

#### Nội dung chính
1. [Tạo AWS Account trong AWS Organization](1-create-aws-account)
2. [Thiết lập Organization Unit (OU)](2-configure-OU)
3. [Thêm AWS Account vào từng OU trong AWS Organization](3-add-account-to-ou)
4. [Thiết lập quyền truy cập giữa các tài khoản bằng tính năng Switch Role](4-switch-role)

#### Kết luận
Bằng cách thiết lập **AWS Organizations** và **Organizational Units (OUs)** với các tài khoản AWS độc lập, bạn có thể quản lý các tài nguyên một cách hiệu quả hơn. Cấu trúc này giúp phân quyền rõ ràng, đảm bảo các dịch vụ bảo mật và logs được tập trung hóa, đồng thời tối ưu hóa việc quản trị tài nguyên trên các môi trường khác nhau.

> Tham khảo thêm: [AWS Organizations Documentation](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)
