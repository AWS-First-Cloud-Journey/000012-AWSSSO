+++
title = "Gán quyền"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++


#### Gán Quyền Truy Cập cho Người Dùng và Nhóm

Để thiết lập các tài khoản AWS cho các nhóm SSO với các chức năng công việc như sau:

| Tài Khoản                                   | Nhóm                                       | Chính Sách Công Việc |
|:--------------------------------------------:|:------------------------------------------:|:-------------------:|
| Management Account, shared-services, logging, security | AWS-Shared-Services-Admin; AWS-Security-Admin; AWS-Logging-Admin             | AdministratorAccess |
| Management Account, shared-services, logging, security | AWS-Shared-Services-Read-Only; AWS-Security-Read-Only; AWS-Logging-Read-Only | SecurityAudit       |

1. Mở AWS SSO Console. Chọn **AWS accounts** ở thanh bên trái.

   Trong tab **AWS organization**, trong danh sách tài khoản AWS, chọn một hoặc nhiều tài khoản mà bạn muốn chỉ định quyền truy cập. (Ví dụ: Management Account, shared-services, logging, và security). Sau đó, chọn **Assign users or groups**

   ![AWS Account](/images/8/0001.png?featherlight=false&width=90pc)

2. Chọn các nhóm và chọn **Next**

   ![AWS Account](/images/8/00011.png?featherlight=false&width=90pc)

3. Chọn **Permission set**

   ![AWS Account](/images/8/00012.png?featherlight=false&width=90pc)

4. Chọn **Submit**

   ![AWS Account](/images/8/00013.png?featherlight=false&width=90pc)

5. Tương tự, đối với tài khoản **Security Account**

   ![AWS Account](/images/8/0006.png?featherlight=false&width=90pc)

6. Chọn các nhóm và chọn **Next**

   ![AWS Account](/images/8/0007.png?featherlight=false&width=90pc)

7. Chọn **Permission set** và chọn **Next**

   ![AWS Account](/images/8/0008.png?featherlight=false&width=90pc)

8. Chọn **Submit**

   ![AWS Account](/images/8/0009.png?featherlight=false&width=90pc)

9. Chúc mừng, bạn đã thiết lập AWS SSO thành công.

   ![AWS Account](/images/8/00010.png?featherlight=false&width=90pc)
