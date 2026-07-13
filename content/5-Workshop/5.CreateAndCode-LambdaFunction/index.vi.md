---
title: "Tạo và viết code cho AWS Lambda"
date: 2026-06-21
weight: 6
chapter: false
pre: ""
---

# Bước 4: Tạo và viết code cho AWS Lambda

### Mục tiêu

Trong bước này, bạn sẽ tạo Lambda Function để nhận message từ Amazon SQS, đọc thông tin ảnh được upload lên Amazon S3 và gọi các dịch vụ AI như Amazon Rekognition và Amazon Textract để phân tích ảnh.

---

### 4.1 - Tạo Lambda Function

1. Truy cập **AWS Lambda**, chọn **Create function**.

![Truy cập AWS Lambda](./images/image1.png)

2. Chọn **Author from scratch**.

![Chọn Author from scratch](./images/image2.png)

![Tạo Lambda function](./images/image3.png)

3. Cấu hình Lambda Function.

![Cấu hình Lambda function](./images/image4.png)

![Chọn runtime và role](./images/image5.png)

Gợi ý cấu hình:

- Function name: **image-quality-processor**
- Runtime: **Python 3.x**
- Execution role: chọn IAM Role **Lambda-ImageProcessing-Role** đã tạo ở bước 1

4. Chọn **Create function**.

![Create function](./images/image6.png)

5. Vào tab **Configuration**, chọn **General configuration**, sau đó chọn **Edit**.

![Mở General configuration](./images/image7.png)

6. Đặt **Timeout = 60 giây**, sau đó lưu cấu hình.

![Đặt timeout cho Lambda](./images/image8.png)

---

### 4.2 - Gắn SQS làm Trigger

1. Ở trang Lambda Function, chọn **Add trigger**.

![Add trigger cho Lambda](./images/image9.png)

2. Chọn source là **SQS**.

![Chọn SQS trigger](./images/image10.png)

3. Chọn queue **image-processing-queue**.

4. Cấu hình **Batch size = 1**.

Batch size bằng 1 giúp Lambda xử lý từng message một, phù hợp cho lab vì dễ quan sát log và debug.

5. Chọn **Add**.

![Cấu hình SQS trigger](./images/image11.png)

---

### 4.3 - Viết code Python

1. Vào tab **Code**.

2. Xóa code mẫu, dán đoạn code Python xử lý SQS message, sau đó chọn **Deploy** để lưu code.

![Viết code Lambda và Deploy](./images/image12.png)

Code mẫu:

```python
... (omitted in preview) ...
```
