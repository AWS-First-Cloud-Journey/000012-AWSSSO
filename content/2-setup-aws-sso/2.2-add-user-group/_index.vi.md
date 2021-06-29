+++
title = "Thêm Users và Groups"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++


#### Thêm Users và Groups

Bạn cần tạo những User và Group như bảng dưới. Trong đó, User ở cột **User logon name** sẽ thuộc các Group ở cột **Group**.

| User logon name |                  Group           |
|:---------------:|:--------------------------------:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only           |

1. Mở **AWS SSO Console**. Chọn **Users** ở thanh bên trái
2. Chọn **Add user** và cung cấp các thông tin cần thiết sau:
   - **Username** - Tên User này sẽ được yêu cầu để đăng nhập vào cổng thông tin User và không thể thay đổi sau này. (Ví dụ: Super-User)
   - **Password** - Chọn một trong các lựa chọn sau để gửi mật khẩu của User.
     - **Send an email to the user with password setup instructions** - Với tùy chọn này, Amazon Web Services sẽ tự động gửi cho User một email mời User truy cập vào cổng thông tin User AWS SSO.
     - **Generate a one-time password that you can share with the user** - Tùy chọn này cung cấp một URL đến cổng thông tin User và mật khẩu để bạn có thể tự gửi cho User. **Bạn sẽ chọn tùy chọn này trong bài thực hành này**.
     - **Email address**: nhập email của User
     - **Confirm email address**: nhập lại email của USer
     - Để rõ ràng, hãy sử dụng **tiền tố** của **User logon name** làm **First name** và **hậu tố** làm **Last name**. VD: đối với Super-User, Super sẽ là First name, trong khi User sẽ là Last name Display name
3. Chọn **Next: Groups**. 
![AddUserDetails](../../../images/2/2_AddUserDetails.png?width=90pc)
4. Hiện tại, bạn vẫn chưa có group nào. Chọn **Create group** để tạo các group được nêu ở bảng phía trên
   - Ở prompt tạo group, bạn nhập tên các group và mô tả của các group rồi nhấn **Create**
   - Lặp lại bước này cho các group còn lại
   ![Add Users and Groups](../../../images/2/2_CreateGroupPrompt.png?width=90pc)
5. Chọn một hoặc nhiều group để thêm User là thành viên vào. Sau đó chọn **Add user**. (Ví dụ: Super-User sẽ có quyền truy cập vào tất cả các group)
![AddUserGroups](../../../images/2/2_AddUserGroups.png?width=90pc)
6. Tại trang kết quả của **Add user**, bạn sẽ thấy được các thông số:
   - **User portal URL**: đây là đường link mà người dùng có thể dùng để đăng nhập vào AWS SSO User vừa được tạo. 
   - **Username**: tên tài khoản của User
   - **One-time password**: mật khẩu đăng nhập dùng một lần. Người dùng sẽ phải thay đổi mật khẩu này khi họ đăng nhập vào User.
7. Chọn **Copy details** để lưu thông tin đăng nhập trên vào một chỗ thuận tiện *(Lưu ý: Bạn sẽ cần thông tin đăng nhập ấy cho phần kiểm tra kết quả sau này*). Chọn **Close**.
![AddUserGroups](../../../images/2/2_AddUserComplete.png?width=90pc)
8. Hãy lặp lại các bước trên sao cho phù hợp với **Security-User**.
