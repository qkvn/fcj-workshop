---
title: "Creating and Coding AWS Lambda"
date: 2026-06-21
weight: 6
chapter: false
pre: ""
---

# Step 4: Creating and Coding AWS Lambda

### Objective

In this step, you will create a Lambda Function to receive messages from Amazon SQS, read information about images uploaded to Amazon S3, and call AI services like Amazon Rekognition and Amazon Textract to analyze images.

---

### 4.1 - Creating Lambda Function

1. Access **AWS Lambda**, select **Create function**.

![Access AWS Lambda](./images/image1.png)

2. Select **Author from scratch**.

![Select Author from scratch](./images/image2.png)

![Create Lambda function](./images/image3.png)

3. Configure Lambda Function.

![Configure Lambda function](./images/image4.png)

![Select runtime and role](./images/image5.png)

Configuration recommendations:

- Function name: **image-quality-processor**
- Runtime: **Python 3.x**
- Execution role: select the IAM Role **Lambda-ImageProcessing-Role** created in step 1

4. Select **Create function**.

![Create function](./images/image6.png)

5. Go to the **Configuration** tab, select **General configuration**, then select **Edit**.

![Open General configuration](./images/image7.png)

6. Set **Timeout = 60 seconds**, then save configuration.

![Set timeout for Lambda](./images/image8.png)

---

### 4.2 - Attaching SQS as Trigger

1. On the Lambda Function page, select **Add trigger**.

![Add trigger to Lambda](./images/image9.png)

2. Select source as **SQS**.

![Select SQS trigger](./images/image10.png)

3. Select the queue **image-processing-queue**.

4. Configure **Batch size = 1**.

Batch size of 1 helps Lambda process each message individually, suitable for the lab as it's easy to observe logs and debug.

5. Select **Add**.

![Configure SQS trigger](./images/image11.png)

---

### 4.3 - Writing Python Code

1. Go to the **Code** tab.

2. Delete sample code, paste the Python code for processing SQS messages, then select **Deploy** to save the code.

![Write Lambda code and Deploy](./images/image12.png)

Sample code:

```python
... (omitted in preview) ...
```
