+++
title = "Thêm AWS Account vào AWS Organization"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++


Ở bước 1.1, bạn đã thực hiện tạo AWS Account mới từ dịch vụ AWS Organization! Vậy nếu như bạn đã có một hoặc nhiều AWS Account với các Workload đang chạy & bạn muốn thêm AWS Account đó vào Organization của bạn để dễ dàng phân bổ tài nguyên, nhóm các accounts (như bước 1.2,) và áp dụng các nguyên tắc quản trị -> thì chức năng **Invite an existing AWS accoun** sẽ hỗ trợ bạn.

1. Thêm AWS Account vào Organizations

- Truy cập vào **AWS Management Comsole** và tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm.

- Chọn **Add an AWS account**

![AWS Account](/images/10/0001.png?featherlight=false&width=90pc)

- Chọn mục **Invite an existing AWS account**

- Tại mục **Email address or account ID of the AWS account to invite**, điền địa chỉ mail hoặc Account ID của AWS Account mà bạn muốn thêm vào Organization, ví dụ: `fcj@amazon.com.vn` hoặc 888800009920

- Chọn **Send invitation**

![AWS Account](/images/10/0002.png?featherlight=false&width=90pc)

2. Kiểm tra lời mời tham dự vào Organizations

- Tại khung bên trái, chọn **Invitations**, sẽ thấy được Account ID bạn vừa thêm tại bước 1 - đã xuất hiện ở đây với trạng thái **OPEN**

![AWS Account](/images/10/0003.png?featherlight=false&width=90pc)

3. Chấp nhận lời mời tham dự vào Organizations

- Truy cập vào **AWS Management Comsole** của Account bạn vừa thêm tại bước 1, tìm dịch vụ **AWS Organizations** trong thanh tìm kiếm

![AWS Account](/images/10/0004.png?featherlight=false&width=90pc)

- Tại bên phải màn hình, chọn lời mời **View 1 invitation**
- Ngoài ra, dịch vụ AWS Organization không bị tính phí

![AWS Account](/images/10/0005.png?featherlight=false&width=90pc)

**Lưu ý**: bạn chỉ có thể nhìn thấy lời mời trên, khi và chỉ khi AWS Account này chưa tham gia vào bất kỳ **AWS Organizations**

4. Chọn **Accept invitation**

![AWS Account](/images/10/0006.png?featherlight=false&width=90pc)

- Kết quả:

![AWS Account](/images/10/0007.png?featherlight=false&width=90pc)

- Dù bạn đang ở **Dashboard** nhưng bạn chỉ thấy được thông tin của **Organizations** mà bạn đang tham dự, vì bạn đang là thành viên (member account)

5. Kiểm tra **AWS Organizations**

- Quay trở lại AWS Account ở bước 1, kiểm tra xem Account vừa được thêm tại bước 4 đã tham gia vào Organizations hay chưa

![AWS Account](/images/10/0008.png?featherlight=false&width=90pc)

- Tại đây, bạn có thể nhìn thấy toàn bộ cấu trúc của **Organizations** bao gồm các Organization Unit với các member account & management account.

- Với **management account** sẽ là acc chính để quản lý và truy cập vào các **member account** thông qua chức năng **switch role**

Chúc mừng, AWS Account đã được thêm vào với thông tin chi tiết về ngày tham gia
