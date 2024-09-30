+++
title = "Thiết lập Organization Unit"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2 </b>"
+++

#### Thiết lập Organization Unit trong AWS Organizations

Ở bước này, bạn sẽ thực hành thiết lập các Organization Unit (**Security**, **Shared Services**, **Logging**, và **Application**) tương ứng với các tài khoản AWS được tạo ở phần trước. Các OU sẽ nằm bên trong **Root** - nơi chứa tất cả OU và tài khoản AWS.

#### Nội dung
- [Thiết lập Organization Unit trong AWS Organizations](#thiết-lập-organization-unit-trong-aws-organizations)
- [Nội dung](#nội-dung)
- [Tạo Organization Unit](#tạo-organization-unit)
- [Di chuyển các tài khoản AWS vào Organization Unit tương ứng](#di-chuyển-các-tài-khoản-aws-vào-organization-unit-tương-ứng)
- [Kết luận](#kết-luận)

#### Tạo Organization Unit

1. Đăng nhập vào **AWS Management Console** và điều hướng đến dịch vụ **AWS Organizations** bằng cách nhập tên dịch vụ vào thanh tìm kiếm.

2. Tại cây phân cấp của **AWS Organizations**, chọn **Root**, nhấp vào **Actions**, và chọn **Create new Organizational Unit**.

    ![AWS Account](/images/4/0003.png?featherlight=false&width=90pc)

3. Trong trang **Create Organizational Unit in Root**:
    - Dưới mục **Details**, nhập tên của Organizational Unit (ví dụ: **Logging Unit**).

    ![AWS Account](/images/4/0004.png?featherlight=false&width=90pc)

4. Kiểm tra thông tin và chọn **Create organizational unit**.

    ![AWS Account](/images/4/0005.png?featherlight=false&width=90pc)

5. Lặp lại các bước trên với những Organizational Unit còn lại theo danh sách sau:
    - **Security Unit**
    - **Shared Services Unit**
    - **Application Unit**

    ![AWS Account](/images/4/0006.png?featherlight=false&width=90pc)

#### Di chuyển các tài khoản AWS vào Organization Unit tương ứng

1. Đăng nhập vào **AWS Management Console** và điều hướng đến dịch vụ **AWS Organizations** bằng cách nhập tên dịch vụ vào thanh tìm kiếm.

2. Tại cây phân cấp của **AWS Organizations**, tick vào tài khoản AWS mà bạn muốn di chuyển (ví dụ: **Logging Account**), chọn **Actions**, và chọn **Move** dưới mục **AWS Account**.

    ![AWS Account](/images/4/0007.png?featherlight=false&width=90pc)

3. Chọn OU tương ứng với tài khoản (ví dụ: **Logging Unit**) và nhấp vào **Move AWS account**.

    ![AWS Account](/images/4/0008.png?featherlight=false&width=90pc)

4. Lặp lại với các tài khoản AWS và Organization Unit còn lại:

    - **Security Account** với **Security Unit**
    - **Shared Services Account** với **Shared Services Unit**
    - **Application Account** với **Application Unit**

#### Kết luận

Việc phân loại tài khoản AWS vào các Organization Unit giúp tối ưu hóa việc quản lý tài nguyên và kiểm soát chính sách (policy control). Việc này cũng hỗ trợ trong việc áp dụng các quy tắc bảo mật và quy trình kế toán một cách hiệu quả hơn trên toàn bộ **AWS Organization** của bạn.
