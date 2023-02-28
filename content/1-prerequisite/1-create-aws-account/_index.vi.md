+++
title = "Tạo AWS Account trong AWS Organizations"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

Ở bước này, bạn sẽ thực hành tạo các tài khoản AWS (**Security**, **Shared Services**, **Logging** và **Application**) bên trong dịch vụ AWS Organization. Các tải khoản AWS được tạo bên trong AWS Organization chỉ có thể dược truy cập bằng IAM Role hoặc thông tin của root user.

**Nội dung**
- [Tạo AWS Account trong AWS Organization](#tạo-aws-account-trong-aws-organization)

#### Tạo AWS Account trong AWS Organization

1. Truy cập vào **AWS Management Comsole** và tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm.

![AWS Account](/images/1/0001.png?featherlight=false&width=90pc)

![AWS Account](/images/1/0002.png?featherlight=false&width=90pc)

2. Tại **AWS Organizations Console**, chọn **Add an AWS account**

![AWS Account](/images/1/0003.png?featherlight=false&width=90pc)

3. Chọn **Create an AWS account** và nhập các thông số dưới đây:
    - **AWS account name**: Logging
    - **Email address of the account's owner**: example+lab12Logging@amazon.com.vn

![AWS Account](/images/4/0002.png?featherlight=false&width=90pc)

{{% notice note %}}
Để tạo nhiều tài khoản AWS với cùng một email, bạn có thể lấy phần tên email của bạn, thêm dấu **"+"**, và thêm miêu tả phía sau.
{{% /notice %}}

- **IAM role name**: giữ mặc định là **OrganizationAccountAccessRole**. Đây sẽ là role name mà bạn sẽ dùng để truy cập vào tải khoản AWS thành viên qua phương pháp [chuyển đổi role](https://000002.awsstudygroup.com/3-switch-roles/).

![AWS Account](/images/4/0002.png?featherlight=false&width=90pc)


4. Kiếm tra thông tin và chọn **Create AWS account**


![AWS Account](/images/4/0002.png?featherlight=false&width=90pc)


5. Lặp lại các bước trên với các tài khoản **Security**, **Shared Services**,và **Application**, tùy theo mỗi tài khoản cá nhân hay doanh nghiệp bao có thể tạo số lượng tài khoản có giới hạn.

**Lưu ý**: nếu địa chỉ mail mà bạn dùng để tạo AWS Account đã tồn tại, AWS sẽ phản hồi như sau trong mục request:

- Chọn **Requests**

![AWS Account](/images/10/001.png?featherlight=false&width=90pc)

- Tại mục **Failure reason** lý do là: **EMAIL_ALREADY_EXISTS**

![AWS Account](/images/10/002.png?featherlight=false&width=90pc)