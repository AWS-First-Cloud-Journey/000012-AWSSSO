+++
title = "Truy cập qua các AWS Account khác trong Organization"
date = 2020
weight = 4
chapter = false
pre = "<b>1.4 </b>"
+++

#### Truy cập qua các AWS Account khác trong Organization

Ở bước này, bạn sẽ đứng tại **management account** để truy cập vào các **member account** thông qua chức năng **switch role**.

#### **Nội dung**

- **Switch role** vào các **member account** được tạo bởi **AWS Organization** (bước 1.1)
- **Switch role** vào các **member account** được mời tham gia **AWS Organization** (bước 1.3)

#### A) **Switch role** vào các **member account** được tạo bởi **AWS Organization**

1. Đăng nhập vào **management account**

   - Sử dụng **IAM User** để đăng nhập.
   - Truy cập **AWS Management Console**, tìm kiếm và chọn **AWS Organizations**.
   - Sao chép **Account ID** (12 chữ số dưới tên của Account) mà bạn muốn truy cập.
   - Nhấp vào biểu tượng hình tam giác bên phải tên tài khoản và chọn **Switch role**.

   <!-- ![AWS Account](/images/11/0000.png?featherlight=false&width=90pc) -->

   **Lưu ý**: Nếu bạn đang dùng tài khoản **root**, bạn sẽ không thấy tùy chọn **Switch role**.

   Nếu bạn chưa quen việc tạo IAM User với quyền Admin, hãy xem lại bài: [Quản trị quyền truy cập với AWS IAM](https://000002.awsstudygroup.com/vi/1-introduction/).

2. **Switch role**

   - Tại mục **Account**, dán **Account ID** mà bạn đã sao chép.
   - Tại mục **Role**, điền **role name** bạn đã tạo, ví dụ: `OrganizationAccountAccessRole`.
   - Mục **Display Name**: nhập tên để dễ nhận diện, ví dụ: `FCJ-DEV`.
   - Chọn **Switch Role**.

   ![AWS Account](/images/11/0003.png?featherlight=false&width=90pc)

   - **Kết quả**: Bạn đã Switch Role thành công.

   ![AWS Account](/images/11/0004.png?featherlight=false&width=90pc)

#### Giải thích:

- IAM User trong **management account** có quyền admin, cho phép sử dụng role `OrganizationAccountAccessRole` để truy cập vào **member account** vì:
  - **AWS Organizations** đã gán quyền **AdministratorAccess** cho role này khi tạo tài khoản.

#### Thực hành:

3. **Tạo User Groups** trên **management account**

   - Truy cập **IAM**, chọn **User Groups**, nhấn **Create Group**.
   - Nhập tên Group, ví dụ: `DevGroup`.
   - Chọn **Create policy**, một cửa sổ mới sẽ xuất hiện.

4. **Tạo Custom Policy**

   - Dịch vụ: **STS** -> Chọn **AssumeRole**.
   - Tài nguyên: Nhập **Account ID** và **Role name** của member account.
   - Chọn **Next**, rồi đặt tên policy, ví dụ: `switch_role_999999999943`.
   - Chọn **Create policy**.

5. Gắn policy vừa tạo vào **User Groups**

   - Quay lại trang **Create user group**.
   - Tìm **switch_role_999999999943** trong danh sách và chọn.

6. **Tạo User**

   - Nhập tên user, ví dụ: **DevLead**.
   - Chọn Group vừa tạo (`DevGroup`).

7. Đăng nhập vào **IAM User** vừa tạo và kiểm tra.

8. Thực hiện **switch role** qua **member account** theo các bước ở trên.

#### B) **Switch role** vào các **member account** được mời tham gia **AWS Organization**

1. **Tạo Role** trong **member account**

   - Chọn **AWS account** -> **Another AWS account**.
   - Nhập **Account ID** của **management account**.
   - Gán quyền **AdministratorAccess** cho role `OrganizationAccountAccessRole`.

2. Thực hiện **switch role** từ **management account** như phần trên.

#### Đúc kết:

- **Create an AWS account** sẽ tự động thêm **OrganizationAccountAccessRole** với quyền **AdministratorAccess**.
- **Invite an existing AWS account** cần tạo role `OrganizationAccountAccessRole` thủ công và gán quyền.

#### Tùy chọn mở rộng: Thiết lập **AWS SSO** để truy cập vào các **member account** dễ dàng hơn.
