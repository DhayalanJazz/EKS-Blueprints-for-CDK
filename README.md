# EKS-Blueprints-for-CDK
## Architecture Diagram
![Architecture for EKS Blueprints](./Images/EKS.png)

EKS Blueprints allows you to configure and deploy what we call blueprint clusters. A blueprint combines clusters, add-ons, and teams into a cohesive object that can be deployed as a whole. Once a blueprint is configured, it can be easily deployed across any number of AWS accounts and regions. Blueprints also leverage GitOps tooling to facilitate cluster bootstrapping and workload onboarding.

![Architecture for EKS Blueprints](./Images/EKS_2.png)

| Concept | Description |
| --- | --- |
| Blueprint | A blueprint combines clusters, add-ons, and teams into a cohesive object that can deployed as a whole. |
| Cluster | An EKS Cluster deployed following best practices. |
| Resource Provider | Resource providers are abstractions that supply external AWS resources to the cluster (e.g. hosted zones, VPCs, etc.). |
| Add-on | Allow you to configure, deploy, and update the operational software, or add-ons, that provide key functionality to support your Kubernetes applications. |
| Teams | A logical grouping of IAM identities that have access to a Kubernetes namespace(s), or cluster administrative access depending upon the team type. |
| Pipelines | Continuous Delivery pipelines for deploying clusters and add-ons. |
| Application | An application that runs within an EKS Cluster. |

## Application
Applications represent the actual workloads that run within a Kubernetes cluster. The framework leverages a GitOps approach for deploying applications onto clusters.

## Clusters
A cluster is simply an EKS cluster. EKS Blueprints provide for customizing the compute options you leverage with your clusters. The framework currently supports EC2, Fargate and BottleRocket instances. To specify the type of compute you want to use for your cluster, you supply a ClusterProvider object to your blueprint. The framework defaults to leveraging the EC2ClusterProvider.

## Resource Provider

A resource is a CDK construct that implements IResource interface from @aws-cdk/core which is a generic interface for any AWS resource. An example of a resource could be a hosted zone in Route53 IHostedZone , an ACM certificate ICertificate , a VPC or even a DynamoDB table  which could be leveraged either in add-ons or teams.

ResourceProviders enable customers to supply resources for add-ons, teams, and/or post-deployment steps.

## Add-on

Add-ons Allow you to configure, deploy, and update the operational software, or add-ons, that provide key functionalities to support your Kubernetes applications.

For examples, the MetricsServerAddon only deploys the Kubernetes manifests that are needed to run the Kubernetes Metrics Server. By contrast, the AWSLoadBalancerControllerAddon deploys Kubernetes YAML, in addition to creating resources via AWS APIs that are needed to support the AWS Load Balancer Controller.



## Pipeline

Pipelines allow you to configure Continuous Delivery (CD) pipelines for your cluster blueprints that are directly integrated with your Git provider.
