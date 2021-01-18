+++
title = "Các bước chuẩn bị"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

+ Bài thực hành này là một phần của bài thực hành Landing Zone.
+ Trước đó, chúng ta sẽ phải tạo một AWS Organizations, với 4 Organization Units nhằm phân nhóm các tài khoản. Tạo các Tài khoản AWS (AWS Account) với tên: Security, Shared Services, Logging và Application và thêm các Tài khoản vào từng OU tương ứng.

![Lab Diagram](/images/1/1.png?width=60pc)

+ Kế đến, chúng ta thiết lập môi trường bảo mật đa tài khoản với thông số như sau:
	* **Tài khoản Logging:** Là nơi tập trung cho Amazon VPC Flow Logs, CloudTrail logs, Config logs.
	* **Tài khoản Security**: Tập hợp AWS Config, Amazon GuardDuty master, và các cảnh báo.
	* **Tài khoản Network/Shared Services:** Chia sẻ chung một VPC dành cho các kết nối từ xa đến các tài khoản khác. AWS Direct Connect chính được cài đặt với AWS Transit Gateway nhằm giao tiếp với các VPC ở các tài khoản khác.
	* **Tài khoản dành cho Business Unit:** tài khoản cho Analytics-Prod, và Analytics-non-prod.
