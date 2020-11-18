---
title: "Deploy on Azure AKS"
chapter: false
weight: 7
pre: "<b>7 </b>"
---

We are now ready to deploy your image with Azure Kubernetes Service (AKS).

![AKS Architecture](/images/aks-architecture.svg)

1. Execute the following command to get connectivity to the cluster.

```
az aks get-credentials \
    --resource-group jfrog-azure-workshop \
    --name jfrog-azure-workshop-cluster
```

2. To confirm connectivity, execute the following command to list the Kubernetes nodes.

``
kubectl get nodes
``

![Kubectl Get Nodes](/images/kubectl-get-nodes.png)

3. First, let's create a namespace to provide isolation. Execute the following.

``
kubectl create namespace jfrog-azure-workshop
``

4. Next, we need to set our Artifactory registry credentials in order to pull the NPM application image. We will do this my creating Kubernetes secrets to store these. Execute the following command. Substitute your _server name_ and JFrog Platform credentials (_username_ and _API key_).

``
kubectl create secret docker-registry regcred 
    --namespace jfrog-azure-workshop
    --docker-server=$JFROG_SERVER_ID 
    --docker-username=$JFROG_USER
    --docker-password=$JFROG_APIKEY
``

5. We will use a Kubernetes deployment manifest to deploy the NPM application image. First, we must make a substitution in the file for the image that we want to deploy.

``
sed "s|imageName|$IMAGE_NAME|g" deployment.yaml > my-deployment.yaml
``

6. Now we can deploy with the following command.

``
kubectl apply -f my-deployment.yaml --namespace jfrog-azure-workshop
``

7. Execute the following to see your deployed pod.

``
kubectl get pods --namespace jfrog-azure-workshop
``

You should see you npm-app pod.

![Kubectl Get Pods](/images/kubectl-get-pods.png)

8. Now let's get the external IP so that we can view your application. Execute the following.

``
kubectl get services --namespace jfrog-azure-workshop
``

This will provide the EXTERNAL-IP.

![Kubectl External IP](/images/kubectl-external-ip.png)

9. In your browser, go to https://\<EXTERNAL-IP\> to view your deployed web application. 
10. Click through the self-signed certificate warning. You should see the following web application.

![NPM Application](/images/npm-app.png)


Congratulations! You have used Azure AKS to deploy the image that you built with the JFrog Platform.


