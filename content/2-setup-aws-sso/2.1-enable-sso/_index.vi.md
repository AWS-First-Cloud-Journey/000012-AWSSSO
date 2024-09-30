+++
title = "Kích hoạt AWS SSO"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

#### Kích hoạt AWS SSO

#### Mục lục
- [Kích hoạt AWS SSO](#kích-hoạt-aws-sso)
- [Mục lục](#mục-lục)
- [1. Đăng nhập AWS Management Console](#1-đăng-nhập-aws-management-console)
- [2. Mở AWS SSO Console](#2-mở-aws-sso-console)
- [3. Kích hoạt AWS SSO](#3-kích-hoạt-aws-sso)
- [4. Quản lý Người dùng và Nhóm](#4-quản-lý-người-dùng-và-nhóm)
- [Bước 1: Tạo Người dùng và Nhóm](#bước-1-tạo-người-dùng-và-nhóm)
- [Bước 2: Thêm Người dùng vào Nhóm](#bước-2-thêm-người-dùng-vào-nhóm)
- [Bước 3: Gán quyền truy cập](#bước-3-gán-quyền-truy-cập)
- [Tài liệu tham khảo:](#tài-liệu-tham-khảo)

<a name="1-đăng-nhập-aws-management-console"></a>
#### 1. Đăng nhập AWS Management Console
- Truy cập vào **AWS Management Console** tại [https://aws.amazon.com/console](https://aws.amazon.com/console).
- Sử dụng thông tin đăng nhập của **Tài khoản chính (Root)** thuộc **AWS Organization** để đăng nhập.

    ![AWS Account](/images/2/0001.png?featherlight=false&width=90pc)

<a name="2-mở-aws-sso-console"></a>
#### 2. Mở AWS SSO Console
- Trong **AWS Management Console**, tìm kiếm và mở **AWS Single Sign-On (SSO)**.

    ![AWS SSO Console](/images/2/0002.png?featherlight=false&width=90pc)

<a name="3-kích-hoạt-aws-sso"></a>
#### 3. Kích hoạt AWS SSO
- Chọn **Enable AWS SSO** để kích hoạt tính năng **AWS Single Sign-On**.

    ![Enable AWS SSO](/images/2/0002.png?featherlight=false&width=90pc)

> **Lưu ý:** AWS SSO cung cấp khả năng quản lý truy cập tập trung cho các tài khoản AWS và ứng dụng SaaS khác. Sau khi kích hoạt, bạn có thể tích hợp AWS SSO với dịch vụ quản lý danh tính (Identity Provider) như **Active Directory** hoặc sử dụng tính năng lưu trữ người dùng tích hợp sẵn.

<a name="4-quản-lý-người-dùng-và-nhóm"></a>
#### 4. Quản lý Người dùng và Nhóm
Sau khi kích hoạt, bạn sẽ có một **kho lưu trữ mặc định** để quản lý Người dùng và Nhóm của mình. Thực hiện các bước sau để cấu hình quyền truy cập:

#### Bước 1: Tạo Người dùng và Nhóm
- Trong **AWS SSO Console**, chọn **Users and Groups** > **Add User** hoặc **Create Group** để tạo mới Người dùng và Nhóm.

#### Bước 2: Thêm Người dùng vào Nhóm
- Sau khi tạo Người dùng và Nhóm, chọn nhóm mà bạn muốn thêm người dùng, sau đó nhấn **Add users to group**.

#### Bước 3: Gán quyền truy cập
- Chọn **AWS accounts** hoặc **Applications** > **Assign users/groups** để gán quyền truy cập mong muốn cho các tài khoản và ứng dụng AWS.

    ![AWS SSO Permissions](/images/2/0003.png?featherlight=false&width=90pc)

> **Mẹo:** Đảm bảo rằng bạn đã định nghĩa rõ các nhóm quyền theo nguyên tắc **least privilege** (tối thiểu quyền cần thiết) để hạn chế quyền truy cập không cần thiết cho các tài khoản và ứng dụng AWS.

<a name="tài-liệu-tham-khảo"></a>
#### Tài liệu tham khảo:
- [AWS SSO User Guide](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)
- [AWS IAM Identity Center](https://aws.amazon.com/iam/identity-center/)
