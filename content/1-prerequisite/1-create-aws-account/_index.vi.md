+++
title = "Tạo AWS Account trong AWS Organizations"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1 </b>"
+++

#### Tạo AWS Account trong AWS Organization

#### Mục tiêu

Hướng dẫn chi tiết cách tạo tài khoản AWS mới trong **AWS Organizations**, bao gồm thiết lập email, cấu hình IAM role, và kiểm tra tính hợp lệ của tài khoản.

---

#### 1. Truy cập vào AWS Organizations

1. Đăng nhập vào **AWS Management Console**.
2. Tìm kiếm và chọn dịch vụ **AWS Organizations** từ thanh tìm kiếm.

![AWS Organizations Console](/images/1/0001.png?featherlight=false&width=90pc)

---

#### 2. Thêm tài khoản AWS mới

1. Trong giao diện **AWS Organizations Console**, chọn **Add an AWS account**.

![Add an AWS Account](/images/1/0003.png?featherlight=false&width=90pc)

---

#### 3. Chọn Tạo tài khoản AWS mới

1. Chọn **Create an AWS account**.
2. Nhập các thông tin bắt buộc dưới đây:
   - **AWS account name**: Logging
   - **Email address of the account's owner**: `example+lab12Logging@amazon.com.vn`

![AWS Account Configuration](/images/4/0002.png?featherlight=false&width=90pc)

{{% notice note %}}
**Lưu ý:** Để tạo nhiều tài khoản AWS với cùng một email, bạn có thể sử dụng cú pháp: `example+<description>@domain.com`. Ví dụ: `example+lab12Logging@amazon.com.vn`.
{{% /notice %}}

---

#### 4. Cấu hình IAM Role

1. **IAM role name**: Để mặc định là **OrganizationAccountAccessRole**.

Role này sẽ được sử dụng để truy cập vào tài khoản AWS thành viên bằng phương thức [Chuyển đổi role (Switch Role)](https://000002.awsstudygroup.com/3-switch-roles/).

![IAM Role Configuration](/images/4/0002.png?featherlight=false&width=90pc)

---

#### 5. Xác nhận và tạo tài khoản

1. Kiểm tra lại thông tin đã nhập.
2. Chọn **Create AWS account** để tiến hành tạo tài khoản.

---

#### 6. Lặp lại quy trình cho các tài khoản khác

1. Tạo thêm các tài khoản tương tự cho các mục đích khác như:
   - **Security**
   - **Shared Services**
   - **Application**

**Lưu ý:** Nếu địa chỉ email bạn sử dụng đã được đăng ký cho một tài khoản AWS khác, bạn sẽ nhận được thông báo lỗi khi thực hiện yêu cầu tạo tài khoản mới.

---

#### 7. Kiểm tra trạng thái yêu cầu

1. Vào mục **Requests** để xem trạng thái của các yêu cầu tạo tài khoản.
2. Nếu yêu cầu thành công, bạn sẽ thấy tài khoản mới hiển thị trong danh sách các tài khoản thành viên của **AWS Organizations**.
