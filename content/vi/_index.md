---
title: "Chuyển đổi lược đồ và di dời CSDL"
weight: 1
chapter: false
---

# Chuyển đổi lược đồ và di dời CSDL

### Chuyển đổi lược đồ

Chuyển đổi lược đồ (schema) của cơ sở dữ liệu (CSDL) và các đối tượng mã nguốn thường là thao tác tốn nhiều thời gian nhất trong quá trình dịch chuyển các cơ sở dữ liệu không đồng nhất. Chuyển đổi lược đồ đúng cách được xem là một cột mốc quan trọng trong quá trình dịch chuyển CSDL. [Công cụ chuyển đổi lược đồ AWS (SCT)](https://docs.aws.amazon.com/SchemaConversionTool/latest/userguide/CHAP_Installing.html) là một ứng dụng dễ sử dụng mà bạn có thể cài đặt trên máy tính cục bộ hoặc phiên bản Amazon EC2. Tại **ReInvent 2023**, AWS cũng đã thêm giao diện bảng điều khiển web cho phần Chuyển đổi và di chuyển của dịch vụ DMS. Trong tương lai, chúng ta sẽ dần chuyển sang trải nghiệm trong bảng điều khiển.

SCT và Chuyển đổi & Di chuyển trong bảng điều khiển đều giúp đơn giản hóa quá trình di chuyển cơ sở dữ liệu không đồng nhất bằng cách kiểm tra lược đồ cơ sở dữ liệu nguồn và tự động chuyển đổi phần lớn các đối tượng mã cơ sở dữ liệu, bao gồm các dạng xem cũng như các quy trình và hàm được lưu trữ, sang định dạng tương thích với cơ sở dữ liệu đích. Bất kỳ đối tượng nào SCT không thể tự động chuyển đổi sẽ được đánh dấu bằng thông tin chi tiết. Từ đó bạn có thể sử dụng để chuyển đổi thủ công.

![Schema Conversion](/images/0-home/0001.png?width=50pc)

### Data Migration

After you have completed the schema conversion, you'll need to move the data itself. In case of production databases, you may not be able to afford very little downtime during the migration. Moreover, you may want to keep the transactions from source and target database in sync until you switch your application to the new target.

The AWS Database Migration Service helps you migrate the data from the source database to the target database easily and securely. AWS DMS supports data migration to and from most widely used commercial and open-source databases. The source database can be located in your on-premises environment, running on an Amazon EC2 instance, or it can be an Amazon RDS database. The target can be a database on Amazon EC2 or Amazon RDS. The target can also be non-relational like S3, Stream like Kafka/Kinesis, DocumentDB or DynamoDB etc. Additionally, the source database remains fully operational during the migration, minimizing downtime to applications that rely on the database.

![Migration](/images/0-home/0002.png?width=50pc)