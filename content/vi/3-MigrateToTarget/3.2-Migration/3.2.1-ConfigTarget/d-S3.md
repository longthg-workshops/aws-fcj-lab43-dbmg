---
title: "Amazon S3 Target"
weight: 4
chapter: false
pre: "<b> d. </b>"
---

Trong phần này, chúng tôi tạo một thùng Amazon S3 để sử dụng làm đích đến cho dữ liệu của chúng tôi. Amazon S3 là một kho lưu trữ đối tượng có tính khả dụng cao, bền bỉ và có khả năng mở rộng được xây dựng để lưu trữ và truy xuất bất kỳ lượng dữ liệu nào từ bất kỳ đâu với chi phí hiệu quả.

1. Mở [**Amazon S3 console**](https://console.aws.amazon.com/s3/) , sau đó Nhấp vào Tạo bucket.

1. Tên bucket S3 phải là duy nhất trên toàn bộ Amazon S3 (tính tất cả các Region). Đặt tên bucket của bạn là **_dmstargetbucket-<YourInitial>-<RandomNumber>_**, trong đó **"YourInitial"** là chữ cái đầu tiên của tên và họ của bạn viết thường, và **"RandomNumber"** là bất kỳ số ngẫu nhiên 4 chữ số nào bạn muốn chọn. Ví dụ: **_dmstargetbucket-xy-1234_**. Để nguyên mọi cài đặt khác theo mặc định. Chỉ cần đảm bảo rằng bạn đang ở trong vùng mà tất cả các tài nguyên DMS khác cho hội thảo của bạn đã được tạo.

1. Điều hướng đến bucket mà bạn vừa tạo, thường là bằng cách nhấp vào tên, sau đó chọn nút **Tạo thư mục**. Đặt tên cho thư mục là **_dmstargetfolder_**, lấy tất cả các giá trị mặc định khác rồi chọn nút **Create Folder**.

1. Tiếp theo, bạn cần **Tạo chính sách AWS IAM** cấp quyền truy cập vào S3 bucket mà bạn vừa tạo.

    Điều hướng đến bảng điều khiển IAM, sau đó chọn **Chính sách** từ thanh điều hướng.


1. Chọn **Create policy**, sau đó chọn **JSON**. Sao chép mã JSON sau vào trình chỉnh sửa chính sách IAM trong bảng điều khiển. Cập nhật phần tài nguyên của chính sách có nội dung **_"THAY_BẰNG_TÊN_BUCKE_CỦA_BẠN"_**, với tên bucket của bạn. Đảm bảo giữ nguyên dấu * ở cuối tên và bạn thay đổi nó ở cả hai vị trí bên dưới. Nhấp vào **Review policy**.

    ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "s3:PutObject",
                    "s3:DeleteObject"
                ],
                "Resource": [
                    "arn:aws:s3:::REPLACE-WITH-YOUR-BUCKET-NAME*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:ListBucket"
                ],
                "Resource": [
                    "arn:aws:s3:::REPLACE-WITH-YOUR-BUCKET-NAME*"
                ]
            }
        ]
    }
    ```

1. Trong trường Tên, nhập **_DMS-LAB-S3-Access-Policy_**, sau đó nhấp vào **Create policy**.

1. Tiếp theo, bạn cần liên kết chính sách với vai trò AWS IAM. AWS DMS sẽ đảm nhận vai trò này để có quyền đưa các đối tượng vào thùng Amazon S3 mục tiêu.

1. Mở [**Bảng điều khiển IAM**](https://console.aws.amazon.com/iam/), sau đó đi tới **Roles** từ ngăn điều hướng.

1. Nhấp vào thanh tìm kiếm và nhập **_dms-vpc_** rồi nhấp vào liên kết **_dms-vpc-role_** hiển thị

1. Nhấp vào thêm quyền rồi đính kèm chính sách và thêm chính sách chúng ta vừa tạo **_DMS-LAB-S3-Access-Policy_** rồi nhấp vào nút **Add permission** (thêm quyền).

1. Lưu **ARN Role** từ trang **Summary** (Tóm tắt) vào sổ tay của bạn.