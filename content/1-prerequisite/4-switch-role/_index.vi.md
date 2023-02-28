+++
title = "Truy cập qua các AWS Account khác trong Organization"
date = 2020
weight = 4
chapter = false
pre = "<b>1.4 </b>"
+++

Ở bước này, bạn sẽ đứng tại **management account** để truy cập vào các **member account** thông qua chức năng **switch role**

**Nội dung**

- **switch role** vào các **member account** được tạo bởi **AWS Organization** (bước 1.1)
- **switch role** vào các **member account** được mời tham gia **AWS Organization** (bước 1.3)

#### A) **Switch role** vào các **member account** được tạo bởi **AWS Organization**

1. Đăng nhập vào **management account**

- Dùng **IAM User** để đăng nhập

- Truy cập vào **AWS Management Comsole** và tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm.

- Sao chép Account ID (Có 12 con số & xuất hiện phía dưới tên của Account) mà bạn muốn truy cập

- Ở gốc bên phải, phía sau tên của Account, chọn dấu tam giác, Chọn**Switch role**

![AWS Account](/images/11/0000'.png?featherlight=false&width=90pc)

- **Lưu ý**, nếu bạn đang dùng account **root**, bạn sẽ không thể nhìn thấy chức năng **Switch role**

- Nếu bạn chưa thành thạo việc tạo IAM User (có quyền Admin) để phục vụ cho bài lab này, vui lòng xem lại bài: [Quản trị quyền truy cập với AWS Identity and Access Management (AWS IAM)](https://000002.awsstudygroup.com/vi/1-introduction/)

2. **Switch role**

- Tại mục **Account**, dán Account ID mà bạn đã sao chép ở bước 1, vd: `999999999943`
- Tại mục **Role**, điền **role name** bạn đã dùng trong lúc tạo Account (tại bước 1.1), vd: `OrganizationAccountAccessRole` (đây là role name được khuyến nghị bởi AWS)
- Tại mục **Display Name**, dù đây không phải thông tin bắt buộc, nhưng khuyến khích bạn đặt tên để dễ dàng nhận biết & tránh việc truy cập vào nhầm môi trường! Trong thật tế sẽ có nhiều Account được switch. Vd: `FCJ-DEV`
- Tại mục color: hãy chọn màu mà bạn thích
- Chọn **Switch Role**

**lưu ý**: nếu bạn cần thay đổi **Display Name**, chỉ cần làm lại bước 2 và thêm tên mà bạn muốn

![AWS Account](/images/11/0003.png?featherlight=false&width=90pc)

- Kết quả:

![AWS Account](/images/11/0004.png?featherlight=false&width=90pc)

Chúc mừng bạn đã Switch Role thành công!

- Kiểm tra xem bạn có quyền trên các dịch vụ phổ thông hay chưa

![AWS Account](/images/11/0004'.png?featherlight=false&width=90pc)

#### Giaỉ thích:

- Bạn có thể **truy cập** dễ dàng vào member account được tạo từ **AWS Organizations** & có đầy đủ quyền admin vì:

  - IAM User bạn dùng trong bước 1 có quyền admin.
  - Trong lúc khởi tạo account mới bằng **AWS Organizations**, với sự chấp thuận của bạn - AWS đã tự động thêm quyền admin: **AdministratorAccess** vào role **OrganizationAccountAccessRole**. Đối chiếu:

- Bạn đang đứng tại **member accouunt với Display name: FCJ-Dev**, trong khung tìm kiếm, gõ và chọn dịch vụ **IAM**
- Bên phải, chọn **Roles**

![AWS Account](/images/11/0005.png?featherlight=false&width=90pc)

- Chọn Role name: **OrganizationAccountAccessRole**

![AWS Account](/images/11/0006.png?featherlight=false&width=90pc)

- Bạn sẽ thấy quyền admin: **AdministratorAccess** với phần diễn giải **Provides full access to AWS services and resources**

![AWS Account](/images/11/0007.png?featherlight=false&width=90pc)

#### Mở rộng:

Khi bạn đã làm theo bài: [Quản trị quyền truy cập với AWS Identity and Access Management (AWS IAM)](https://000002.awsstudygroup.com/vi/1-introduction/) để tạo IAM User đăng nhập vào **management account** thì bạn cấp quyền admin: **AdministratorAccess** để thực hiện việc switch role, tức bạn không cần thêm quyền **assume role** ([**link giải thích**](https://000002.awsstudygroup.com/vi/1-introduction/1.3-iam-role/)) vì quyền admin đã bao hàm luôn quyền này.

Nhưng trong thật tế để đảm bảo tính **least privilege** cho việc cấp phát quyền tối thiểu, với vai trò quản trị viên, bạn chỉ nên cấp quyền **assume role** cho user được switch qua account - đại diện cho môi trường mà team cần.

**Ví dụ**: **AWS Organizations** của bạn có 4 account chạy workload tương ứng cho 3 môi trường: Dev, Test, Produciton và acc thứ 4 là **management account** (được AWS khuyến nghị: không nên chạy bất kỳ Workload nào, chỉ dành cho việc consolidated billing)! Vì tính chất công việc, DevLead cần duy chuyển qua lại giữa 2 môi trường Dev, Test mà không cần đăng nhập bằng User Name, Password vào 2 tài khoản AWS!

Thì lúc này, việc switch role để di chuyển giữa 2 môi trường sẽ rất nhanh chóng và tiện lợi. Vậy với vai trò quản trị viên - bạn sẽ cấp cho Dev Lead một IAM User truy cập vào **management account** chỉ có quyền **assume role** của 2 môi trường Dev, Test để thực hiện việc switch nhưng không có bất kỳ quyền gì khác trên môi trường Production.

#### Thực hành:

3. Tạo **User Groups**

- Đứng tại **management account** thực hiện lại [mục 2.1 trong bài Quản trị quyền truy cập với IAM](https://000002.awsstudygroup.com/vi/2-create-admin-user-and-group/2.1-create-admin-group/)
- Tại bước 4, **User Group Name** nhập tên Group (Ví dụ: DevGroup)
- Chọn **Create policy**, một cửa sổ mới xuất hiện

![AWS Account](/images/11/0008.png?featherlight=false&width=90pc)

4. Tạo **Customer managed Policy**

- Choose a service: gõ **STS** -> tại bên trái, chọn **STS**
  - **STS** là Security Token Service: là web service cho phép người dùng gửi request tạm thời và cấp quyền một cách giới hạn cho IAM user. Token có hiệu lực mặc định là 1 giờ
- Actions -> Select actions -> gõ `AssumeRole` -> tại chính giữa, chọn **AssumeRole**
- Resources -> Specific -> Add ARN
  - Account \*: điền member Account ID (tức ID mà bạn đã sao chép ở bước 1 phía trên) (vd: `999999999943`)
  - Role name with path \*: điền role name tại bước 1.1 (vd: `OrganizationAccountAccessRole`)
  - Chọn **Add**
- Chọn **Next: Tags**

![AWS Account](/images/11/0009.png?featherlight=false&width=90pc)

- Chọn **Next: Review**
- Name\* : điền policy name (vd:`switch_role_999999999943`)
- Chọn **Create policy**

![AWS Account](/images/11/00010.png?featherlight=false&width=90pc)

5. Gắn policy vừa tạo vào **User Groups**

- Quay lại trang **Create user group**
- Tại mục **Attach permissions policies - Optional**, chọn biểu tượng refesh

![AWS Account](/images/11/00011.png?featherlight=false&width=90pc)

- Tại khung tìm kiếm, nhập: **switch_role_999999999943**
- Tích vào ô vuông
- Chọn **Create Group**

![AWS Account](/images/11/00012.png?featherlight=false&width=90pc)

6. Tạo **User**

- Thực hiện lại [mục 2.2 trong bài Quản trị quyền truy cập với IAM](https://000002.awsstudygroup.com/vi/2-create-admin-user-and-group/2.2-create-admin-user/)
- Tại bước 2, **User name** nhập: **DevLead**,
- Tại bước 3, chọn **DevGroup**
- Hoàn thành các bước còn lại và kiểm tra IAM User vừa được tạo

![AWS Account](/images/11/00013.png?featherlight=false&width=90pc)

-> Vậy IAM User: DevLead đã được tạo & có policy name: **switch_role_999999999943** được gắn thông qua nhóm: DevGroup

**Lưu ý**: Bạn thấy rằng trong giao diện Users hay User Groups, đều có chức năng cho phép bạn gán quyền (**Add permissions**), nhưng theo best pratice:

- Bạn chỉ nên gán quyền vào User Groups
- Rồi thêm User vào trong Group, lúc đó User sẽ tự động có đầy đủ các quyền mà bạn đã trao cho Groups

-> Điều này giúp bạn dễ dàng quản lý quyền ở mức tập trung theo nhóm, tránh việc cấp quyền theo user và khó khăn trong việc quản lý vì phải vào từng user để xem chính sách quyền nào mà ta đã từng trao.

7. Đăng nhập vào **IAM User** vừa được tạo

![AWS Account](/images/11/00014.png?featherlight=false&width=90pc)

Kết quả:

![AWS Account](/images/11/00015.png?featherlight=false&width=90pc)

8. Thực hiện **switch role** qua **member account**

**lưu ý**: bạn vừa đăng nhập vào IAM User nhưng vẫn thuộc **management account**, bây giờ bạn bắt đầu thực hiện **switch role** qua **member account**.

- Thực hiện lại bước 2 phía trên

![AWS Account](/images/11/00016.png?featherlight=false&width=90pc)

Chúc mừng bạn đã **switch role** qua **member account** (ID: 999999999943) với IAM User DevLead

![AWS Account](/images/11/00017.png?featherlight=false&width=90pc)

Bạn có thể dùng chức năng **Create an AWS account** để tạo ra acc cho môi trường test và làm lại từ bước 3 đến bước 8 để switch role qua môi trường Test với ID Account tương ứng

#### B) **Switch role** vào các **member account** được mời tham gia **AWS Organization**

Khi xem lại các mục:

- 1.1 Tạo AWS Account trong AWS Organizations
- 1.3 Thêm AWS Account vào AWS Organization

-> Bạn sẽ thấy chức năng tạo AWS Account trong AWS Organizations (**Create an AWS account**) có sẵn phần tạo IAM role để management account dùng cho việc truy cập resources vào member account bằng cách **Switch role**

-> Nhưng điều trên hoàn toàn không có trong chức năng thêm AWS Account vào AWS Organization (**Invite an existing AWS account**), vậy bạn cần thêm IAM Role cho AWS Account đã được mời.

![AWS Account](/images/12/0001.png?featherlight=false&width=90pc)

1. Tạo Role có quyền admin

- Dùng **member account** mà bạn đã tham gia vào **AWS Organizations** trong mục [1.3]

- Truy cập vào **AWS Management Comsole** và tìm dịch vụ **IAM** trong thanh tìm kiếm, chọn **Roles**, chọn **Create role**

![AWS Account](/images/12/0003.png?featherlight=false&width=90pc)

- Chọn **AWS account**
- Chọn **Another AWS account**
- Điền Account ID của **management account** vào khung, vd: **999999999963**
- Chọn Next

![AWS Account](/images/12/0004.png?featherlight=false&width=90pc)

- Tại mục **Permissions policies**, nhập: `AdministratorAccess`, nhấn enter
- Tích vào ô vuông AdministratorAccess
- chọn Next

![AWS Account](/images/12/0005.png?featherlight=false&width=90pc)

- Role name: nhập `OrganizationAccountAccessRole`
- Kéo xuống cuối trang, chọn **Create role**

![AWS Account](/images/12/0006.png?featherlight=false&width=90pc)

- Kiểm tra role vừa tạo, sao chép Account ID **member account** (ID: 888800009920) bằng cách nhấn vào hình vuông

![AWS Account](/images/12/0007.png?featherlight=false&width=90pc)

2. Thực hiện switch role

- Đăng nhập vào **management account** (như bước 1 và 2 trong phần A)

- Sổ dấu tam giác phía trên cùng bên tay trái - cạnh acc name, chọn **Switch role**

![AWS Account](/images/12/0008.png?featherlight=false&width=90pc)

- Tại mục **Account**, dán Account ID mà bạn đã sao chép ở bước 1, vd: `888800009920`
- Tại mục **Role**, điền **role name** bạn đã dùng trong lúc tạo Account (tạo bước 1), vd: `OrganizationAccountAccessRole`
- Tại mục **Display Name**, dù đây không phải thông tin bắt buộc, nhưng khuyến khích bạn đặt tên để dễ dàng nhận biết & tránh việc truy cập vào nhầm môi trường! Trong thật tế sẽ có nhiều Account được switch. Vd: `FCJ_Invite_Acc`
- Tại mục color: hãy chọn màu mà bạn thích
- Chọn **Switch Role**

![AWS Account](/images/12/0009.png?featherlight=false&width=90pc)

- Chúc mừng, bằng cách Switch Role - bạn di chuyển thành công qua **member account** đã được mời vào **AWS Organizations**

![AWS Account](/images/12/00010.png?featherlight=false&width=90pc)

**Đúc kết**: Từ bước 1.1 đến bước 1.4, chúng ta đã thấy được management account sẽ là acc quản trị trong dịch vụ AWS Organization và các member account sẽ là các acc thành viên thường trực.
Ngoài ra, để member account xuất hiện trong Organization, chúng ta có hai cách:
1. Tạo acc mới bằng chức năng: Create an AWS account
2. Thêm acc đã tồn tại bằng chức năng: Invite an existing AWS account

Bên cạnh đó, chúng ta có thể đứng từ management account để truy cập vào member account qua chức năng switch role và với mỗi cách trong 2 cách trên, chúng ta lại cần các điều kiện khác nhau để switch role thành công:

1. Với cách **Create an AWS account**, việc switch role sẽ khá là đơn giản vì trong lúc khởi tạo member account chúng ta đã cho phép AWS tự động thêm role name **OrganizationAccountAccessRole** với quyền **AdministratorAccess**. Ngoài ra, chúng ta cần cấp quyền **assume role** tương ứng với member account ID cho IAM User thuộc management account

2. Với cách **Invite an existing AWS account**, việc switch role sẽ khó khăn hơn! Chúng ta cần tạo role name **OrganizationAccountAccessRole** và gán quyền **AdministratorAccess** cho account ID của management account
Ngoài ra, chúng ta cần cấp quyền **assume role** tương ứng với member account ID cho IAM User thuộc management account

Tuy nhiên, switch role không phải là cách duy nhất để truy cập vào các member acount. Tại các bước trong mục số 2, các bạn sẽ khám phá ra một cách truy cập khác thông qua việc thiết lập  AWS SSO.