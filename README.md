
# Free Tier WordPress Scalable and Fault-Tolerant on AWS  

This project deploys a **scalable and fault-tolerant WordPress site** on AWS using **CloudFormation**. The deployment utilizes only **AWS Free Tier** resources and is designed to be highly available, with multiple subnets, an Auto Scaling Group, an Application Load Balancer (ALB), an Amazon RDS instance, and an S3 bucket for media file storage.  

## Architecture Overview  
The infrastructure includes the following components:  
- **VPC** with public and private subnets across multiple Availability Zones.  
- **Application Load Balancer (ALB)** for distributing traffic.  
- **Auto Scaling Group (ASG)** to ensure high availability of WordPress instances.  
- **Amazon RDS (MySQL)** for the WordPress database in private subnets.  
- **Amazon S3** bucket for storing media files.  
- **Security Groups** to control traffic between components.  

## Features  
- Highly available and scalable architecture.  
- Uses only AWS Free Tier resources.  
- Secure setup with private subnets for the database.  
- Media file storage on Amazon S3.  

## Prerequisites  
Before deploying the template, ensure you have the following:  
1. An **AWS account** with access to AWS CloudFormation.  
2. An **EC2 Key Pair** for SSH access to the WordPress instances.  
3. AWS CLI and necessary permissions to create the required resources.  

## Deployment  
1. Clone this repository:  
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```  
2. Deploy the CloudFormation template using AWS CLI:  
   ```bash
   aws cloudformation create-stack --stack-name wordpress-stack --template-body file://template.yaml --parameters ParameterKey=KeyName,ParameterValue=<your-key-name>
   ```  
3. Wait for the stack creation to complete.  

## Outputs  
After successful deployment, the following outputs will be available:  
- **WebsiteURL**: The URL to access the WordPress site.  
- **S3BucketName**: The name of the S3 bucket for media file storage.  

## Template Details  
### Parameters  
- **InstanceType**: EC2 instance type for the WordPress server (default: `t2.micro`).  
- **KeyName**: Name of the EC2 Key Pair for SSH access.  
- **DBName, DBUser, DBPassword**: Configuration for the MySQL database.  

### Resources  
- **EC2 Instances**: Automatically managed by an Auto Scaling Group.  
- **RDS MySQL Database**: For WordPress data, deployed in private subnets.  
- **S3 Bucket**: For storing WordPress media files.  

## Security  
This template is for **testing purposes only**. It includes some configurations that should be updated for production environments, such as open **SSH access** and **database credentials**.  

## License  
This project is licensed under the MIT License.  

---

### Disclaimer  
The project is designed to remain within the AWS Free Tier, but exceeding the limits may incur charges. Monitor your usage on the AWS Console.  
```
