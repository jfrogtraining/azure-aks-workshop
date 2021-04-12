---
title: "Create an AKS Cluster"
chapter: false
weight: 416
pre: "<b>4.1.6 </b>"
---

Before creating an AKS cluster for our application, we must first set up the required networking with the following steps.

1. Now we are ready to create an AKS cluster. In your Azure Cloud Shell, let's get the latest version of Kubernetes that is available with the following command.

```
VERSION=$(az aks get-versions \
    --location $REGION \
    --query 'orchestrators[?!isPreview] | [-1].orchestratorVersion' \
    --output tsv)
echo $VERSION
```

2. Let's create an environment variable for the cluster name.

```
CLUSTER_NAME=jfrog-azure-workshop-cluster
echo $CLUSTER_NAME
```

2. Now we are ready to create the AKS cluster. Execute the following command. This will take a few minutes. We can move onto the next step while we wait.

```
az aks create \
    --resource-group $RESOURCE_GROUP \
    --name $CLUSTER_NAME \
    --vm-set-type VirtualMachineScaleSets \
    --node-count 2 \
    --load-balancer-sku standard \
    --location $REGION \
    --kubernetes-version $VERSION \
    --network-plugin azure \
    --generate-ssh-keys \
    --enable-managed-identity
```

{{%expand "What is this command doing?" %}}
![AKS Deploy](/images/aks-deploy-architecture.svg)
.{{% /expand%}}

3. Next, let's update our kubeconfig to get access to his cluster.

``
az aks get-credentials --resource-group $RESOURCE_GROUP --name $CLUSTER_NAME
``

{{% notice info %}}
A kubeconfig file is a file used to configure access to Kubernetes clusters when used in conjunction with the kubectl commandline tool (or other clients).
{{% /notice %}}

4. Finally, execute the following command and copy the kubeconfig so that we can use it to access the cluster from our CI/CD pipeline.

``
cat ~/.kube/config
``
![kubeconfig](/images/azure-kubeconfig.png)

