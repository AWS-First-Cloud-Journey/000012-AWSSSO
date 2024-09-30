+++
title = "Gán quyền"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++

#### Gán Quyền Truy Cập cho Người Dùng và Nhóm

Hướng dẫn này sẽ giúp bạn thiết lập quyền truy cập AWS cho người dùng và nhóm bằng cách sử dụng AWS Single Sign-On (SSO). Hãy làm theo các bước chi tiết dưới đây để đảm bảo rằng người dùng của bạn có các quyền truy cập phù hợp theo chức năng công việc.

#### Bảng phân quyền truy cập

| **Tài Khoản**                                | **Nhóm**                                     | **Chính Sách Công Việc**     |
|----------------------------------------------|---------------------------------------------|-----------------------------|
| `Management Account`, `shared-services`, `logging`, `security` | AWS-Shared-Services-Admin; AWS-Security-Admin; AWS-Logging-Admin             | `AdministratorAccess`       |
| `Management Account`, `shared-services`, `logging`, `security` | AWS-Shared-Services-Read-Only; AWS-Security-Read-Only; AWS-Logging-Read-Only | `SecurityAudit`             |

#### Hướng dẫn chi tiết

#### 1. Mở AWS SSO Console
- Điều hướng đến AWS SSO Console.
- Ở thanh điều hướng bên trái, chọn **AWS accounts**.
  
  ![AWS Account](/images/8/0001.png?featherlight=false&width=90pc)

- Trong tab **AWS organization**, duyệt danh sách các tài khoản AWS hiện có.
- Chọn một hoặc nhiều tài khoản mà bạn muốn gán quyền truy cập. Ví dụ: `Management Account`, `shared-services`, `logging`, và `security`.
- Nhấn **Assign users or groups** để tiến hành gán quyền cho các nhóm hoặc người dùng.

#### 2. Chọn nhóm người dùng
- Trong danh sách các nhóm, chọn nhóm bạn muốn gán quyền (ví dụ: `AWS-Shared-Services-Admin`, `AWS-Security-Admin`, hoặc `AWS-Logging-Admin`).
- Nhấn **Next**.

  ![AWS Account](/images/8/00011.png?featherlight=false&width=90pc)

#### 3. Chọn bộ quyền (Permission Set)
- Chọn **Permission set** tương ứng với nhóm người dùng.
- Ví dụ: `AdministratorAccess` cho nhóm **AWS-Shared-Services-Admin** hoặc `SecurityAudit` cho nhóm **AWS-Security-Read-Only**.

  ![AWS Account](/images/8/00012.png?featherlight=false&width=90pc)

#### 4. Hoàn tất gán quyền
- Nhấn **Submit** để xác nhận gán quyền cho nhóm đã chọn.

  ![AWS Account](/images/8/00013.png?featherlight=false&width=90pc)

#### 5. Lặp lại quy trình cho các tài khoản khác
- Đối với các tài khoản khác như **Security Account**, lặp lại quy trình từ bước 1 đến bước 4.
  
  ![AWS Account](/images/8/0006.png?featherlight=false&width=90pc)

#### 6. Chọn nhóm người dùng
- Chọn nhóm bạn muốn gán quyền cho **Security Account** và nhấn **Next**.

  ![AWS Account](/images/8/0007.png?featherlight=false&width=90pc)

#### 7. Chọn bộ quyền (Permission Set) cho tài khoản Security
- Chọn **Permission set** thích hợp và nhấn **Next** để tiếp tục.

  ![AWS Account](/images/8/0008.png?featherlight=false&width=90pc)

#### 8. Hoàn tất gán quyền
- Nhấn **Submit** để xác nhận gán quyền cho nhóm đã chọn.

  ![AWS Account](/images/8/0009.png?featherlight=false&width=90pc)

#### 9. Kết thúc
- Sau khi hoàn thành, bạn sẽ thấy thông báo xác nhận việc gán quyền thành công.

  ![AWS Account](/images/8/00010.png?featherlight=false&width=90pc)

#### Lời kết
Chúc mừng, bạn đã thiết lập quyền truy cập AWS SSO thành công cho các nhóm và người dùng! Hãy đảm bảo rằng các chính sách truy cập được kiểm tra định kỳ để phù hợp với các thay đổi trong tổ chức và yêu cầu bảo mật.

**Tài liệu tham khảo:**
- [AWS Single Sign-On Documentation](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)
- [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
