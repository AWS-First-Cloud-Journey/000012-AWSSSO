+++
title = "Tạo User và Groups trong IAM Identity Center"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3 </b>"
+++

#### Tạo User và Groups trong IAM Identity Center

**ℹ️ Thông tin:** Phần này hướng dẫn tạo users và groups trong kho danh tính (identity store) tích hợp của IAM Identity Center. Nếu bạn muốn cấu hình External Identity Provider (IdP) làm identity source, hãy tham khảo phần "Sử dụng External IdP với IAM Identity Center" trong mục Extra Credit.

#### Chọn nguồn danh tính (identity source)

**ℹ️ Thông tin:** Việc chọn identity source xác định nơi IAM Identity Center tìm kiếm users và groups cần quyền truy cập SSO. Theo mặc định, IAM Identity Center cung cấp một identity store tích hợp để quản lý nhanh chóng và dễ dàng. Đây là lựa chọn tốt cho các tổ chức nhỏ hoặc môi trường thử nghiệm.

**💡 Pro Tip:** Đối với môi trường doanh nghiệp, bạn có thể kết nối IAM Identity Center với Microsoft Active Directory (thông qua AWS Directory Service) hoặc nhà cung cấp định danh bên ngoài tương thích SAML 2.0 như Okta, Microsoft Entra ID (trước đây là Azure AD), hoặc Google Workspace.

#### Quản lý danh tính trong IAM Identity Center

Users và groups bạn tạo trong IAM Identity Center identity store chỉ có sẵn trong IAM Identity Center. Hãy làm theo quy trình sau để thêm users và groups vào identity store của bạn.

#### Các bước thực hiện

#### 1. Tạo Groups

**ℹ️ Thông tin:** Trong workshop này, chúng ta sẽ tạo 2 groups: Administrators và readOnly. Groups giúp tổ chức users theo vai trò và trách nhiệm, đơn giản hóa việc quản lý quyền truy cập.

1. Điều hướng đến IAM Identity Center Console
2. Chọn **Groups** và nhấp vào **Create Group**

![3.4.11](/images/0001/0005.png)

3. Trong trang Create group:
   - Nhập Group Name, ví dụ: **Administrators**
   - Nhập Description, ví dụ: **Group for administrator users**
   - Nhấp vào **Create group**

![3.4.11](/images/0001/0006.png)

4. Một banner màu xanh lá sẽ xuất hiện cho biết group Administrators đã được tạo thành công
5. Lặp lại các bước 1-3 để tạo group **readOnly**

![3.4.11](/images/0001/0007.png)

**💡 Pro Tip:** Việc tổ chức users thành các groups giúp quản lý quyền truy cập hiệu quả hơn và dễ dàng áp dụng các chính sách quyền hạn theo vai trò. Khi cấu trúc tổ chức thay đổi, bạn chỉ cần cập nhật thành viên group thay vì phải điều chỉnh quyền cho từng user riêng lẻ.

**🔒 Security Note:** Tuân thủ nguyên tắc least privilege bằng cách tạo các groups với quyền hạn cụ thể và giới hạn. Điều này giúp giảm thiểu rủi ro bảo mật và đơn giản hóa việc kiểm toán quyền truy cập.

#### 2. Tạo Users

**ℹ️ Thông tin:** Trong workshop này, chúng ta sẽ tạo hai users: adminUser và readOnlyUser để minh họa các cấp độ quyền truy cập khác nhau.

1. Điều hướng đến IAM Identity Center Console
2. Chọn **Users** dưới Workplace pool và nhấp vào **Add User**

![3.4.11](/images/0001/0008.png)

3. Trong trang Add User:
   - Nhập Username, ví dụ: **adminUser**
   - Đối với Password, chọn tùy chọn **Generate a one-time password that you can share with the user**
   - Nhập Email Address, sử dụng định dạng email+admin@domain.com
   - Xác nhận lại địa chỉ email đã nhập
   - Nhập First name
   - Nhập Last name
   - Để Display name như đã nhập
   - Nhấp vào **Next** (bạn có thể khám phá các trường tùy chọn)

![3.4.11](/images/0001/0009.png)

4. Trong trang Add users to groups - optional:
   - Chọn group **Administrators**
   - Nhấp vào **Next**

![3.4.11](/images/0001/00010.png)

5. Trong trang Review and add user:
   - Xem lại thông tin đã cung cấp trong các bước trước
   - Nhấp vào **Add user**

![3.4.11](/images/0001/00011.png)

6. Một cửa sổ pop-up sẽ xuất hiện với One-time password. Sao chép thông tin bằng nút Copy và lưu lại để sử dụng sau trong workshop.

![3.4.11](/images/0001/00012.png)

**🔒 Security Note:** Mật khẩu một lần (one-time password) chỉ hiển thị một lần và không thể truy xuất lại. Hãy đảm bảo lưu trữ an toàn và chia sẻ với người dùng qua kênh bảo mật. Trong môi trường sản xuất, bạn nên kích hoạt xác thực đa yếu tố (MFA) cho tất cả người dùng để tăng cường bảo mật.

**⚠️ Warning:** Làm theo các bước 1-6 để tạo user **readOnlyUser**. Sử dụng một email duy nhất và khác với email của admin user cho readOnlyUser (tương tự như username+readOnly@domain.com) và đảm bảo gán user này vào group readOnly ở Bước 4.

**💡 Pro Tip:** IAM Identity Center hỗ trợ quản lý vòng đời người dùng (user lifecycle management) bao gồm tạo mới, cập nhật, vô hiệu hóa và xóa người dùng. Trong môi trường doanh nghiệp, bạn có thể tự động hóa các quy trình này thông qua tích hợp với hệ thống HR hoặc sử dụng AWS APIs.

Bạn đã tạo thành công hai users và groups mới. Sử dụng IAM Identity Center, những users này sẽ có thể truy cập nhiều AWS accounts trong AWS Organizations với quyền hạn phù hợp dựa trên vai trò của họ.
