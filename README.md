# AWS Multi-tier Web Application Architecture
## Architecture Diagram
![Multi cloud1](https://github.com/user-attachments/assets/8a57ab25-a31f-42df-933a-fe38d284f7bb)


## Project Overview
 - Deployed inside AWS Cloud.
 - Resources organized within a single Region.
 - Isolated network using VPC (Virtual Private Cloud).
 - Segregated into:
     - Public Subnet
     - Private Subnet
## Public Subnet Components
- Application Load Balancer (ALB): Receives traffic from users (Internet) Distributes requests to EC2 instances.
- S3 Bucket: stores static content and application assets.
- AWS Lambda: Executes serverless functions triggered by events.
## Application Layer
- EC2 Instances:
    - Hosts Web & Application servers.
    - Processes incoming requests from ALB.
    - Communicates with RDS for database operations.
## Database Layer (Private Subnet)
- Amazon RDS:
    - Managed relational database.
    - Placed in private subnet for security.
    - Accessible only from EC2 instances.
## Monitoring & Security
 - IAM (Identity and Access Management).
     - Manages access control and permissions.
 - CloudWatch
     - Monitors application and infrastructure performance.
     - Configured with alarms for alerts.
## Traffic Flow
  - User sends request via Internet.
  - ALB receives and forwards request to EC2.
  - EC2 processes application logic.
  - EC2 interacts with RDS for database operations.
  - Static files stored/retrieved from S3.
## Service Use Cases in This Architecture
### Application Load Balancer (ALB)
 - Distributes incoming user traffic across multiple EC2 instances to ensure high availability and fault tolerance.
### Amazon EC2
 - Hosts the web application and handles user requests, business logic, and communication with backend services.
### Amazon RDS
 - Stores structured application data securely inside a private subnet. Only accessible from the application layer.
### Amazon S3
 - Stores uploaded images and static assets such as CSS, JS, and media files.
### AWS Lambda
 - Triggered automatically when an image is uploaded to S3.  
 - Validates image size and resizes it before saving the processed version back to S3.
### IAM
 - Manages secure access and permissions between AWS services.
### CloudWatch
 - Monitors application performance, logs, and system metrics. Generates alerts when thresholds are exceeded.

## Technologies Used
  - AWS VPC   
  - EC2  
  - Application Load Balancer  
  - Amazon RDS  
  - Amazon S3  
  - AWS Lambda  
  - IAM  
  - CloudWatch  
