# EKS Cluster with Wordpress and MySQL using eksctl and Helm
This repository provides steps to create a Kubernetes cluster on AWS using eksctl and deploy Wordpress and MySQL using Helm.

## Requirements
- AWS account
- eksctl
- Helm
- Kubectl

## Creating the Cluster
Create a cluster configuration file named cluster.yaml and run the following command to create the cluster
`eksctl create cluster -f cluster.yaml`

Get the credentials for the cluster using the following command:
`aws eks update-kubeconfig --name cluster1`

## Deploying Wordpress and MySQL
- Create a PersistentVolumeClaim (PVC) for both Wordpress and MySQL to store data permanently.
- Create services for Wordpress and MySQL. Use an Elastic Load Balancer (ELB) for the Wordpress pods and a ClusterIp service for the MySQL pods.
- Create Wordpress and MySQL deployments using kustomization.yaml file.
