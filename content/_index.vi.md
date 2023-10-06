+++
title = "AWS Single Sign-On"
date = 2020
weight = 1
chapter = false
+++


# AWS Single Sign-On cho Organization

Trong bài viết này, chúng ta sẽ tìm hiểu về cách sử dụng dịch vụ AWS Single Sign-On (SSO) để quản lý việc truy cập vào các tài khoản AWS trong tổ chức của bạn một cách hiệu quả. 

#### Tổng quan về AWS Single Sign-On (SSO)
AWS SSO là một dịch vụ quản lý quyền truy cập được cung cấp bởi Amazon Web Services (AWS). Dịch vụ này cho phép bạn quản lý việc xác thực và ủy quyền người dùng vào các tài khoản AWS một cách thuận tiện. Thay vì phải quản lý nhiều thông tin đăng nhập cho từng tài khoản riêng biệt, bạn có thể sử dụng AWS SSO để tổ chức và kiểm soát việc truy cập này từ một nơi duy nhất.

#### Cách AWS SSO hoạt động trong AWS Organization
Một khía cạnh quan trọng của việc sử dụng AWS SSO là tích hợp nó vào AWS Organization của bạn. AWS Organization cho phép bạn quản lý tập trung các tài khoản AWS của mình trong một cơ cấu có tổ chức. Dưới đây là một số thuật ngữ quan trọng:

- **AWS Organization:** Đây là tập hợp các tài khoản AWS được tổ chức lại theo một cách cụ thể, giúp bạn quản lý chúng một cách dễ dàng hơn.

- **Organizational Unit (OU):** Một phân đơn vị trong AWS Organization, cho phép bạn nhóm các tài khoản lại với nhau. Mỗi OU có thể chứa nhiều OU con khác.

- **Management Account:** Đây là tài khoản quản lý có quyền cao nhất trong AWS Organization. Tài khoản này có thể kiểm soát tất cả các tài khoản khác và chịu trách nhiệm về việc thanh toán chi phí tổng hợp của các tài khoản thành viên.

#### Bước tiếp theo

- Chúng ta sẽ tiến hành thực hiện các bước chuẩn bị cần thiết trước khi thiết lập AWS SSO trong môi trường của chúng ta. Hãy tiếp tục đọc bài viết Các bước chuẩn bị để bắt đầu.

- Nếu bạn đã hoàn thành các bước chuẩn bị, bạn có thể tiếp tục đến phần Thiết lập AWS SSO để làm quen với việc cấu hình dịch vụ AWS SSO.

- Cuối cùng, sau khi bạn đã thực hiện xong và muốn dọn dẹp tài nguyên, hãy xem phần Kiểm tra kết quả & Dọn dẹp tài nguyên để biết cách làm điều này một cách hiệu quả.

- Chúc bạn thành công trong việc triển khai AWS SSO cho tổ chức của mình!