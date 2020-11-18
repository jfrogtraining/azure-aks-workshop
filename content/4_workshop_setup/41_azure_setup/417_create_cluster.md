---
title: "Create an AKS Cluster"
chapter: false
weight: 416
pre: "<b>4.1.6 </b>"
---

Before deploying an AKS cluster for the NPM application, we must first set up the required networking with the following steps.

1. Execute the following command to create a virtual network for the AKS cluster.

```
az network vnet create \
    --resource-group jfrog-azure-workshop \
    --location westus \
    --name aks-vnet \
    --address-prefixes 10.0.0.0/8 \
    --subnet-name aks-subnet \
    --subnet-prefixes 10.240.0.0/16
```

2. Retrieve and store the resultant subnet ID in an environment variable.

```
SUBNET_ID=$(az network vnet subnet show \
    --resource-group jfrog-azure-workshop \
    --vnet-name aks-vnet \
    --name aks-subnet \
    --query id -o tsv)
echo $SUBNET_ID
```

3. Now we are ready to create an AKS cluster. Let's get the latest version of Kubernetes that is available with the following command.

```
VERSION=$(az aks get-versions \
    --location westus \
    --query 'orchestrators[?!isPreview] | [-1].orchestratorVersion' \
    --output tsv)
echo $VERSION
```

4. Now we are ready to create the AKS cluster. Execute the following command.

```
az aks create \
    --resource-group jfrog-azure-workshop \
    --name jfrog-azure-workshop-cluster \
    --vm-set-type VirtualMachineScaleSets \
    --node-count 2 \
    --load-balancer-sku standard \
    --location westus \
    --kubernetes-version $VERSION \
    --network-plugin azure \
    --vnet-subnet-id $SUBNET_ID \
    --service-cidr 10.2.0.0/24 \
    --dns-service-ip 10.2.0.10 \
    --docker-bridge-address 172.17.0.1/16 \
    --generate-ssh-keys
```

The response will provide a large JSON object showing the cluster attributes.

![Azure Create Cluster](/images/azure-create-cluster.png)

{{%expand "What is this command doing?" %}}
![AKS Deploy](/images/aks-deploy-architecture.svg)
.{{% /expand%}}


