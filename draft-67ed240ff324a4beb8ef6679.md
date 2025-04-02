---
title: "#30DaysOfDevOps Challenge - Day1 - Introduction to Terraform and Infrastructure as Code (IaC)"
slug: 30daysofdevops-challenge-day1-introduction-to-terraform-and-infrastructure-as-code-iac
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1743594740789/3cbd18f1-c71c-4661-8aca-2ed3e8154a70.png

---

Hello. Welcome to Day 1 of my 30-day Terraform sprint. I will be starting from the basics and progressing to advanced concepts through multiple projects. Throughout this journey, I'll share my learnings and document the projects I work on. Let’s gear up for an exciting Terraform experience!

This article will cover an introduction to infrastructure as code, its benefits and a project showcasing the difference between manually provisioning AWS resources using the AWS Management Console and automating the deployment using Terraform.

# What is Infrastructure as Code?

Infrastructure as Code is simply writing and executing code to define, deploy, update and destroy your infrastructure.

IaC is also a hub that can be used for collaboration across the IT organization to improve infrastructure deployments, increase ability to scale quickly and improve application development process.

## Categories of IaC Tools

1. Adhoc Scripts (bash, python and ruby scripts)
    
2. Configuration management tools (ansible, Chef and puppet)
    
3. Server Templating Tools (packer, docker and vagrant)
    
4. Orchestration Tools (Kubernetes, swarm, mesos)
    
5. Provisioning Tools (Terraform, Cloud Formation, OpenStack heat)
    

## Benefits of Infrastructure as Code

1. **Simplification of Cloud Adoption**
    
    IaC allows quick adoption to cloud-based services and offerings to improve infrastructure capabilities.
    
2. **Automation**
    
    IaC automates infrastructure provisioning and management, reducing manual errors and speeding up deployments. 
    
3. **Standardization and consistency**
    
    Infrastructure is defined as code, ensuring consistent and repeatable deployments across different environments. 
    
4. **Capacity on demand**
    
    IaC offers a library of services for our developers, even publishing a self-service capability where developers and application owners can be empowered to request and provision infrastructure that better matches their requirements.
    

## Project 1: A Proof of Concept for an AWS Multi-AZ Infrastructure Deployment with Terraform.

### **Architecture Diagram**

### **Task 1: Log into the AWS Console and create a VPC.**

**Step 1.1**

In the VPC console, click **Create VPC**:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743599265641/881a8a7b-36ab-4a20-aec2-6116b11a4038.png align="center")

**Step 1.2**

Give the VPC a name eg joyce-demo-vpc and set the IPv4 CIDR block to use 10.0.0.0/16. Leave all of the other settings as default and select **Create VPC** at the bottom of the screen.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743599667367/1fbf4466-ed84-42fc-910b-48960dc5684b.png align="center")

### **Task 2: Create public and private subnets in three different Availability Zones.**

**Step 2.1**

In the VPC console, select **Subnets** from the left navigation panel. Click **Create Subnet**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743599440637/335e8698-d683-4486-b279-2f6cca6417cf.png align="center")

**Step 2.2**

Select the VPC created in Step 1 from the dropdown list. Give the subnet the name ***private-subnet -1*** and select ***us-east-1a*** from the dropdown list for the Availability Zone. Enter the IPv4 CIDR block of ***10.0.0.0/24***.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743599633197/e130539b-3098-4797-be26-f5a970df4023.png align="center")

Step 2.3

Repeat the previous step to create the additional subnets required to build out the required infrastructure, including 2 additional **private subnets** and the **3 public subnets**. Use the following information to complete this step:

| **Subnet Name** | **Availability Zone** | **CIDR Block** |
| --- | --- | --- |
| private-subnet-2 | us-east-1b | 10.0.1.0/24 |
| private-subnet-3 | us-east-1c | 10.0.2.0/24 |
| public-subnet-1 | us-east-1a | 10.0.100.0/24 |
| public-subnet-2 | us-east-1b | 10.0.101.0/24 |
| public-subnet-3 | us-east-1c | 10.0.102.0/24 |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743600173958/d6c247aa-73d3-41fc-a30d-c3075bd79f54.png align="center")

### **Task 3: Deploy an Internet Gateway and attach it to the VPC.**

**Step 3.1**

In the VPC console, select **Internet Gateways** from the left navigation panel in the VPC console. Click the **Create Gateway** button in the top right of the AWS console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743611710418/e55e8aaa-0f44-4bb8-aad0-f2974a9bcf5f.png align="center")

**Step 3.2**

Give the new Internet Gateway a name of **joyce-demo-igw** and click the **Create internet gateway** button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743612138610/bd120ce2-7e19-4d53-84f9-66bf41c41def.png align="center")

**Step 3.3**

In the **Internet Gateway console**, select the **Actions** menu and choose **Attach to VPC** from the dropdown list.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743612541201/8ba1cc95-e608-4809-8b3a-5829a28b728f.png align="center")

Select the VPC created in Step 1 by clicking the text box and choosing the VPC. Click the **Attach internet gateway** button to complete the task.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743612605201/b70a5deb-1dd0-479b-862d-1100ad3e7302.png align="center")

### Task 4: Provision a NAT Gateway (a single instance will do) for outbound connectivity.

**Step 4.1**

Back in the VPC Console, select **NAT Gateways** from the left navigation panel. Click the **Create NAT Gateway** button on the top right of the AWS console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743612711271/06f01c63-b7dc-4bbc-9076-19f1ed08eae1.png align="center")

**Step 4.2**

Provide the name **joyce-demo-nat-gateway** for the NAT Gateway. Select a subnet by choosing **public-subnet-2** from the dropdown list. Keep the Connectivity Type as **Public**. Click the **Allocate Elastic IP** button to automatically create and assign a new Elastic IP address for the NAT Gateway. Scroll down and click the **Create NAT Gateway** button to complete the task.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743612802484/b100de69-e2b0-46ce-8e17-28c00268f11c.png align="center")

### Task 5: Ensure that route tables are configured to properly route traffic based on the requirements.

**Step 5.1**

In the VPC console, select **Route Tables** from the left navigation panel. Click the **Create route table** button on the top right of the AWS console. Provide the name **public-rtb** for the route table and select the VPC created in Step 1. Click the **Create route table** button to create your first route table.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743613171799/fda44300-d87e-45bb-8843-59ddde80d53d.png align="center")

Repeat the above task to create a second route table. Name the second route table **private-rtb**. Select the same VPC created in Step 1. Click the Create route table button to create the second route table.

**Step 5.2**

From the **Route Tables console**, select the t**ick box** next to the route table named **public-rtb**. In the bottom panel, select the **Subnet Associations** tab. Click the **Edit subnet associations** button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743613269315/d834b422-5af0-4aec-b630-09d776a5f0e4.png align="center")

Select the **three public subnets** from the list of available subnets by checking the tick box next to the subnets. These are the same three subnets that you created in Step 2. Once you have selected the three subnets, click on the **Save associations** button to save your configuration. Repeat this step for the private-rtb and selecting the 3 private subnets that were created in Step 2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743613363700/e544f74d-3501-4dba-9e62-ef503c3bc799.png align="center")

Step 5.3

Now that the subnets have been associated with the proper route table, we need to add the **routes** to ensure network traffic is routed correctly. From the **Route Tables console**, select the **public-rtb** again. In the bottom pane, select the **Routes tab** and click **Edit Routes.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743613585434/cc2bd1e3-c3c3-49d9-aa04-47e2d86aa552.png align="center")

In the Edit Routes window, click the **Add route** button. Enter **0.0.0.0/0** in the **Destination text box** to define our new route destination. Click the text box for **Target**, select **Internet Gateway**, and select the Internet Gateway that was created in Step 3. It should be the only one listed. Click **Save changes** to save the new route configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743613686416/162e9478-7bd9-48bc-a0ca-935498a71ccc.png align="center")

Repeat this step to add a route to the **private-rtb**. The Destination should be **0.0.0.0/0**. Click the text box for **Target**, select **NAT Gateway**, and choose the NAT Gateway that was created in Step 4. It should be the only one listed. Click **Save changes** to save the new route configuration.

We’ve just manually configured a vpc environment with the required resources. Let’s say that your organization has 100+ accounts in AWS and you’re required to handle the same similar task in all of the accounts. Its pretty tedious,monotonous,time-consuming and prone to mistakes. That’s where IaC comes about.

IaC allows us to easily replicate deployment tasks and take the human aspect out of repetitive tasks. By codifying your infrastructure, you can reduce or eliminate risks to the infrastructure running your applications. IaC makes changes idempotent, consistent, repeatable, and predictable. Plus, you can easily see how any modifications to your environment will impact your infrastructure before ever applying it.

### Task 6: Delete the VPC resources.

Step 6.1

In the VPC Console, select the VPC that we just created by checking the tick box next to the VPC. From the Actions menu, select **Delete VPC**. Confirm you wish to delete the VPC and related AWS resources by typing delete in the text box at the bottom of the prompt. Click the **Delete** button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743614504061/7d09988d-75a5-4d5d-9d48-bdaa3f37fd1f.png align="center")

### Task 7: Prepare files and credentials for using Terraform to deploy cloud resources.

**Step 7.1**

On your workstation (code editor such as VScode), create a folder eg **Terraform-Challenge**, then create this nested directory: **/workstation/terraform** directory.Create a new file called [main.tf](http://main.tf) and [variables.tf](http://variables.tf).

In the [variables.tf](http://variables.tf), copy the following variable definitions and save the file. Don’t worry about understanding the file.

```bash
variable "aws_region" {
type = string
default = "us-east-1"
}
variable "vpc_name" {
type = string
default = "demo_vpc"
}
variable "vpc_cidr" {
type = string
default = "10.0.0.0/16"
}
variable "private_subnets" {
default = {
"private_subnet_1" = 1
"private_subnet_2" = 2
"private_subnet_3" = 3
}
}
variable "public_subnets" {
default = {
"public_subnet_1" = 1
"public_subnet_2" = 2
"public_subnet_3" = 3
}
}
```

In the **main.tf** file, copy the following Terraform configuration and save the file.

```bash
# Configure the AWS Provider
provider "aws" {
region = "us-east-1"
}
#Retrieve the list of AZs in the current AWS region
data "aws_availability_zones" "available" {}
data "aws_region" "current" {}
#Define the VPC
resource "aws_vpc" "vpc" {
cidr_block = var.vpc_cidr
tags = {
Name = var.vpc_name
Environment = "demo_environment"
Terraform = "true"
}
}
#Deploy the private subnets
resource "aws_subnet" "private_subnets" {
for_each = var.private_subnets
vpc_id = aws_vpc.vpc.id
cidr_block = cidrsubnet(var.vpc_cidr, 8, each.value)
availability_zone = tolist(data.aws_availability_zones.available.names)[
each.value]
tags = {
Name = each.key
Terraform = "true"
}
}
#Deploy the public subnets
resource "aws_subnet" "public_subnets" {
for_each = var.public_subnets
vpc_id = aws_vpc.vpc.id
cidr_block = cidrsubnet(var.vpc_cidr, 8, each.value + 100)
availability_zone = tolist(data.aws_availability_zones.available.
names)[each.value]
map_public_ip_on_launch = true
tags = {
Name = each.key
Terraform = "true"
}
}
#Create route tables for public and private subnets
resource "aws_route_table" "public_route_table" {
vpc_id = aws_vpc.vpc.id
route {
cidr_block = "0.0.0.0/0"
gateway_id = aws_internet_gateway.internet_gateway.id
#nat_gateway_id = aws_nat_gateway.nat_gateway.id
}
tags = {
Name = "demo_public_rtb"
Terraform = "true"
}
}
resource "aws_route_table" "private_route_table" {
vpc_id = aws_vpc.vpc.id
route {
cidr_block = "0.0.0.0/0"
# gateway_id = aws_internet_gateway.internet_gateway.id
21
nat_gateway_id = aws_nat_gateway.nat_gateway.id
}
tags = {
Name = "demo_private_rtb"
Terraform = "true"
}
}
#Create route table associations
resource "aws_route_table_association" "public" {
depends_on = [aws_subnet.public_subnets]
route_table_id = aws_route_table.public_route_table.id
for_each = aws_subnet.public_subnets
subnet_id = each.value.id
}
resource "aws_route_table_association" "private" {
depends_on = [aws_subnet.private_subnets]
route_table_id = aws_route_table.private_route_table.id
for_each = aws_subnet.private_subnets
subnet_id = each.value.id
}
#Create Internet Gateway
resource "aws_internet_gateway" "internet_gateway" {
vpc_id = aws_vpc.vpc.id
tags = {
Name = "demo_igw"
}
}
#Create EIP for NAT Gateway
resource "aws_eip" "nat_gateway_eip" {
domain = "vpc"
depends_on = [aws_internet_gateway.internet_gateway]
tags = {
Name = "demo_igw_eip"
}
}
#Create NAT Gateway
resource "aws_nat_gateway" "nat_gateway" {
depends_on = [aws_subnet.public_subnets]
allocation_id = aws_eip.nat_gateway_eip.id
subnet_id = aws_subnet.public_subnets["public_subnet_1"].id
tags = {
Name = "demo_nat_gateway"
}
}
```

### Task 8: Set credentials for Terraform deployment

**Step 8.1**

This step involves setting up a few environment variables to set our AWS credentials and region used by Terraform. In AWS, generate an access key and secret key from an IAM user with Administrative privilege.

```bash
export AWS_ACCESS_KEY_ID="<YOUR ACCESS KEY>"
export AWS_SECRET_ACCESS_KEY="<YOUR SECRET KEY>"
```

### Task 9: Deploy the AWS infrastructure using Terraform

**Step 9.1**

The first step to using Terraform is initializing the working directory. In your bash shell, type the following command:

```bash
terraform init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743617163428/67ffcb01-e897-4e6b-98cd-0b5d3db76c9e.png align="center")

**Step 9.2**

Create a plan for execution. This will provide a preview of the changes to our AWS environment.

```bash
terraform plan
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743617254246/1777a21a-067e-4aa2-aa56-27afc0021786.png align="center")

**Step 9.3**

We need to apply the configuration. An apply will instruct Terraform to create the resources in AWS that are defined in our configuration file.

```bash
terraform apply -auto-approve
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743617459614/572a3f95-7fac-4cae-8315-fad593c8b6c9.png align="center")

At this point, Terraform has created new resources in our AWS account that match the manually created environment.

### Task 10: Delete the AWS resources using Terraform to clean up our AWS environment.

**Step 10.1**

In this step we will use Terraform to destroy the resources, this ensures that every single resource deployed with Terraform is destroyed from your account.

```bash
terraform destroy -auto-approve
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1743617707730/bbe12210-f6ab-4337-8fa9-2e873b13596f.png align="center")