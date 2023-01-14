+++
title = "Thiết lập Organization Unit"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

Ở bước này, bạn sẽ thực hành thiết lập các Organization Unit (**Security**, **Shared Services**, **Logging** và **Application**) tương ứng với các tài khoản AWS được tạo ở phần trước. Các OU sẽ nằm bên trong Root - nơi chứa tất cả OU và tài khoản AWS.

**Nội dung**
- [Tạo Organization Unit](#tạo-organization-unit)
- [Di chuyển các tài khoản AWS vào Organization Unit tương ứng](#di-chuyển-các-tài-khoản-aws-vào-organization-unit-tương-ứng)

#### Tạo Organization Unit

1. Truy cập vào **AWS Management Comsole** và tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm.

2. Tick vào **Root**, chọn **Actions**, và chọn **Create new** dưới **Organizational Unit**

![AWS Account](/images/4/0003.png?featherlight=false&width=90pc)

3. Tại trang **Create organizational unit in Root**:
    - Dưới mục **Details**, nhập tên của OU (Ví dụ: Logging Unit)

![AWS Account](/images/4/0004.png?featherlight=false&width=90pc)

4. Kiểm tra thông tin và chọn **Create organizational unit**

![AWS Account](/images/4/0005.png?featherlight=false&width=90pc)

5. Lặp lại với các Organization Unit còn lại. 

![AWS Account](/images/4/0006.png?featherlight=false&width=90pc)

#### Di chuyển các tài khoản AWS vào Organization Unit tương ứng

1. Truy cập vào **AWS Management Comsole** và tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm.

2. Tick vào tài khoản AWS mà bạn muốn di chuyển (Ví dụ: **Logging**), chọn **Actions**, và chọn **Move** dưới **AWS Account**


![AWS Account](/images/4/0007.png?featherlight=false&width=90pc)

3. Tick vào OU phù hợp (Ví dụ: **Logging Unit**) và chọn **Move AWS account**


![AWS Account](/images/4/0008.png?featherlight=false&width=90pc)

4. Lặp lại với các tài khoản AWS và Organization Unit còn lại:
    - Security Account với Security Unit
    - Shared Services với Shared Services Unit
    - Application Account với Application Unit

