+++
title = "Các bước chuẩn bị"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Tổng quan

Bài thực hành này là một phần của bài thực hành Landing Zone.

Để chuẩn bị các tài nguyên cần thiết, bạn sẽ tạo một AWS Organizations, với 4 Organization Units nhằm phân nhóm các tài khoản. Tạo các Tài khoản AWS (AWS Account) với tên: **Security**, **Shared Services**, **Logging** và **Application** và thêm các Tài khoản vào từng OU tương ứng.

Các tài khoản được tạo sẽ được phân bố các tài nguyên như sau (*Lưu ý: bạn chỉ tham khảo phần này vì nó nằm ngoài phạm vi của bài lab*):
- **Tài khoản Logging:** Là nơi tập trung cho Amazon VPC Flow Logs, CloudTrail logs, Config logs.
- **Tài khoản Security**: Tập hợp AWS Config, Amazon GuardDuty master, và các cảnh báo.
- **Tài khoản Network/Shared Services:** Chia sẻ chung một VPC dành cho các kết nối từ xa đến các tài khoản khác. AWS Direct Connect chính được cài đặt với AWS Transit Gateway nhằm giao tiếp với các VPC ở các tài khoản khác.
- **Tài khoản dành cho Business Unit:** tài khoản cho Analytics-Prod, và Analytics-non-prod.

![Lab Diagram](/images/1/1.png?width=70pc)

#### Nội dung
1. [Tạo AWS Account trong AWS Organization](1-create-aws-account)
2. [Thiết lập Organization Unit](2-configure-OU)
3. [Thêm AWS Account vào AWS Organization](2-configure-OU)
4. [Truy cập qua các acc khác trong Organization](4-switch-role)