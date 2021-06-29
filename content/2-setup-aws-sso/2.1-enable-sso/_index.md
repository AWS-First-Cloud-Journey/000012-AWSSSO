+++
title = "Kích hoạt AWS SSO"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

#### Kích hoạt AWS SSO
1. Đăng nhập vào **AWS Management Console** bằng thông tin đăng nhập tài khoản master của **AWS Organization**.
2. Mở **AWS SSO Console**
3. Chọn **Enable AWS SSO**.

![Enable AWS SSO](../../../images/2/2_EnableSSO.png?width=90pc)

Đăng nhập một lần trên AWS SSO cung cấp cho bạn một kho lưu trữ mặc định nơi bạn có thể lưu trữ User và Group của mình. Nếu bạn chọn lưu trữ chúng trong AWS SSO, tất cả những gì bạn cần làm là:
- Tạo User và Group.
- Thêm User làm thành viên Group.
- Chỉ định các Group với mức truy cập mong muốn vào các tài khoản và ứng dụng AWS.
