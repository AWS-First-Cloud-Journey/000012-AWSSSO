+++
title = "Thêm Users và Groups"
date = 2021
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++


#### Thêm Users và Groups

Bạn cần tạo các User và Group như bảng dưới đây. User ở cột **User logon name** sẽ thuộc các Group ở cột **Group**.

| User logon name | Group |
|:---------------:|:-----:|
| Super-User      | AWS-Shared-Services-Admin; AWS-Shared-Services-Read-Only; AWS-Security-Admin; AWS-Security-Read-Only; AWS-Logging-Admin; AWS-Logging-Read-Only; |
| Security-User   | AWS-Security-Read-Only |

#### Tạo Group

1. Hiện tại, bạn chưa có group nào. Hãy chọn **Create group** để tạo các group được liệt kê ở bảng phía trên.

   ![AWS Account](/images/6/0001.png?featherlight=false&width=90pc)

2. Tại prompt tạo group, bạn nhập tên và mô tả của các group, sau đó nhấn **Create**.

   ![AWS Account](/images/6/0002.png?featherlight=false&width=90pc)

3. Lặp lại bước này cho các group khác.

   ![AWS Account](/images/6/0003.png?featherlight=false&width=90pc)

#### Thêm User

1. Mở **AWS SSO Console**. Trong thanh bên trái, chọn **Users**.
   - Chọn **Add user** và cung cấp các thông tin cần thiết.

   ![AWS Account](/images/5/0001.png?featherlight=false&width=90pc)

2. Hoàn thành thông tin sau:
   - **Username**: Tên User này sẽ được yêu cầu để đăng nhập vào cổng thông tin User và không thể thay đổi sau này (VD: Super-User).
   - **Password**: Chọn một trong các lựa chọn sau để gửi mật khẩu của User.
       - **Send an email to the user with password setup instructions**: AWS sẽ tự động gửi email mời User truy cập vào cổng thông tin User AWS SSO.
       - **Generate a one-time password that you can share with the user**: URL đến cổng thông tin User và mật khẩu sẽ được cung cấp.
   - ***Email address**: Nhập email của User.
   - **Confirm email address**: Nhập lại email của User.
   - Để rõ ràng, hãy sử dụng tiền tố của **User logon name** làm **First name** và hậu tố làm **Last name**. Ví dụ: đối với Super-User, "Super" sẽ là **First name**, trong khi "User" sẽ là **Last name** Display name.

   ![AWS Account](/images/5/0002.png?featherlight=false&width=90pc)

3. Chọn **Next**.

   ![AWS Account](/images/5/0003.png?featherlight=false&width=90pc)

4. Chọn các group và chọn **Next**.

   ![AWS Account](/images/5/0004.png?featherlight=false&width=90pc)

5. Chọn **Add user**.

   ![AWS Account](/images/5/0005.png?featherlight=false&width=90pc)

6. Hoàn thành tạo user.

   ![AWS Account](/images/5/0006.png?featherlight=false&width=90pc)

7. Nếu bạn chọn **Send an email to this user with password setup instructions**, thực hiện xác thực email để đăng nhập.

   ![AWS Account](/images/5/0007.png?featherlight=false&width=90pc)

8. Chọn **Send**.

   ![AWS Account](/images/5/0008.png?featherlight=false&width=90pc)

9. Thực hiện **Verify**.

   ![AWS Account](/images/5/0009.png?featherlight=false&width=90pc)

10. Thực hiện cấu hình mật khẩu. Lưu ý: Giữ mật khẩu và trang portal để đăng nhập.

    ![AWS Account](/images/5/00010.png?featherlight=false&width=90pc)
    ![AWS Account](/images/5/00011.png?featherlight=false&width=90pc)
    ![AWS Account](/images/5/00012.png?featherlight=false&width=90pc)
