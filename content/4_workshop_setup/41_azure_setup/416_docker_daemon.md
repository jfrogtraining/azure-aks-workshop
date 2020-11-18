---
title: "Set up Docker Daemon"
chapter: false
weight: 415
pre: "<b>4.1.5 </b>"
---

Azure Cloud Shell does not include a Docker daemon by default. We can configure a remote Docker daemon instead with the following steps.

1. In your Azure Cloud Shell, execute the following command to create a remote Docker daemon machine. This will take a few minutes.

```
SUB_ID=$(az account show --query "id" -o tsv)
docker-machine create -d azure \
    --azure-subscription-id $SUB_ID \
    --azure-ssh-user azureuser \
    --azure-open-port 80 \
    --azure-size "Standard_DS2_v2" \
    docker-vm
```

2. When prompted click on the _devicelogin_ link to open a new browser tab.

![Azure Authenticate Device](/images/azure-authenticate-device.png)

3. Authenticate in the browser using the provided code. This will authenticated the new remote Docker daemon machine.

![Azure Authenticate Code](/images/azure-az-login-code.png)

{{%expand "What's going on here?" %}}
We are creating a Docker virtual machine as a remote Docker daemon. Our Azure Cloud Shell will be a Docker CLI client and communicate with the docker-vm virtual machine to execute Docker commands.
![Docker Machine](/images/docker-machine.png)
.{{% /expand%}}

4. When this completes, execute the following to configure Azure Cloud Shell to use this remote Docker daemon machine.

``
eval $(docker-machine env docker-vm --shell bash)
``

{{% notice info %}}
[docker-machine](https://docs.docker.com/machine/) lets you create Docker hosts on your computer, on cloud providers, and inside your own data center. It creates servers, installs Docker on them, then configures the Docker client to talk to them.
{{% /notice %}}

