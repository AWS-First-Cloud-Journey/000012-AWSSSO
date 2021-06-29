+++
title = "Tạo Permission Set"
date = 2021
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Permission Set
**Permission Set** xác định khả năng truy cập mà User và Group có đối với các tài khoản AWS trong AWS Organization. Các bộ quyền được lưu trữ trong AWS SSO và được cung cấp cho tài khoản AWS dưới dạng IAM roles. Bạn có thể gán nhiều quyền cho một User.

1. Mở **AWS SSO Console**. Chọn **AWS accounts** ở thanh bên trái.
2. Chọn tab **Permission sets**.
3. Chọn **Create permission set**.
![Permission Sets](../../../images/2/2_CreatePermission.png?width=90pc)
4. Tại trang **Create new permission set**:
   - Bước 1: Chọn **Use an existing job function policy** để sử dụng các quyền có sẫn. Chọn **Next: Details**.
   - Bước 2: Chọn **AdministratorAccess** để cung cấp quyền truy cập đầy đủ vào các tài nguyên và dịch vụ AWS. Chọn **Next: Tags**.
   - Bước 3: Chọn **Next: Review**
   - Bước 4: Kiếm tra và chọn **Create**
5. Lặp lại các bước trên để thiết lập Permission Set với quyền **SecurityAudit**. Bạn sẽ có kết quả như hình dưới đây.
![PermissionComplete](../../../images/2/2_PermissionComplete.png?width=90pc)

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