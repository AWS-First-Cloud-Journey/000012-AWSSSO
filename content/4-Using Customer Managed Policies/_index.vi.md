+++
title = "Customer Managed Policies"
date = 2020
weight = 4
chapter = false
pre = "<b> 4. </b>"
+++


Khi sử dụng Identity Center, có những tình huống bạn muốn tái sử dụng các chính sách quyền IAM hiện có trong permission sets của mình, chẳng hạn như:

- Bạn muốn vai trò (role) giống nhau trên tất cả các AWS accounts nhưng cần cách để điều chỉnh các chính sách trong từng tài khoản để tham chiếu đến các tài nguyên cụ thể của họ
- Bạn sử dụng Identity Center như một giải pháp thay thế cho federation trên từng tài khoản, nhưng cần cách để tái sử dụng customer managed policies mà bạn đã tạo

Việc hỗ trợ Customer Managed Policies (CMP) với permission set giải quyết các yêu cầu này. Trong module này, bạn sẽ đi qua một kịch bản nơi CMPs có thể được sử dụng để giải quyết các yêu cầu cụ thể.

> **Lưu ý**
> 
> Trước khi gán permission set với các chính sách IAM, bạn phải chuẩn bị member account của mình. Tên của chính sách IAM trong member account phải khớp phân biệt chữ hoa chữ thường với tên của chính sách trong management account. IAM Identity Center không thể gán permission set nếu chính sách không tồn tại trong member account. Quyền mà chính sách cấp không nhất thiết phải khớp chính xác giữa các tài khoản.

#### Kịch bản

Xem xét một kịch bản mà nhóm vận hành (operator group) cần được cấp quyền truy cập vào các member accounts khác nhau và quyền truy cập của họ vào các tài khoản nên được giới hạn trong các AWS CloudWatch log groups trong các tài khoản đó. Yêu cầu này có thể được giải quyết bằng Customer Managed Policies (CMPs) nơi một chính sách operatorAccess có thể được tạo trong mỗi AWS account, với các chính sách và quyền truy cập/cấp phép thực tế chỉ cho phép thực hiện các hoạt động CloudWatch đối với các log groups của tài khoản được chỉ định. Sau đó, bạn có thể tạo permission sets gắn với CMP operatorAccess cho phép các hoạt động CloudWatch đối với log group của các tài khoản được chỉ định. Trong phần còn lại của module này, bạn sẽ thực hiện các bước tạo CMP, tạo permission set bằng cách gắn CMP đã tạo và cuối cùng là cung cấp permission set cho AWS account.

#### Tạo Customer Managed IAM Policy

1. Theo [link này] để tạo IAM policy
2. Chọn tab JSON và sao chép và dán đoạn chính sách sau vào khu vực văn bản
3. Thay thế `<account-id>` bằng ID tài khoản cho tài khoản mà chính sách này được tạo
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "logs:CreateLogStream",
                "logs:DescribeLogStreams",
                "logs:PutLogEvents",
                "logs:GetLogEvents"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:logs:us-east-1:<account-id>:log-group:OperationsLogGroup:*"
        },
        {
            "Action": [
                "logs:DescribeLogGroups"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:logs:us-east-1:<account-id>:log-group::log-stream:*"
        }
    ]
}
```

4. Nhấp Next: Tags (Tags là tùy chọn)
5. Nhấp Next: Review.
6. Trên trang Create Policy, cung cấp:
   - Tên của policy là `operatorAccess`
   - Cung cấp mô tả
   - Nhấp Create Policy

#### Tạo permission Set với Customer Managed policy

1. Điều hướng đến IAM Identity Center Console
2. Chọn AWS Region được đề xuất bởi AWS Team nếu đây là một phần của AWS Event hoặc Region mà bạn dự định cấu hình quy tắc, nếu bạn đang chạy điều này một mình

3. Nhấp vào Permission sets trong menu bên trái và nhấp vào nút Create permission set

4. Trong trang Select permission set type:
   - Chọn radio button Custom permission set
   - Nhấp Next

5. Trong trang Specify policies:
   - Mở rộng tùy chọn "Customer managed Policies"
   - Nhấp vào "Attach policies"
   - Trong hộp văn bản hiển thị "Enter Policy name(s)", nhập "operatorAccess". Tên này phải khớp với tên của policy mà bạn đã tạo trong phần Create Customer Managed IAM policy.
   - Nhấp Next

6. Trong trang Specify permission set details:
   - Cung cấp tên cho permission set, ví dụ: operatorAccessPermissionSet
   - Để các trường còn lại [Description, Session Duration, Relay state và Tags] ở mặc định
   - Nhấp Next

7. Trong trang Review and create:
   - Xem lại các chi tiết đã cung cấp trong các bước trước
   - Nhấp vào nút Create

#### Tạo Group

Hãy tạo Group mới có tên operations:

1. Điều hướng đến IAM Identity Center Console
2. Chọn Groups dưới mục Workplace pool và nhấp Create Group.
3. Trong trang Create group:
   - Cung cấp Group Name là operations
   - Cung cấp Description, ví dụ: Group for cloud operations
   - Nhấp Create group

#### Tạo user và thêm vào Group

Đối với module này, chúng ta sẽ tạo một user mới: operationsUser

1. Điều hướng đến IAM Identity Center Console
2. Chọn Users dưới mục Workplace pool và nhấp Create User.

3. Trong trang Create User:
   - Cung cấp Username, ví dụ: operationsUser
   - Đối với Password, chọn radio button Generate a one-time password that you can share with the user
   - Cung cấp Email Address, sử dụng định dạng email+operations@domain.com, ví dụ: example+operations@amazon.com
   - Xác nhận lại địa chỉ email đã cung cấp ở trường trước
   - Cung cấp First name là operations
   - Cung cấp Last name là user
   - Để Display name như đã nhập
   - Nhấp Next

4. Trong trang Add users to groups - optional:
   - Chọn Group Operations
   - Nhấp Next

5. Trong trang Review and add user:
   - Xem lại thông tin đã cung cấp trong các bước trước
   - Nhấp Add user

6. Một cửa sổ pop-up sẽ xuất hiện với One-time password. Sao chép thông tin bằng nút Copy và lưu lại cho bước xác thực. Lưu ý User portal URL, Username và Password

#### Gán Permission set cho AWS Account

1. Điều hướng đến IAM Identity Center Console, chọn AWS accounts
2. Chọn tài khoản mà bạn muốn người dùng có quyền truy cập.
3. Nhấp Assign users or groups.

4. Trong trang Assign users and Group to AccountName:
   - Chọn nhóm operations
   - Nhấp Next

5. Trong trang Select permission sets:
   - Dưới Permission sets, chọn operatorAccessPermissionSet
   - Nhấp Next

6. Trong trang Review and submit:
   - Xem lại thông tin
   - Nhấp Submit

7. IAM Identity Center sẽ liên kết User group với Permission set và gán nó cho AWS Account được chọn. Bạn sẽ thấy một trang với banner màu xanh lá.

#### Xác minh quyền truy cập

> **Lưu ý**:
> Để có trải nghiệm tốt hơn, bạn nên thực hiện các bước xác minh sau trong chế độ duyệt web riêng tư hoặc trình duyệt web khác

1. Đăng nhập vào AWS Portal bằng User portal URL đã lưu khi tạo operationsUser
2. Cung cấp username cho người dùng đã tạo trước đó trong module này

3. Cung cấp mật khẩu một lần cho username
4. Đặt mật khẩu mới cho người dùng

5. Sau khi đăng nhập thành công, trên trang Identity Center portal, chọn liên kết Management console cho vai trò operatorAccessPermissionSet

6. Sau khi đăng nhập thành công vào Management Console, điều hướng đến trang CloudWatch Log groups và xác nhận rằng bạn có thể liệt kê các log groups OperationsLogGroup hiện có và tạo log stream mới trong đó thành công

Module này chứng minh cách AWS IAM Identity Center hoạt động với customer managed policies mà bạn tạo trong AWS account của mình. Mặc dù module đã tạo CMP và permission set và cung cấp nó trong một tài khoản duy nhất, bạn có thể tạo CMP với cùng tên trong tất cả các member account và sử dụng cùng permission set operatorAccessPermissionSet và cung cấp nó trên tất cả các member accounts của bạn.
