# 🚀 AWS Billing Alert Terraform Module  

![AWS-billing](https://github.com/user-attachments/assets/8e779cd7-68a8-4ec3-92f4-74fccc8bd773" />)


Welcome to the **AWS Billing Alert Terraform module!** This module helps you set up automatic billing alerts for your AWS account. Once configured, you'll receive notifications when your AWS charges exceed specified amounts, helping you stay on top of your costs. 💰  

---

## 🛠️ Prerequisites  

> [!IMPORTANT]
> **Before you begin, make sure you have the following:**  
>
> - 🧰 **Terraform (v1.5.0 or later)** installed on your local machine.  
> - 🌐 **An AWS account** with appropriate permissions.  
> - 🔑 **AWS CLI** configured with the necessary credentials.  

---

## 🔍 Understanding the AWS Services  

### 🌟 AWS CloudWatch  

[AWS CloudWatch](https://aws.amazon.com/cloudwatch/) is a monitoring and observability service that collects and tracks metrics, collects and monitors log files, and sets alarms. This module uses CloudWatch to monitor your AWS billing and trigger an alarm when specified thresholds are exceeded.  

### 📢 AWS SNS (Simple Notification Service)  

[AWS SNS](https://aws.amazon.com/sns/) is a fully managed messaging service. It allows you to send notifications to multiple subscribers. In this module, SNS is used to send billing alerts via email, SMS, or other supported channels when the CloudWatch alarm is triggered.  

### 🧾 AWS Billing  

[AWS Billing](https://aws.amazon.com/aws-cost-management/aws-bill/) provides tools to manage your AWS costs and budget. This module automates the monitoring of your AWS billing, so you're notified before your bill goes beyond your expectations.  

---

## 🚀 New Features & Improvements [07-03-2025]

✅ **Multiple Email Alerts** – Supports multiple recipients by allowing a list of emails.  
✅ **SNS Dead-Letter Queue (DLQ)** – Ensures failed notifications are retried.  
✅ **Per-Service Billing Alerts** – Monitors spending on individual AWS services like EC2, S3, etc.  
✅ **Enhanced CloudWatch Filters** – Improved billing log monitoring for better cost visibility.  
✅ **CloudWatch Dashboard** – Provides an overview of billing trends and cost insights.  

---

## 📦 Setup Instructions  

### 1️⃣ Clone the Repository  

1. Open your terminal or command prompt.  
2. Navigate to the directory where you'd like to place the project:  

   ```bash  
   cd /path/to/your/directory  
   ```  

3. Clone the repository:  

   ```bash  
   git clone https://github.com/Haswanth/aws-billing-alert-terraform.git  
   ```  

4. Move into the directory:  

   ```bash  
   cd aws-billing-alert-terraform  
   ```  

---

### 2️⃣ Install Terraform  

Follow the steps in your system documentation to install **Terraform** or use the quick instructions for Amazon Linux:  

```bash  
sudo yum install -y yum-utils shadow-utils  
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo  
sudo yum -y install terraform  
terraform --version  
```  

---

### 3️⃣ Initialize Terraform  

Prepare Terraform for use:  

```bash  
terraform init  
```  

---

### 4️⃣ Configure and Apply Changes  

#### Update Configuration Variables:  

With the recent changes, you can now: 

- Set custom **AWS regions** using `aws_region`.  
- Configure **currencies** for billing alerts.  
- Automatically confirm **email subscriptions** for ease of setup during testing.  
- Configure **per-service billing alerts** to track costs for specific AWS services.  
- Enable **SNS DLQ** for better message reliability.  
- Visualize billing trends via the **CloudWatch Dashboard**.  

Update the `terraform.tfvars` file with your settings:  

```hcl  
aws_region            = "us-east-1"  
alert_thresholds      = [100, 150, 200]  
currency              = "USD"  
email_endpoints       = ["your-email@example.com", "team@example.com"]  
auto_confirm_subscription = true  
```  

#### Apply the Configuration:  

```bash  
terraform apply  
```  

---

## 🔧 Customization  

### Billing Thresholds  

Modify the `alert_thresholds` in your variables file to configure additional thresholds for your billing alerts:  

```hcl  
alert_thresholds = [100, 150, 200, 250]  
```  

### Email Subscription Auto-Confirmation  

For testing purposes, you can enable automatic email confirmation by setting:  

```hcl  
auto_confirm_subscription = true  
```  

> [!IMPORTANT]  
> **Use this option only in test environments with proper permissions.**  

---

## 📬 Notifications  

This module supports email alerts via **AWS SNS**. Update the `email_endpoints` variable with your preferred email addresses to receive billing notifications.  

---

## 📝 Example Usage  

Here’s an example configuration:  

```hcl  
module "billing_alert" {  
  source                     = "github.com/Haswanth/aws-billing-alert-terraform"  
  aws_region                 = "us-west-2"  
  alert_thresholds           = [100, 150, 200]  
  email_endpoints            = ["my-email@example.com", "finance@example.com"]  
  auto_confirm_subscription  = true  
  currency                   = "USD"  
}  
```  

---

## 🎯 Usage  

This module is flexible and supports dynamic region, currency, and threshold configurations. Customize the `alert.tf` file as needed and reapply the configuration using `terraform apply`.  

---

## 🙌 Feedback and Contributions

> [!TIP]  
> _We'd love to hear your thoughts! Whether it's feedback, bug reports, or pull requests, feel free to get involved. Your contributions help make this module better for everyone._

## ⭐ Hit the Star  

> [!IMPORTANT]  
> _If you find this repository helpful for learning or in practice, **please hit the star button on GitHub.** ⭐ It helps others find this resource too!_
