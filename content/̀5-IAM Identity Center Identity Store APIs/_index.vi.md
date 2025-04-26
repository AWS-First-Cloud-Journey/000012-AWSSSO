+++
title = "IAM Identity Center Identity Store APIs"
date = 2020
weight = 5
chapter = false
pre = "<b> 5. </b>"
+++


Trong phần bài tập nâng cao này, bạn sẽ quản lý và kiểm toán các hoạt động User và Group của AWS IAM Identity Center ở quy mô lớn bằng cách sử dụng Identity Store APIs. Với các API này, bạn có thể xây dựng các quy trình tự động hóa để:

- Cấp phát và hủy cấp phát người dùng và nhóm
- Thêm thành viên mới vào nhóm hoặc xóa họ khỏi nhóm
- Truy vấn thông tin về người dùng và nhóm trong IAM Identity Center
- Cập nhật thông tin về người dùng và nhóm này
- Tìm hiểu người dùng nào là thành viên của nhóm nào

[Nhấp vào đây] để xem tài liệu tham khảo về Identity Store API

Trong phần này, bạn sẽ sử dụng script Python (được tham chiếu trong phần Environment Setup) để thực hiện các hoạt động Identitystore bằng Python boto3 SDKs.

#### Prerequisites

Trước khi bắt đầu, bạn nên có các điều kiện tiên quyết sau:

- Một Organization trong AWS Organizations
- Quyền truy cập quản trị vào AWS IAM Identity Center
- Python phiên bản 3.10.5 trở lên
- AWS CLI
- AWS SDK for Python (Boto3)
- Git

#### Environment Setup

Clone repo này:

```
git clone https://github.com/aws-samples/iam-identitycenter-identitystoreapi-operations
```

Repo này có script mẫu identitystore_operations.py sẽ được sử dụng để thực hiện các hoạt động identity store. Script này sử dụng Python SDKs. Bạn có thể tham khảo tài liệu boto3 cho các hoạt động identity store.

Dưới đây là ví dụ về phương thức create_group để tạo nhóm trong Identitystore bằng Python SDK:

```python
response = client.create_group(
    IdentityStoreId='string',
    DisplayName='string',
    Description='string'
)
```

Phương thức Create_group chấp nhận các tham số sau:

Parameters:
* **IdentityStoreId** (string) -- [REQUIRED] Định danh duy nhất toàn cầu cho identity store.
* **DisplayName** (string) -- Chuỗi chứa tên của nhóm. Giá trị này thường được hiển thị khi nhóm được tham chiếu.
* **Description** (string) -- Chuỗi chứa mô tả của nhóm.

> **Lưu ý**
> 
> Bạn có thể tham khảo tài liệu boto3 để biết chi tiết liên quan đến cú pháp yêu cầu, cú pháp phản hồi và các ngoại lệ cho hoạt động API phương thức create_group.

#### Test Setup

Trong bước này, bạn sẽ chạy script python identitystore_operations.py và xem tất cả các tùy chọn được hỗ trợ có sẵn trong script.

> **Lưu ý**
> 
> Nếu bạn không sử dụng profile mặc định, hãy đảm bảo cấu hình phiên shell của bạn với các biến môi trường trước khi chạy script.

```
python identitystore_operations.py —h
```

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
usage: identitystore_operations.py [-h]
                                   {create_user,create_group,adduser_to_group,delete_group,list_members,list_membership}
                                   ...
positional arguments:
  {create_user,create_group,adduser_to_group,delete_group,list_members,list_membership}

options:
  -h, --help            show this help message and exit
```

Như bạn có thể thấy từ đầu ra ở trên, script này hỗ trợ nhiều hoạt động IdentityStore như Create_user, Create_group, delete_group, List_members, v.v.

#### Use case Prerequisites

Trong phần này, bạn sẽ sử dụng script python để tạo hai nhóm SSO (AWS_Data_Science & AWS_Applied_Scientists) sẽ được sử dụng trong các bước sau.

Bạn sẽ cần Identity Store ID để tiếp tục với các bước còn lại.

1. Đăng nhập vào AWS account của bạn.
2. Truy cập AWS IAM Identity Center settings
3. Sao chép Identity store id từ tab identity store. Điều này sẽ được sử dụng trong bước tiếp theo.

Chạy lệnh dưới đây để tạo nhóm AWS_Data_Science:

```
python identitystore_operations.py create_group --identitystoreid d-123456a7890 --groupname AWS_Data_Science --description "My Data Science group"
```

> **Lưu ý**
> 
> Thay thế giá trị identitystoreid "d-123456a7890" bằng IdentityStore Id của bạn.

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
Group:AWS_Data_Science with GroupId:94482488-3041-7026-18f3-be45837cd0e4 created successfully
```

Tương tự, chạy lệnh dưới đây để tạo nhóm AWS_Applied_Scientists:

```
python identitystore_operations.py create_group --identitystoreid d-123456a7890 --groupname AWS_Applied_Scientists --description "Applied Scientist group"
```

> **Lưu ý**
> 
> Thay thế giá trị identitystoreid "d-123456a7890" bằng IdentityStore Id của bạn.

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
Group:AWS_Applied_Scientists with GroupId:94482488-3041-7026-18f3-be45837cd0e4 created successfully
```

#### AWS IAM Identity Center User and Group API Operations

Trong phần này, bạn sẽ sử dụng script python để tạo người dùng và cập nhật tư cách thành viên nhóm của người dùng.

#### Create User and add to the group

Trong bước này, bạn sẽ tạo một người dùng và thêm người dùng mới được tạo vào một nhóm hiện có. Bạn có thể kiểm tra mã python của hàm create_user (dòng # 9 đến # 77) trong script python identitystore_operations.py để biết chi tiết. Hàm này gọi các API create_user và create_group_membership cho hoạt động này. Cú pháp Request, Response và các ngoại lệ cho các hoạt động API này có thể được tìm thấy trong tài liệu boto3.

Hàm này tạo một người dùng và thêm người dùng vào nhóm nếu nhóm tồn tại.

Nếu nhóm không tồn tại, hàm này sẽ chỉ tạo người dùng và bỏ qua việc thêm người dùng vào nhóm.

Required parameters
-------------------
--identitystoreid - Identity Store Id của cấu hình SSO
--username  - User Name cho người dùng
--givenname - First Name cho người dùng
--familyname - Last Name cho người dùng

Optional parameters
-------------------
--groupname - Tên của nhóm SSO

Dưới đây là ví dụ về cách bạn có thể tạo một người dùng mới "John Doe" trong identity store của IAM Identity Center và thêm người dùng vào nhóm "AWS_Data_Science" hiện có.

```
python identitystore_operations.py create_user --identitystoreid d-123456a7890 --username johndoe --givenname John --familyname Doe --groupname AWS_Data_Science
```

> **Lưu ý**
> 
> Thay thế giá trị identitystoreid "d-123456a7890" bằng IdentityStore Id của bạn.

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
User:johndoe with UserId:94482488-3041-7026-18f3-be45837cd0e4 created successfully
User:johndoe added to Group:AWS_Data_Science successfully
```

#### Update User's Group Membership

Bây giờ, giả sử chuyên gia dữ liệu chuyển sang vai trò nhà khoa học ứng dụng và cần truy cập vào các ứng dụng và tài nguyên AWS bổ sung. Trước đây, bạn phải cập nhật thông tin của họ thủ công và thêm họ vào nhóm "AWS_Applied_Scientists" để họ có quyền truy cập đúng. Bây giờ, tự động hóa của bạn có thể cập nhật người dùng và cung cấp cho họ quyền truy cập họ cần. Tham khảo mã python của hàm adduser_to_group (dòng #108 đến #154) trong script python để biết chi tiết. Hàm này gọi các API get_group_id, get_user_id và create_group_membership cho hoạt động này. Cú pháp Request, Response và các ngoại lệ cho các hoạt động API này có thể được tìm thấy trong tài liệu boto3.

Dưới đây là ví dụ về cách người dùng "John Doe" đã được tạo trước đó có thể được thêm vào nhóm "AWS_Applied_Scientists":

```
python identitystore_operations.py adduser_to_group --identitystoreid d-123456a7890 --groupname AWS_Applied_Scientists --username johndoe
```

> **Lưu ý**
> 
> Thay thế giá trị identitystoreid "d-123456a7890" bằng IdentityStore Id của bạn.

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
User:johndoe added to Group:AWS_Applied_Scientists successfully
```

#### AWS IAM Identity Center User and Group Audit Operations

Trong phần này, bạn sẽ sử dụng script python để kiểm toán tư cách thành viên của người dùng và nhóm.

#### Find Members of a specific group

Dưới đây là ví dụ về cách bạn có thể tìm tất cả các thành viên của nhóm "AWS_Applied_Scientists". Tham khảo hàm list_members trong mã python (#199 đến #232) trong script để biết chi tiết. Hàm này gọi các API get_group_id và list_group_memberships cho hoạt động này. Cú pháp Response và các ngoại lệ cho các hoạt động API này có thể được tìm thấy trong tài liệu boto3.

```
python identitystore_operations.py list_members --identitystoreid d-123456a7890 --groupname AWS_Applied_Scientists 
```

> **Lưu ý**
> 
> Thay thế giá trị identitystoreid "d-123456a7890" bằng IdentityStore Id của bạn.

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
UserName:johndoe,Display Name: John Doe 
```

#### Find User's Group Membership

Dưới đây là ví dụ về cách bạn có thể tìm tư cách thành viên nhóm của một người dùng cụ thể "johndoe". Tham khảo hàm list_membership trong mã python (#235 đến #276) trong script để biết chi tiết. Hàm này thực hiện các cuộc gọi API get_user_id, list_group_memberships_for_member & describe_group cho hoạt động này. Cú pháp Response và các ngoại lệ cho các hoạt động API này có thể được tìm thấy trong tài liệu boto3.

```
python identitystore_operations.py list_membership --identitystoreid d-123456a7890 --username johndoe
```

> **Lưu ý**
> 
> Thay thế giá trị identitystoreid "d-123456a7890" bằng IdentityStore Id của bạn.

Bạn sẽ thấy đầu ra như dưới đây:

**Sample Output:**
```
User :johndoe is a member of the following groups
AWS_Data_Science
AWS_Applied_Scientists
```