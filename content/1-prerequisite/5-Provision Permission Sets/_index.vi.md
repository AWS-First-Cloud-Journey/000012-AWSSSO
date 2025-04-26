+++
title = "Cung cấp Permission Sets"
date = 2020
weight = 5
chapter = false
pre = "<b>1.5 </b>"
+++

#### Cung cấp Permission Sets

**ℹ️ Thông tin:** Theo mặc định, khi bạn tạo một permission set, nó chưa được cung cấp (chưa được áp dụng trong bất kỳ AWS account nào). Để kích hoạt permission set trong một AWS account, bạn cần gán quyền truy cập IAM Identity Center cho users và groups trong account đó, sau đó áp dụng permission set cho những users và groups này.

#### Các bước thực hiện

1. Điều hướng đến IAM Identity Center Console, chọn **AWS accounts** và chọn một account mà bạn muốn người dùng có quyền truy cập. Nhấp vào **Assign users or groups**.

![3.4.11](/images/0002/0009.png)

2. Trong trang Select users and groups:
   - Chọn tab **Groups**
   - Chọn group **Administrators**
   - Nhấp vào **Next**

![3.4.11](/images/0002/00010.png)

3. Trong trang Select permission sets:
   - Dưới mục Permission sets, chọn **AdministratorAccess**
   - Nhấp vào **Next**

![3.4.11](/images/0002/00011.png)

4. Trong trang Review and submit:
   - Xem lại thông tin đã cung cấp
   - Nhấp vào **Submit**

![3.4.11](/images/0002/00012.png)

**ℹ️ Thông tin:** IAM Identity Center sẽ liên kết User group với Permission set và gán nó cho (các) AWS Account đã chọn. Bạn sẽ thấy một trang với banner màu xanh lá xác nhận việc cung cấp thành công.

#### Cung cấp Permission Set khác cho cùng một account

1. Trong IAM Identity Center Console, chọn **AWS accounts** và chọn cùng account mà bạn đã sử dụng ở trên. Nhấp vào **Assign users or groups**.

![3.4.11](/images/0002/00013.png)

2. Trong trang Select users and groups:
   - Chọn tab **Groups**
   - Chọn group **readOnly**
   - Nhấp vào **Next**

![3.4.11](/images/0002/00014.png)

3. Trong trang Select permission sets:
   - Dưới mục Permission sets, chọn **readOnly**
   - Nhấp vào **Next**

![3.4.11](/images/0002/00015.png)

4. Trong trang Review and submit:
   - Xem lại thông tin đã cung cấp
   - Nhấp vào **Submit**

![3.4.11](/images/0002/00016.png)

![3.4.11](/images/0002/00017.png)

**💡 Pro Tip:** Kiểm tra các roles xuất hiện bên cạnh account nơi bạn đã cung cấp permission sets. Điều này giúp xác nhận rằng các quyền đã được áp dụng đúng cách và IAM Identity Center đã tạo các IAM roles tương ứng trong account đó.

![3.4.11](/images/0002/00018.png)

**🔒 Security Note:** Việc phân quyền theo nhóm (group-based permissions) giúp quản lý quyền truy cập hiệu quả hơn và dễ dàng duy trì khi tổ chức phát triển. Đây là phương pháp tốt nhất để triển khai mô hình least privilege access và tuân thủ các nguyên tắc Zero Trust. Khi cấu trúc tổ chức thay đổi, bạn chỉ cần cập nhật thành viên group thay vì phải điều chỉnh quyền cho từng user riêng lẻ.

**ℹ️ Thông tin:** Khi permission set được cung cấp, IAM Identity Center tự động tạo và quản lý IAM roles tương ứng trong mỗi AWS account được chỉ định. Điều này giúp đơn giản hóa việc quản lý quyền truy cập trên quy mô lớn và đảm bảo tính nhất quán trong toàn bộ AWS Organization.

Bạn đã cung cấp thành công Permission Sets cho AWS account. Bây giờ hãy chuyển sang kiểm tra thiết lập.
