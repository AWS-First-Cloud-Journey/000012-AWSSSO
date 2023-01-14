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

#### Tạo Group

1. Hiện tại, bạn vẫn chưa có group nào. Chọn Create group để tạo các group được nêu ở bảng phía trên


![AWS Account](/images/6/0001.png?featherlight=false&width=90pc)

2. Ở prompt tạo group, bạn nhập tên các group và mô tả của các group rồi nhấn Create

![AWS Account](/images/6/0002.png?featherlight=false&width=90pc)

3. Lặp lại bước này cho các group còn lại

![AWS Account](/images/6/0003.png?featherlight=false&width=90pc)
#### Thêm User.

1. Mở AWS SSO Console. Chọn Users ở thanh bên trái
   - Chọn Add user và cung cấp các thông tin cần thiết

![AWS Account](/images/5/0001.png?featherlight=false&width=90pc)

2. Hoàn thành thông tin

- **Username** - Tên User này sẽ được yêu cầu để đăng nhập vào cổng thông tin User và không thể thay đổi sau này. (Ví dụ: Super-User)
- **Password** - Chọn một trong các lựa chọn sau để gửi mật khẩu của User.
- **Send an email to the user with password setup insstructions** - Với tùy chọn này, Amazon Web Services sẽ tự động gửi cho User một email mời User truy cập vào cổng thông tin User AWS SSO.
- **Generate a one-time password that you can share with the user** - Tùy chọn này cung cấp một URL đến cổng thông tin User và mật khẩu để bạn có thể tự gửi cho User. Bạn sẽ chọn tùy chọn này trong bài thực hành này. Hoặc chọn **Send an email to this user with password setup instructions**.
- ***Email address**: nhập email của User
- **Confirm email address**: nhập lại email của USer
- Để rõ ràng, hãy sử dụng tiền tố của User logon name làm First name và hậu tố làm Last name. VD: đối với Super-User, Super sẽ là First name, trong khi User sẽ là Last name Display name

![AWS Account](/images/5/0002.png?featherlight=false&width=90pc)

3. Chọn **Next**.

![AWS Account](/images/5/0003.png?featherlight=false&width=90pc)

4. Chọn các group và chọn **Next**

![AWS Account](/images/5/0004.png?featherlight=false&width=90pc)

5. Chọn *Add user**

![AWS Account](/images/5/0005.png?featherlight=false&width=90pc)

6. Hoàn thành tạo user.

![AWS Account](/images/5/0006.png?featherlight=false&width=90pc)

7. Nếu bạn chọn **Send an email to this user with password setup instructions.** thì thực hiện xác thực email để đăng nhập.

![AWS Account](/images/5/0007.png?featherlight=false&width=90pc)

8. Chọn **Send**

![AWS Account](/images/5/0008.png?featherlight=false&width=90pc)

9. Thực hiện **Verify**

![AWS Account](/images/5/0009.png?featherlight=false&width=90pc)

10. Thực hiện cấu hình mật khẩu. Lưu ý: giữ mật khẩu và trang portal để đăng nhập.

![AWS Account](/images/5/00010.png?featherlight=false&width=90pc)

![AWS Account](/images/5/00011.png?featherlight=false&width=90pc)

![AWS Account](/images/5/00012.png?featherlight=false&width=90pc)