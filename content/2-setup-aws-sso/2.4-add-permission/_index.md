+++
title = "Gán quyền"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++

#### Gán quyền truy cập cho Users và Groups

Bạn cần thiết lập các tài khoản AWS vào các SSO group với chức năng công việc như sau:

|                      Accounts                      |                                   Groups                                   | Job function policy |
|:--------------------------------------------------:|:--------------------------------------------------------------------------:|:-------------------:|
| Management Account, shared-services, logging,security  | AWS-Shared-Services-Admin; AWS-Security-Admin; AWS-Logging-Admin             | AdministratorAccess |
| Management Account, shared-services, logging, security | AWS-Shared-Services-Read-Only; AWS-Security-Read-Only; AWS-Logging-Read-Only | SecurityAudit       |

1. Mở **AWS SSO Console**. Chọn **AWS accounts** ở thanh bên trái.
2. Trong tab **AWS organization**, trong danh sách tài khoản AWS, chọn một hoặc nhiều tài khoản mà bạn muốn chỉ định quyền truy cập. (Ví dụ: Management Account, shared-services, logging, và security). Sau đó, chọn **Assign users**.
![Assign access to users or groups](../../../images/2/2_AssignUser.png?width=90pc) 
3. Tại trang **Select users or groups**, chọn tab Group và chọn các group thích hợp (Ví dụ: AWS-Shared-Services-Admin; AWS-Security-Admin; AWS-Logging-Admin ), và chọn **Next: Permission sets**. 

4. Tại trang **Select permission sets**, bạn sẽ gán quyền **AdministatorAccess**  truy cập cho các tài khoản AWS và group đã chọn. 
5. Chọn **Finish** để bắt đầu quá trình cấu hình tài khoản AWS.
6. Lặp lại các bước trên để gán tổ hợp nhóm và quyền **SecurityAudit**

Chúc mừng, bạn đã thiết lập AWS SSO thành công. 