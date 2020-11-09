---
title: "Deploy Your Image with AKS"
chapter: false
weight: 73
pre: "<b>7.3 </b>"
---

With an AKS cluster deployed, we are now ready to deploy our NPM application!  

1. First, let's create a namespace to provide isolation. Execute the following.

``
kubectl create namespace azureworkshop
``

2. Next, we need to set our Artifactory registry credentials in order to pull the NPM application image. We will do this my creating Kubernetes secrets to store these. Execute the following command. Substitute your _server name_ and JFrog Platform credentials (_username_ and _API key_).

```
kubectl create secret docker-registry regcred \
    --namespace azureworkshop \
    --docker-server=<server name>.jfrog.io \
    --docker-username=<username/email> \
    --docker-password=<api key>
```

3. We will use a Kubernetes deployment manifest to deploy the NPM application image. First, we must make a substitution in the file for the image that we want to deploy. Substitute your _server name_.

``
sed -i 's/server/<server name>/g' deployment.yaml > my-deployment.yaml
``

4. Now we can deploy with the following command.

``
kubectl apply -f my-deployment.yaml --namespace azureworkshop
``
