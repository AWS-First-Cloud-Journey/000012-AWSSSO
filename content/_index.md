+++
title = "AWS Single Sign-On"
date = 2020
weight = 1
chapter = false
+++

# AWS Single Sign-On cho Organization

#### Tổng quan

Trong bài lab này, bạn sẽ thực hành thiết lập dịch vụ **AWS SSO** để dễ dàng cung cấp và quản lý quyền truy cập tài nguyên tới các tài khoản AWS thuộc **AWS Organization** của bạn.

#### AWS Single Sign-On (SSO)

**AWS SSO** là một dịch vụ cho phép bạn cấp cho người dùng trong danh mục (*directory*) của mình quyền truy cập SSO vào một hoặc nhiều tài khoản AWS trong AWS Organization.

#### AWS Organization

**AWS Organization** là một dịch vụ quản lý tài khoản cho phép bạn quản lý tập trung nhiều tài khoản AWS trong tổ chức của bạn. Với AWS Organization, bạn có thể gộp các AWS Account vào những **Organizational Unit** và tổng hợp chi phí của tất cả các tài khoản AWS lại cho **Management Account**.

#### Organizational Unit (OU)

**Organizational Unit** là một nhóm các tài khoản AWS. Một OU có thể chứa đến 5 tầng OU lồng nhau bên trong nó. Bạn có thể gán các chính sách quản lý cho OU, và chính sách ấy sẽ áp dụng cho tất cả các OU thành viên và tài khoản AWS thành viên.

#### Management Account

**Management Account** là tài khoản AWS có quyền cao nhất và có thể kiểm soát tất cả các tài khoản AWS khác trong một AWS Organization. Management account cũng chịu trách nhiệm chi trả chi phí tổng hợp của các tài khoản thành viên.

#### Nội dung
1. [Các bước chuẩn bị](1-prerequisite)
2. [Thiết lập AWS SSO](2-setup-aws-sso)
3. [Kiểm tra kết quả & Dọn dẹp tài nguyên](3-clean-up)