# AWS Lambda Blog Generator with Bedrock and S3

## **Project Overview**
This project is an **AWS Lambda-based serverless application** that generates blogs using **AWS Bedrock (Llama 3 AI Model) I Used** and stores them in **Amazon S3**. The application is designed to take a blog topic as input, generate AI-written content, and save it in a cloud storage bucket for easy access.

---

## **How It Works**
1. A user provides a **blog topic** through an API request.
2. The **AWS Lambda function** processes the request and sends a prompt to **AWS Bedrock**.
3. **Bedrock** uses the **Llama 3 AI model** to generate a blog based on the provided topic.
4. The generated blog content is stored in an **Amazon S3 bucket**.
5. A response is returned to the user with the **S3 file path** of the saved blog.

---

## **Project Architecture**

### **1. AWS Lambda Function**
- Handles API requests.
- Calls **AWS Bedrock** to generate blog content.
- Saves the blog in **Amazon S3**.

### **2. AWS Bedrock (Llama 3 Model)**
- AI-powered model used to generate **200-word blogs**.
- Takes structured prompts and returns human-like text.

### **3. Amazon S3 (Storage Service)**
- Stores the generated blogs.
- Provides a **unique file path** for each blog.

### **4. API Gateway (Optional)**
- Can be used to expose the Lambda function as a public API.

---

## **Technologies Used**
- **AWS Lambda** – Serverless function execution.
- **AWS Bedrock** – AI-powered content generation.
- **Amazon S3** – Cloud storage for blogs.
- **Boto3 (AWS SDK for Python)** – Interacts with AWS services.
- **JSON** – Handles data exchange between API and Lambda.

---

## **Setup & Deployment**

### **1. Prerequisites**
- AWS account with permissions for:
  - Lambda execution.
  - Bedrock model invocation.
  - S3 file operations.
- Python installed with `boto3` library.

### **2. Configure AWS CLI (Optional)**
Run the following command to set up AWS credentials:
```sh
aws configure
```
Provide:
- **AWS Access Key ID**
- **AWS Secret Access Key**
- **Region (e.g., us-east-1)** I Used

### **3. Deploying the Lambda Function**
1. **Create a new AWS Lambda function** in the AWS console.
2. Upload the Python script as a **Lambda function**.
3. Set environment variables (if required).
4. Configure permissions for:
   - `bedrock:InvokeModel`
   - `s3:PutObject`
5. Deploy and test the function.

---

## **API Request Format**
The API expects a JSON body with the following format:
```json
{
  "blog_topic": "Benefits of Cloud Computing"
}
```

### **Example Response**
```json
{
  "message": "Blog generation completed",
  "s3_key": "blog-output/123456.txt"
}
```

---

## **Error Handling**
- **Missing Blog Topic**: Returns `400 Bad Request`.
- **AWS Bedrock Failure**: Returns `500 Internal Server Error`.
- **S3 Storage Failure**: Returns `500 Internal Server Error`.

---

## **Use Cases**
- **Automated blog generation** for businesses, writers, or marketing teams.
- **Serverless content generation** for websites or applications.
- **AI-powered research and content writing**.

---

## **Future Enhancements**
- Add **DynamoDB** to store metadata for generated blogs.
- Implement **API Gateway** to expose a public API.
- Enable **S3 event triggers** for notifications.

---

## **Conclusion**
This project demonstrates how **AWS Bedrock** can be integrated with **Lambda and S3** to automate content generation in a scalable, serverless manner. It provides a cost-effective and efficient way to create AI-generated blogs with cloud-based storage.

