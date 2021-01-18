+++
title = "Thiết lập AWS Single Sign-On"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

Trong bước này, chúng ta có thể cấp cho User trong danh mục của mình quyền truy cập SSO vào một hoặc nhiều AWS Console cho các tài khoản AWS cụ thể trong Organization trên AWS. Sau đó, User chỉ thấy biểu tượng tài khoản AWS (VD: Development) mà họ đã được chỉ định từ trong cổng thông tin User của họ. Khi họ nhấp vào biểu tượng, họ có thể chọn IAM Role nào họ muốn sử dụng khi đăng nhập vào AWS Console cho tài khoản AWS đó.

**Nội dung:**
- [1. Enable AWS SSO](#1-enable-aws-sso)
- [2. Thêm Users and Groups](#2-thêm-users-and-groups)
- [3. Permission Set](#3-permission-set)
- [4. To assign access to users or groups](#4-to-assign-access-to-users-or-groups)

#### 1. Enable AWS SSO
1. Đăng nhập vào **AWS Management Console** bằng thông tin đăng nhập tài khoản master của **AWS Organization**.
2. Mở **AWS SSO Console**
3. Chọn **Enable AWS SSO**.

![Enable AWS SSO](../../../images/2/1.png?width=50pc)

4. Chọn nguồn nhận dạng để xác định nơi AWS SSO tìm kiếm User và Group khi cần truy cập SSO. Theo mặc định, chúng ta có một kho AWS SSO để quản lý User nhanh chóng và dễ dàng.

![Enable AWS SSO](../../../images/2/2.png?width=50pc)

{{% notice info %}}
Đăng nhập một lần trên AWS (AWS SSO) cung cấp cho bạn một kho lưu trữ mặc định nơi ta có thể lưu trữ User và Group của mình. Nếu ta chọn lưu trữ chúng trong AWS SSO, tất cả những gì bạn cần làm là:
- Tạo User và Group.
- Thêm User làm thành viên Group.
- Chỉ định các Group với mức truy cập mong muốn vào các tài khoản và ứng dụng AWS.
{{% /notice %}}

5. User và Group bạn tạo trong kho lưu trữ AWS SSO của bạn chỉ có sẵn trong AWS SSO. Sử dụng quy trình sau để thêm User vào kho lưu trữ AWS SSO.

#### 2. Thêm Users and Groups
1. Mở **AWS SSO Console**. Chọn **User**.

![Add Users and Groups](../../../images/2/3.png?width=50pc)

2. Chọn Thêm User và cung cấp các thông tin cần thiết sau:
   - **Username** - Tên User này sẽ được yêu cầu để đăng nhập vào cổng thông tin User và không thể thay đổi sau này.
   - **Password** - Chọn một trong các lựa chọn sau để gửi mật khẩu của User.
     - **Send an email to the user with password setup instructions** - Tùy chọn này tự động gửi cho User một email được gửi từ Amazon Web Services. Email mời User truy cập vào cổng thông tin User AWS SSO.
     - **Generate a one-time password that you can share with the user** - Tùy chọn này cung cấp một URL đến cổng thông tin User và mật khẩu để ta có thể tự gửi cho User từ địa chỉ email của mình.
     - **Email address**
     - **Confirm email address**
     - Để rõ ràng, hãy sử dụng **tiền tố** của **User logon name** làm **First name** và **hậu tố** làm **Last name**. VD: đối với Super-User, Super sẽ là First name, trong khi User sẽ là Last name Display name
3. Chọn **Next: Groups**. 

![Add Users and Groups](../../../images/2/4.png?width=50pc)

4. Chọn một hoặc nhiều Group để thêm User là thành viên vào. Sau đó chọn **Add user**.

![Add Users and Groups](../../../images/2/5.png?width=50pc)

5. Chúng ta cần tạo những User và Group sau:

| User logon name |                                                                      Group                                                                      |
|:---------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only                                                                                                                          |

![Add Users and Groups](../../../images/2/6.png?width=50pc)

#### 3. Permission Set
Permission Set xác định khả năng truy cập mà User và Group có đối với tài khoản AWS. Các bộ quyền được lưu trữ trong AWS SSO và được cung cấp cho tài khoản AWS dưới dạng IAM roles. Ta có thể gán nhiều quyền cho một User

1. Mở **AWS SSO Console**. Chọn **AWS accounts**.
2. Chọn trang **Permission sets**.

![Permission Sets](../../../images/2/7.png?width=50pc)

3. Chọn **Create permission set**.

![Permission Sets](../../../images/2/8.png?width=50pc)

4. Trên trang **Create new permission set**, chọn một trong các tùy chọn sau, rồi làm theo hướng dẫn được cung cấp trong tùy chọn đó:
   - Chọn **Use an existing job function policy**. Trong phần **Select job function policy**, chọn một trong các chính sách chức năng công việc IAM mặc định trong danh sách. Để biết thêm thông tin, xem Chính sách được quản lý bởi AWS cho các Chức năng công việc.
   - Chọn **AdministratorAccess** để cung cấp quyền truy cập đầy đủ vào các tài nguyên và dịch vụ AWS. Chọn **Create**.
   - Chọn **SecurityAudit** để cung cấp quyền truy cập Chỉ đọc vào các dịch vụ và tài nguyên AWS. Chọn **Create**.

![Permission Sets](../../../images/2/9.png?width=50pc)

![Permission Sets](../../../images/2/10.png?width=50pc)

#### 4. To assign access to users or groups
1. Mở **AWS SSO Console**. Chọn **AWS accounts**.

![Assign access to users or groups](../../../images/2/11.png?width=50pc)

2. Trong trang **AWS organization**, trong danh sách tài khoản AWS, chọn một hoặc nhiều tài khoản mà ta muốn chỉ định quyền truy cập.
3. Trên trang chi tiết tài khoản AWS, chọn **Assign users**.

![Assign access to users or groups](../../../images/2/12.png?width=50pc) 

4. Trên trang **Select users or groups**, nhập tên User hoặc tên Group và chọn **Search connected directory**. 
5. Khi bạn đã chọn tất cả các tài khoản mà bạn muốn gán quyền truy cập, hãy chọn **Next: Permission sets**. Ở đây có thể chỉ định nhiều User hoặc Group bằng cách chọn các tài khoản áp dụng khi chúng xuất hiện trong kết quả tìm kiếm.

![Assign access to users or groups](../../../images/2/13.png?width=50pc)

6. Trên trang **Select permission sets**, chọn bộ các quyền mà bạn muốn áp dụng cho User hoặc Group từ bảng. Sau đó chọn **Finish**.
7. Chọn **Finish** để bắt đầu quá trình cấu hình tài khoản AWS.

![Assign access to users or groups](../../../images/2/14.png?width=50pc)

![Assign access to users or groups](../../../images/2/15.png?width=50pc)

8. Các tài khoản và chính sách chức năng công việc như sau:

|                      Accounts                      |                                   Groups                                   | Job function policy |
|:--------------------------------------------------:|:--------------------------------------------------------------------------:|:-------------------:|
| Master Account, shared-services, logging,security  | AWS-Shared-Services-Admin AWS-Security-Admin AWS-Logging-Admin             | AdministratorAccess |
| Master Account, shared-services, logging, security | AWS-Shared-Services-Read-Only AWS-Security-Read-Only AWS-Logging-Read-Only | SecurityAudit       |

![Assign access to users or groups](../../../images/2/16.png?width=50pc)
