+++
title = "Sử dụng Time-based access control"
date = 2025
weight = 3
chapter = false
pre = "<b> 3. </b>"
+++

Có thể có những tình huống bạn muốn cung cấp quyền truy cập cho các người dùng hoặc nhóm cụ thể trong một khoảng thời gian nhất định, như cấp quyền cho Security Auditors trong thời gian kiểm toán hoặc cho các tư vấn viên trong thời gian dự án. Trong những tình huống này, bạn có thể sử dụng permission sets với inline policies có chứa điều kiện để cung cấp time-based access control. Trong module này, chúng ta sẽ xem xét trường hợp cung cấp quyền truy cập tạm thời vào AWS accounts cho Security Auditor. Để thực hiện yêu cầu này với time-based access control, bạn cần thực hiện các bước sau:

1. Tạo Permission Set với quyền truy cập cần thiết cho Security Auditor dưới dạng inline policy với các điều kiện time-based access control
2. Tạo Group cho Security Auditors
3. Gán người dùng vào Group Security Auditors
4. Gán quyền truy cập vào AWS Account cho nhóm Security Auditors với permission set mới tạo

#### Tạo Permission Set

1. Điều hướng đến IAM Identity Center Console
2. Chọn AWS Region được đề xuất bởi AWS Team nếu đây là một phần của AWS Event. Nếu bạn đang thực hiện điều này một mình, hãy chọn Region mà bạn dự định cấu hình quy tắc.

3. Nhấp vào Permission sets trong menu bên trái dưới mục Multi-account permissions và nhấp vào nút Create permission set.

![3.4.11](/images/0003/1.png)

4. Trong trang Select permission set type:
   - Chọn radio button Custom permission set và nhấp Next.

![3.4.11](/images/0003/2.png)

5. Trong trang Specify policies:
   - Mở rộng phần Inline Policy, sau đó xóa các dấu ngoặc nhọn hiện có.
   - Sao chép và dán chính sách quyền sau vào vùng văn bản:
   - Nhấp Next
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                    "acm:Describe*",
                    "acm:List*",
                    "cloudtrail:Describe*",
                    "cloudtrail:Get*",
                    "cloudtrail:GetTrailStatus",
                    "cloudtrail:ListTags",
                    "cloudtrail:LookupEvents",
                    "cloudwatch:Describe*",
                    "cloudwatch:ListTagsForResource",
                    "config:BatchGetAggregateResourceConfig",
                    "config:BatchGetResourceConfig",
                    "config:Deliver*",
                    "config:Describe*",
                    "config:Get*",
                    "config:List*",
                    "detective:GetGraphIngestState",
                    "detective:ListGraphs",
                    "detective:ListMembers",
                    "ec2:Describe*",
                    "ec2:Get*",
                    "guardduty:DescribePublishingDestination",
                    "guardduty:Get*",
                    "guardduty:List*",
                    "iam:GenerateCredentialReport",
                    "iam:GenerateServiceLastAccessedDetails",
                    "iam:Get*",
                    "iam:List*",
                    "inspector:Describe*",
                    "kms:Describe*",
                    "kms:Get*",
                    "kms:List*",
                    "s3:Get*",
                    "s3:List*",
                    "secretsmanager:DescribeSecret",
                    "secretsmanager:GetResourcePolicy",
                    "secretsmanager:List*",
                    "securityhub:Describe*",
                    "securityhub:Get*",
                    "securityhub:List*",
                    "trustedadvisor:Describe*"
            ],
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {
                    "aws:CurrentTime": "2022-07-26T00:00:00Z"
                },
                "DateLessThan": {
                    "aws:CurrentTime": "2022-07-27T23:59:59Z"
                }
            }
        }
    ]
}
```
![3.4.11](/images/0003/3.png)
6. Trong trang Specify permission set details:
   - Cung cấp tên cho permission set, ví dụ: secAuditorTimeBased
   - Description: **Time-based read-only permissons for auditors**
   - Để các trường còn lại [Session Duration, Relay state và Tags] ở mặc định và nhấp Next
![3.4.11](/images/0003/5.png)
7. Trong trang Review and create:
   - Xem lại các chi tiết đã cung cấp trong các bước trước
   - Nhấp vào nút Create
8. Thông báo màu xanh: Permission set “secAuditorTimeBased” đã được tạo thành công.
![3.4.11](/images/0003/6.png)
#### Tạo Group

Hãy tạo Group mới có tên securityAuditors:

1. Điều hướng đến IAM Identity Center Console
2. Chọn Groups dưới mục Workplace pool và nhấp Create Group.
![3.4.11](/images/0003/7.png)
3. Trong trang Create group:
   - Cung cấp Group Name là: securityAuditors
   - Cung cấp Description, ví dụ: The audit group has read-only access to information and can only monitor events.
   - Nhấp Create group
![3.4.11](/images/0003/8.png)
4. Nhóm securityAuditors đã tạo thành công.
![3.4.11](/images/0003/9.png)
#### Tạo user và thêm vào Group

Đối với module này, chúng ta sẽ tạo một user mới: secAuditUser

1. Điều hướng đến IAM Identity Center Console
2. Chọn Users dưới mục Workplace pool và nhấp Add User.
![3.4.11](/images/0003/15.png)
3. Trong trang Add User:
   - Cung cấp Username, ví dụ: secAuditUser
   - Đối với Password, chọn radio button Generate a one-time password that you can share with the user
   - Cung cấp Email Address, sử dụng định dạng email+secaudit@domain.com
   - Xác nhận lại địa chỉ email đã cung cấp ở trường trước
   - Cung cấp First name là secAudit
   - Cung cấp Last name là user
   - Để Display name như đã nhập và nhấp Next
![3.4.11](/images/0003/16.png)
4. Trong trang Add users to groups - optional:
   - Chọn Group SecurityAuditors và nhấp Next
![3.4.11](/images/0003/17.png)
5. Trong trang Review and add user:
   - Xem lại thông tin đã cung cấp trong các bước trước và nhấp Add user
![3.4.11](/images/0003/18.png)
6. Một cửa sổ pop-up sẽ xuất hiện với One-time password. Sao chép thông tin bằng nút Copy và lưu lại để sử dụng sau trong workshop.
![3.4.11](/images/0003/19.png)
#### Gán Permission set cho AWS Account

1. Điều hướng đến IAM Identity Center Console, chọn AWS accounts dưới mục Multi-account permissions
2. Chọn tài khoản mà bạn muốn người dùng có quyền truy cập.
3. Nhấp Assign users or groups.
![3.4.11](/images/0003/10.png)
4. Trong trang Assign users and Group to AccountName:
   - Chọn Groups, chọn securityAuditors và nhấp Next.
![3.4.11](/images/0003/11.png)
5. Trong trang Select permission sets:
   - Dưới Permission sets, chọn secAuditorTimeBased và nhấp Next
![3.4.11](/images/0003/12.png)
6. Trong trang Review and submit:
   - Xem lại thông tin và nhấp Submit
![3.4.11](/images/0003/13.png)
7. IAM Identity Center sẽ liên kết User group với Permission set và gán nó cho AWS Account được chọn. Bạn sẽ thấy một trang với banner màu xanh lá.
![3.4.11](/images/0003/014.png)
#### Xác minh quyền truy cập

> **Lưu ý**:
> Để có trải nghiệm tốt hơn, bạn nên thực hiện các bước xác minh sau trong chế độ duyệt web riêng tư hoặc trình duyệt web khác

1. Đăng nhập vào AWS access Portal bằng URL User portal đã lưu khi tạo secAuditUser
2. Cung cấp username cho người dùng đã tạo trước đó trong module này

3. Cung cấp mật khẩu một lần cho username
4. Đặt mật khẩu mới cho người dùng

5. Sau khi đăng nhập thành công, trên trang SSO portal, chọn liên kết Management console cho vai trò secAuditorTimeBased

6. Sau khi đăng nhập thành công vào Management Console, điều hướng đến trang EC2 console và xác nhận rằng bạn có thể liệt kê tất cả các instances bằng cách chọn Instances trong menu bên trái

Để mô phỏng việc kiểm soát quyền truy cập cho Security Auditors, hãy cập nhật Permission set và cung cấp lại nó trong tài khoản của chúng ta. Chúng ta sẽ mô phỏng bằng cách chọn một khoảng thời gian trong quá khứ (2022-07-04).

1. Điều hướng đến IAM Identity Center Console
2. Nhấp vào Permission sets trong menu bên trái và chọn permission set secAuditorTimeBased
![3.4.11](/images/0003/027.png)

3. từ màn hình “Select permission set type chọn Custom permission set, nhấn next.
![3.4.11](/images/0003/28.png)
4. Chỉnh sửa inline policy bằng cách nhấp vào nút Edit
![3.4.11](/images/0003/29.png)
5. Sao chép và thay thế chính sách quyền bằng đoạn mã dưới đây

   Thay đổi duy nhất trong chính sách là giá trị ngày/giờ xảy ra trong quá khứ "2022-07-04T00:00:00Z" "2022-07-04T23:59:59Z"

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                    "acm:Describe*",
                    "acm:List*",
                    "cloudtrail:Describe*",
                    "cloudtrail:Get*",
                    "cloudtrail:GetTrailStatus",
                    "cloudtrail:ListTags",
                    "cloudtrail:LookupEvents",
                    "cloudwatch:Describe*",
                    "cloudwatch:ListTagsForResource",
                    "config:BatchGetAggregateResourceConfig",
                    "config:BatchGetResourceConfig",
                    "config:Deliver*",
                    "config:Describe*",
                    "config:Get*",
                    "config:List*",
                    "detective:GetGraphIngestState",
                    "detective:ListGraphs",
                    "detective:ListMembers",
                    "ec2:Describe*",
                    "ec2:Get*",
                    "guardduty:DescribePublishingDestination",
                    "guardduty:Get*",
                    "guardduty:List*",
                    "iam:GenerateCredentialReport",
                    "iam:GenerateServiceLastAccessedDetails",
                    "iam:Get*",
                    "iam:List*",
                    "inspector:Describe*",
                    "kms:Describe*",
                    "kms:Get*",
                    "kms:List*",
                    "s3:Get*",
                    "s3:List*",
                    "secretsmanager:DescribeSecret",
                    "secretsmanager:GetResourcePolicy",
                    "secretsmanager:List*",
                    "securityhub:Describe*",
                    "securityhub:Get*",
                    "securityhub:List*",
                    "trustedadvisor:Describe*"
            ],
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {
                    "aws:CurrentTime": "2022-07-04T00:00:00Z"
                },
                "DateLessThan": {
                    "aws:CurrentTime": "2022-07-04T23:59:59Z"
                }
            }
        }
    ]
}
```

6. Lưu các thay đổi vào Permission set và việc này cung cấp lại permission set cho AWS Account

7. Đăng nhập lại vào AWS access portal bằng cách làm theo các bước và xác minh quyền truy cập vào EC2 instance. Bạn sẽ thấy rằng secAuditUser không còn quyền liệt kê các EC2 instances nữa.
