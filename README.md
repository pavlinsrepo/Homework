# EKS Cluster with Wordpress and MySQL.
This repositories was done for my homework on Monday.

## Requirements
- AWS account

## Creating the Cluster
- To make an EKS cluster, we need to have an AWS account, after we make an AWS account, we need to look for the service named EKS.
<img width="800" alt="Searching for k8s" src="https://github.com/pavlinsrepo/Homework/assets/163166111/8a6f8f88-11ad-4b08-a2bf-2d4bcd3ec3cb">

---

- Once we have found the service, we need to make an EKS cluster through the "Create cluster" button.
<img width="800" alt="starting to create a cluster" src="https://github.com/pavlinsrepo/Homework/assets/163166111/4442e0f0-3407-4ff3-9a35-fd1a469e5524">

---

- Once we have clicked on the button, it will take us to the place where we can configure our cluster. To configure the cluster we first need to make an IAM role with permissions for it.
<img width="800" alt="creating the clister (configure cluster)" src="https://github.com/pavlinsrepo/Homework/assets/163166111/df2c526d-3942-4363-8f8f-565cc7784041">
<img width="600" alt="creating a service role for the eks cluster " src="https://github.com/pavlinsrepo/Homework/assets/163166111/2d700625-5ff3-4adb-8d7c-959d309edad7">

---

- When we want to make a user with permissions , role for services or groups of users with the same permissions, we do them through IAM (Identity and Access Management) service. In order to create a role for our eks cluster, we need to find an IAM service through the search engine and find the option to create roles in the access management section. Тhen click on the "Create a Role" button.
<img width="800" alt="creating a role " src="https://github.com/pavlinsrepo/Homework/assets/163166111/c3f382e5-925a-4c24-ab16-eac37315fbbb">

---

- Then we have to choose what service we want to apply this role to. We choose EKS and click on the EKS-Cluster option.
<img width="800" alt="choosing what type of a rle" src="https://github.com/pavlinsrepo/Homework/assets/163166111/cd6e5c4e-e618-4589-9f13-de07560015d5">

---

1. Then we choose what kind of permission to give to this role.
2. We choose how to name the role and also what description to have.
3. We create the role through the "Create Role" button at the bottom.
<img width="600" alt="selecting permisions" src="https://github.com/pavlinsrepo/Homework/assets/163166111/98330122-1eaf-47d7-923d-4ae78006d7db">
<img width="600" alt="adding details" src="https://github.com/pavlinsrepo/Homework/assets/163166111/a28537c5-f069-45b1-a55e-9e4a26296a2b">
<img width="600" alt="then create role" src="https://github.com/pavlinsrepo/Homework/assets/163166111/7c8f8d08-1cc9-480d-8578-766b45ba5bb9">

---

- Then we go back to the configurator of our cluster and configure it to our liking.
<img width="600" alt="configuring the cluster" src="https://github.com/pavlinsrepo/Homework/assets/163166111/410c4c37-7933-4201-b895-764f721af713">
<img width="600" alt="configuring the networking for the cluster" src="https://github.com/pavlinsrepo/Homework/assets/163166111/fc3f1ebc-cb5c-4f20-b0c2-d3b12c8ee7eb">
<img width="600" alt="selecting add ons" src="https://github.com/pavlinsrepo/Homework/assets/163166111/c047d224-1dc7-4cfc-a9d5-de0bf57426dd">

---

- And finally, when we have decided how to configure our cluster we create it through the "Create" button at the bottom.

<img width="700" alt="final step is to create" src="https://github.com/pavlinsrepo/Homework/assets/163166111/cea69b63-fd7d-49fa-a08e-0a361eca8927">

---

- Once our cluster is created, it will take us to the new page where our cluster dashboard is. It takes to wait 10-15 minutes for aws to create the cluster for us. Then we have to create a node-group that will represent our worker nodes.
<img width="700" alt="dashboard when you create the cluster" src="https://github.com/pavlinsrepo/Homework/assets/163166111/4c2ab074-7ba2-49b0-9f36-196b5d3d1674">

---

- When we want to create a node group, we go to the compute section below, and then click on the add node group button.
<img width="700" alt="making a node group" src="https://github.com/pavlinsrepo/Homework/assets/163166111/9da3560e-4b07-47ae-be0a-dbda5ca1c4c0">

---
- To create a node group we will need a role from the IAM service, and for the role we will choose to be assigned to ec2 (We choose ec2 because our worker nodes will be ec2), these three permissions that I have shown are mandatory for our worker nodes to function.

<img width="600" alt="node group role" src="https://github.com/pavlinsrepo/Homework/assets/163166111/b6937cfe-e9db-46dc-a213-6c77d7687871">
<img width="600" alt="the type of permissions" src="https://github.com/pavlinsrepo/Homework/assets/163166111/9c8f5283-ba07-4d6c-89e7-56589be18a02">

---

1. Then we go back to the configurator of our nodes and put the role we just did.
2. We configure our nodes according to how we decide, for example, what EC2 instance types to go with, how many nodes to have, how much storage, what AMI type, with what node group scaling configuration.
<img width="600" alt="configuring it" src="https://github.com/pavlinsrepo/Homework/assets/163166111/26cfa21e-9283-48b7-9292-acc93859290e">
<img width="600" alt="setting instance type" src="https://github.com/pavlinsrepo/Homework/assets/163166111/2c2bf0a0-cd4a-4f77-8358-881fdd76138c">

---

- When we create our nodes and they are ready, we access the cluster through the cloudshell option (AWS CloudShell is a browser-based shell that makes it easier to securely manage, explore, and interact with your AWS resources).
<img width="700" alt="starting cloudshell" src="https://github.com/pavlinsrepo/Homework/assets/163166111/ad2d3a22-a422-4dbf-a685-a323955b8310">

---

## Deploying Wordpress and MySQL

- The command `aws eks update-kubeconfig` is used to update the kubeconfig file for your Amazon Elastic Kubernetes Service (EKS) cluster. This command is necessary to configure the kubectl CLI tool to communicate with your EKS cluster.

![Screenshot 2024-03-14 145124](https://github.com/pavlinsrepo/Homework/assets/163166111/f85d3e63-940a-4b1f-9034-8f9f99f5d511)

---
- When we update the kubeconfig file, it's time to put our yaml manifest contents, we will first put our mysql-secret manifest in mysql-secret file.
- Then apply manifest files with `kubectl apply command -f mysql-secret`
<img width="485" alt="applying the secret" src="https://github.com/pavlinsrepo/Homework/assets/163166111/62c6274f-5e5a-48f1-ad9f-9ab903e6bb7e">

---

- The next manifest yaml content that we need to put in a file is the mysql database and the service that is responsible for the traffic to the mysql database
- Once we put our content in the file, it's time to apply them
<img width="600" alt="apply the db manifests and the service " src="https://github.com/pavlinsrepo/Homework/assets/163166111/d1308800-1e24-47dd-a801-9455203b9634">

---
- The last manifest yaml file you need to apply is wordpress with the service which is responsible for exposing our website in the browser and routing the incoming traffic to wordpress.

<img width="600" alt="Now apply the yaml file for the wordpress and the loadbalancer" src="https://github.com/pavlinsrepo/Homework/assets/163166111/2c62ea52-8fce-4b79-8a3f-26c4de8a72fe">


---

- The final step is to see the External IP of our LoadBalancer which еxposes WordPress, through this DNS name we access WordPress via the browser. When we open the browser we just type DNS name from our Loadbalancer in the search engine and access wordpress.
<img width="788" alt="now type the following command to see the loadbalancers dns name" src="https://github.com/pavlinsrepo/Homework/assets/163166111/dbba78c0-920f-4659-bb8f-bc5bc8ff7c60">

---

- If you see this page in your browser after you have put the dns name, then you have followed the steps correctly and it turned out perfectly. Congratulations.

<img width="700" alt="congrats you made it" src="https://github.com/pavlinsrepo/Homework/assets/163166111/84728ce9-b835-4064-b64d-0c4b7c06d9d8">


---
## My Wordpress Blog
![Screenshot 2024-03-12 180032](https://github.com/pavlinsrepo/Homework/assets/163166111/4722fee0-d153-4f35-8677-843b738fdbb7)










