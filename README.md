# EKS-Blueprints-for-CDK
## Architecture Diagram
![Architecture for EKS Blueprints](./Images/EKS.png)

Applications represent the actual workloads that run within a Kubernetes cluster. The framework leverages a GitOps approach for deploying applications onto clusters.

![Architecture for EKS Blueprints](./Images/EKS_2.png)

## Clusters
A cluster is simply an EKS cluster. EKS Blueprints provide for customizing the compute options you leverage with your clusters. The framework currently supports EC2, Fargate and BottleRocket instances. To specify the type of compute you want to use for your cluster, you supply a ClusterProvider object to your blueprint. The framework defaults to leveraging the EC2ClusterProvider.
