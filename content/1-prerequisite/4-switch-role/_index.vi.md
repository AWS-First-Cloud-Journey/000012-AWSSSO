+++
title = "Tạo Permission Sets"
date = 2025
weight = 4
chapter = false
pre = "<b>1.4 </b>"
+++

#### Tạo Permission Sets

**ℹ️ Thông tin:** Permission sets là cơ chế để định nghĩa quyền hạn tập trung trong IAM Identity Center, cho phép áp dụng các quyền này một cách nhất quán trên tất cả AWS accounts trong tổ chức của bạn. Mỗi permission set được triển khai dưới dạng IAM role trong từng AWS account được chỉ định.

#### Các bước thực hiện

Trong workshop này, chúng ta sẽ tạo hai permission sets: AdministratorAccess và readOnly để minh họa các cấp độ quyền truy cập khác nhau.

1. Điều hướng đến IAM Identity Center Console
2. Chọn AWS Region được đề xuất bởi AWS Team nếu đây là một phần của AWS Event. Nếu bạn đang thực hiện điều này một mình, hãy chọn Region gần với vị trí địa lý của bạn để tối ưu hóa độ trễ.

3. Nhấp vào **Permission sets** ở menu bên trái dưới mục Multi-account permissions và nhấp vào nút **Create permission set**

![3.4.11](/images/0001/image14.png)

4. Trên trang Select permission set type:
   - Dưới mục Permission set type, chọn **Predefined permission set**
   - Dưới mục Policy for predefined permission set, chọn AWS managed policy **AdministratorAccess** sau đó nhấp vào **Next**

![3.4.11](/images/0001/image15.png)

5. Trên trang Specify permission set details, nhập Permission set name: **AdministratorAccess** giữ tất cả các giá trị mặc định và nhấp vào **Next**

![3.4.11](/images/0001/image16.png)

6. Trên trang Review and create, xem lại các lựa chọn bạn đã thực hiện, sau đó nhấp vào **Create**

![3.4.11](/images/0001/image17.png)

**ℹ️ Thông tin:** Sau khi permission set được tạo, bạn sẽ thấy một trang xác nhận việc tạo permission set thành công. IAM Identity Center sẽ tự động tạo IAM role tương ứng trong mỗi AWS account khi bạn gán permission set này cho users hoặc groups.

![3.4.11](/images/0001/image18.png)

#### Tạo Permission Set cho quyền truy cập chỉ đọc

Tương tự, hãy tạo một permission set khác cho quyền truy cập chỉ đọc:

1. Trên trang Select permission set type:
   - Dưới mục Permission set type, chọn **Predefined permission set**

![3.4.11](/images/0001/image19.png)

   - Dưới mục Policy for predefined permission set, chọn AWS managed policy **ViewOnlyAccess** sau đó nhấp vào **Next**

2. Trên trang Specify permission set details:
   - Dưới mục Permission set name, nhập **readOnly**
   - Để các trường còn lại [Description, Session Duration, Relay state và Tags] ở giá trị mặc định
   - Nhấp vào **Next**

![3.4.11](/images/0001/image20.png)

3. Trên trang Review and create, xem lại các lựa chọn bạn đã thực hiện, sau đó nhấp vào **Create**

![3.4.11](/images/0001/image21.png)

**ℹ️ Thông tin:** Sau khi permission set được tạo, bạn sẽ thấy một trang xác nhận việc tạo permission set thành công. IAM Identity Center sẽ tự động tạo IAM role tương ứng trong mỗi AWS account khi bạn gán permission set này cho users hoặc groups.

![3.4.11](/images/0001/image211.png)

**💡 Pro Tip:** Ngoài các predefined permission sets, bạn có thể tạo custom permission sets bằng cách kết hợp nhiều AWS managed policies hoặc tạo customer managed policies với JSON. Điều này cho phép bạn triển khai các quyền hạn chi tiết theo nguyên tắc least privilege, phù hợp với yêu cầu cụ thể của tổ chức.

**🔒 Security Note:** Permission sets trong IAM Identity Center hỗ trợ các tính năng bảo mật nâng cao như giới hạn thời gian phiên (session duration), điều kiện truy cập (access requirements), và khả năng tích hợp với AWS CloudTrail để ghi nhật ký hoạt động. Trong môi trường sản xuất, hãy cân nhắc việc thiết lập các giới hạn phiên ngắn hơn và yêu cầu xác thực đa yếu tố (MFA) cho các permission sets có quyền hạn cao.

**ℹ️ Thông tin:** IAM Identity Center tự động quản lý vòng đời của IAM roles được tạo từ permission sets, bao gồm cả việc cập nhật khi bạn thay đổi cấu hình permission set. Điều này giúp đơn giản hóa việc quản lý quyền truy cập trên quy mô lớn và đảm bảo tính nhất quán trong toàn bộ AWS Organization.

Bạn đã tạo thành công hai Permission Sets mới, bây giờ hãy chuyển sang bước cung cấp quyền truy cập cho users và groups.