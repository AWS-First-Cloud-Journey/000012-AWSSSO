+++
title = "Dọn dẹp tài nguyên"
date = 2020
weight = 6
chapter = false
pre = "<b> 6. </b>"
+++

## Dọn dẹp tài nguyên

Sau khi hoàn thành workshop, bạn cần xóa các tài nguyên AWS đã tạo trong tài khoản của mình để tránh phát sinh chi phí không cần thiết.

#### Xóa tài nguyên CloudFormation

Sau khi hoàn thành workshop, hãy xóa stack CloudFormation đã được tạo trong phần "Kiểm tra quyền truy cập dựa trên User và Group".

**⚠️ Warning**: Việc xóa stack CloudFormation sẽ xóa tất cả tài nguyên được tạo bởi stack đó. Đảm bảo bạn không còn cần các tài nguyên này trước khi tiếp tục.

Để xóa stack CloudFormation:
1. Điều hướng đến trang dịch vụ CloudFormation trên AWS Console
2. Chọn Stack (với tên bạn đã nhập)
3. Nhấp vào nút **Delete**

#### Dọn dẹp tài nguyên IAM Identity Center

**ℹ️ Information**: Việc xóa cấu hình IAM Identity Center sẽ loại bỏ tất cả người dùng, nhóm và cấu hình quyền được thiết lập trong Identity Center.

Để dọn dẹp tất cả tài nguyên IAM Identity Center:

1. Điều hướng đến IAM Identity Center Console
2. Chọn AWS Region được đề xuất bởi AWS Team nếu đây là một phần của sự kiện AWS, hoặc Region bạn đã cấu hình nếu bạn đang thực hiện workshop này tự mình
3. Chọn **Settings** từ menu bên trái
4. Trong trang Settings, chọn tab **Management**
5. Nhấp vào nút **Delete** trong phần "Delete IAM Identity Center configuration"
6. Nhập ID instance vào ô văn bản và nhấp vào nút **Confirm** trong cửa sổ hộp thoại "Confirm delete settings"

**💡 Pro Tip**: Trước khi xóa cấu hình IAM Identity Center, hãy đảm bảo bạn đã ghi lại bất kỳ cấu hình nào mà bạn có thể muốn tham khảo trong tương lai, vì không thể khôi phục cấu hình sau khi đã xóa.