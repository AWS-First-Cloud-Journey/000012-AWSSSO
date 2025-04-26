+++
title = "Kiểm tra quyền truy cập"
date = 2020
weight = 6
chapter = false
pre = "<b> 1.6 </b>"
+++

#### Kiểm tra quyền truy cập dựa trên người dùng, nhóm và permission set

**ℹ️ Thông tin:** Trong phần này, bạn sẽ xác thực thiết lập đã thực hiện để cấu hình IAM Identity Center quản lý quyền của người dùng và nhóm trên các AWS account bằng cách triển khai một AWS CloudFormation Stack chứa các tài nguyên AWS. Template CloudFormation sẽ triển khai các tài nguyên bao gồm 2 VPC, public và private subnet, EC2 instance và một số VPC Security Group.

#### Triển khai CloudFormation Template

1. Tải xuống [Template](https://static.us-east-1.prod.workshops.aws/public/3fac600e-c0e3-4410-9a4f-8ca05b549ec7/static/iam-identitycenter-validation.yml)
2. Điều hướng đến [CloudFormation console](https://console.aws.amazon.com/cloudformation/)
3. Nhấp vào **Create stack**, chọn **With new resources (standard)**
4. Trong trang Create stack:
   - Chọn **Template is ready** cho Prepare template
   - Chọn **Upload a template file** cho Template source
   - Nhấp vào **Choose file** và chọn tệp đã tải xuống ở bước 1


![3.4.11](/images/0003/0001.png)


5. Trong trang Specify stack details:
   - Đặt tên stack của bạn, ví dụ: **iam-identitycenter-validation-setup**
   - Để giá trị tham số **LatestAmiId** ở mặc định và nhấp **Next**

![3.4.11](/images/0003/0002.png)

6. Để mọi thứ ở mặc định trong trang Configure stack options. Cuộn xuống dưới và nhấp **Next**

![3.4.11](/images/0003/0003.png)

7. Trong trang Review, cuộn xuống dưới và nhấp **Submit**

![3.4.11](/images/0003/0004.png)

**ℹ️ Thông tin:** Việc triển khai CloudFormation Stack sẽ mất khoảng 5 phút để hoàn thành. Bạn có thể xác nhận rằng việc triển khai đã hoàn tất bằng cách xác thực trạng thái là **CREATE_COMPLETE**.


![3.4.11](/images/0003/0005.png)


#### Xác thực quyền truy cập

**⚠️ Cảnh báo:** Để có trải nghiệm tốt hơn, bạn nên thực hiện các bước xác thực sau trong chế độ duyệt web riêng tư hoặc trình duyệt web khác để tránh xung đột phiên đăng nhập.

#### Kiểm tra quyền Administrator

1. Đăng nhập vào AWS Access Portal sử dụng URL AWS Access Portal đã lưu khi tạo adminUser
2. Cung cấp tên người dùng cho người dùng đã tạo trước đó trong module này
3. Cung cấp mật khẩu một lần cho tên người dùng
4. Đặt mật khẩu mới cho người dùng

5. Sau khi đăng nhập thành công, trên trang AWS portal, chọn liên kết **Management console** cho vai trò **AdministratorAccess**
6. Sau khi đăng nhập thành công vào Management Console, điều hướng đến trang EC2 console
7. Chọn một instance đang chạy
8. Trên menu thả xuống Instance state, chọn **Stop instance**

**ℹ️ Thông tin:** Bạn sẽ thấy một trang với banner màu xanh lá xác nhận instance đã dừng thành công. Điều này chứng minh rằng người dùng có quyền Administrator có thể thực hiện các thao tác thay đổi trạng thái tài nguyên.

9. Đăng xuất khỏi cả AWS Management console và trang AWS Portal

#### Kiểm tra quyền ReadOnly

1. Đăng nhập vào AWS Access Portal sử dụng readOnlyUser
2. Cung cấp mật khẩu một lần cho tên người dùng
3. Đặt mật khẩu mới cho người dùng

4. Sau khi đăng nhập thành công, trên trang AWS Access portal, chọn liên kết **Management console** cho vai trò **readOnly**
5. Sau khi đăng nhập thành công vào Management Console, điều hướng đến trang EC2 console
6. Chọn một instance đang chạy
7. Trên menu thả xuống Instance state, chọn **Stop instance**

**🔒 Security Note:** Bạn sẽ thấy một trang với banner màu đỏ thông báo "Failed to stop the instance". Điều này xác nhận rằng người dùng chỉ có quyền đọc không thể thực hiện các hành động thay đổi trạng thái, đảm bảo nguyên tắc phân quyền tối thiểu (least privilege) đang hoạt động đúng.

**💡 Pro Tip:** Việc kiểm tra quyền truy cập theo cách này giúp xác minh rằng cấu hình IAM Identity Center của bạn đang hoạt động chính xác và các permission set đã được áp dụng đúng cách cho các nhóm người dùng khác nhau. Trong môi trường sản xuất, bạn nên thực hiện kiểm tra này định kỳ như một phần của quy trình kiểm toán bảo mật để đảm bảo các quyền truy cập luôn được duy trì đúng cách.