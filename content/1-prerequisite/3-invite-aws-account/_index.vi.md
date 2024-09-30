+++
title = "Thêm AWS Account vào AWS Organization"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Mục tiêu

Ở bước 1.1, bạn đã thực hiện tạo AWS Account mới từ dịch vụ AWS Organizations! Vậy nếu bạn đã có một hoặc nhiều AWS Account với các Workload đang chạy và bạn muốn thêm các AWS Account đó vào Organization của bạn để dễ dàng phân bổ tài nguyên, nhóm các accounts (như bước 1.2,) và áp dụng các nguyên tắc quản trị -> chức năng **Invite an existing AWS account** sẽ hỗ trợ bạn trong trường hợp này.

#### Hướng dẫn chi tiết

#### 1. Thêm AWS Account vào Organizations

1. Truy cập vào **AWS Management Console** và tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm.
   
2. Tại trang **AWS Organizations**, chọn **Add an AWS account**.

   ![AWS Account](/images/10/0001.png?featherlight=false&width=90pc)

3. Chọn mục **Invite an existing AWS account**.

4. Trong mục **Email address or account ID of the AWS account to invite**, nhập địa chỉ email hoặc Account ID của AWS Account mà bạn muốn thêm vào Organization (ví dụ: `fcj@amazon.com.vn` hoặc `888800009920`).

5. Chọn **Send invitation** để gửi lời mời.

   ![AWS Account](/images/10/0002.png?featherlight=false&width=90pc)

#### 2. Kiểm tra lời mời tham gia vào Organization

1. Truy cập lại trang **AWS Organizations**.

2. Tại khung bên trái, chọn **Invitations**, bạn sẽ thấy được Account ID mà bạn vừa thêm tại bước 1 xuất hiện tại đây với trạng thái **OPEN**.

   ![AWS Account](/images/10/0003.png?featherlight=false&width=90pc)

#### 3. Chấp nhận lời mời tham gia vào Organization

1. Đăng nhập vào **AWS Management Console** của AWS Account mà bạn vừa thêm tại bước 1.

2. Tìm kiếm và truy cập dịch vụ **AWS Organizations** trong thanh tìm kiếm.

   ![AWS Account](/images/10/0004.png?featherlight=false&width=90pc)

3. Tại bên phải màn hình, bạn sẽ thấy thông báo **View 1 invitation**, chọn để xem chi tiết lời mời.

4. Nhấn **Accept invitation** để chấp nhận lời mời tham gia vào Organization.

   ![AWS Account](/images/10/0005.png?featherlight=false&width=90pc)

**Lưu ý**: Bạn chỉ có thể nhìn thấy lời mời nếu AWS Account này chưa tham gia vào bất kỳ **AWS Organizations** nào trước đó.

#### 4. Xác nhận lời mời

1. Sau khi chấp nhận lời mời, bạn sẽ nhận được thông báo xác nhận và AWS Account của bạn sẽ được liên kết với **AWS Organizations**.

   ![AWS Account](/images/10/0006.png?featherlight=false&width=90pc)

2. Dù bạn đang ở **Dashboard**, bạn chỉ có thể nhìn thấy thông tin của **Organization** mà bạn đang tham gia với vai trò là **Member Account** (thành viên).

   ![AWS Account](/images/10/0007.png?featherlight=false&width=90pc)

#### 5. Kiểm tra trạng thái của AWS Organizations

1. Truy cập vào AWS Management Console của **Management Account** (tài khoản quản lý chính).

2. Quay lại trang **AWS Organizations** và kiểm tra trạng thái của AWS Account mà bạn đã thêm ở bước trước. Nếu thành công, Account mới sẽ xuất hiện trong danh sách với trạng thái **Active**.

   ![AWS Account](/images/10/0008.png?featherlight=false&width=90pc)

3. Bạn có thể xem cấu trúc **Organization** hiện tại bao gồm các **Organization Units (OUs)**, **Member Accounts**, và **Management Account**.

   - **Management Account** là tài khoản chính để quản lý và truy cập vào các **Member Account** thông qua chức năng **Switch Role**.
   
#### Kết luận

Chúc mừng bạn đã thêm thành công một AWS Account vào Organization! Bạn có thể bắt đầu quản lý tài nguyên và áp dụng các nguyên tắc bảo mật và quản trị một cách dễ dàng.

