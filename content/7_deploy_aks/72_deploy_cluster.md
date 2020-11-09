---
title: "Deploy an AKS Cluster"
chapter: false
weight: 72
pre: "<b>7.2 </b>"
---

Now we are ready to deploy an AKS cluster.

1. First, let's get the latest version of Kubernetes that is available with the following command.

```
VERSION=$(az aks get-versions \
    --location $REGION_NAME \
    --query 'orchestrators[?!isPreview] | [-1].orchestratorVersion' \
    --output tsv)
```

2. Execute the following command to see the version.

``
echo $VERSION
``

3. Next, set an environment variable for the AKS cluster name.

``
AKS_CLUSTER_NAME=jfrog-aks-workshop-$RANDOM
``

4. Execute the following command to confirm the cluster name.

``
echo $AKS_CLUSTER_NAME
``

5. Now we are ready to deploy the AKS cluster. Execute the following command.

```
az aks create \
    --resource-group $RESOURCE_GROUP \
    --name $AKS_CLUSTER_NAME \
    --vm-set-type VirtualMachineScaleSets \
    --node-count 2 \
    --load-balancer-sku standard \
    --location $REGION_NAME \
    --kubernetes-version $VERSION \
    --network-plugin azure \
    --vnet-subnet-id $SUBNET_ID \
    --service-cidr 10.2.0.0/24 \
    --dns-service-ip 10.2.0.10 \
    --docker-bridge-address 172.17.0.1/16 \
    --generate-ssh-keys
```

6. Execute the following command to get connectivity to the cluster.

```
az aks get-credentials \
    --resource-group $RESOURCE_GROUP \
    --name $AKS_CLUSTER_NAME
```

7. To confirm connectivity, execute the following command to list the Kubernetes nodes.

``
kubectl get nodes
``
