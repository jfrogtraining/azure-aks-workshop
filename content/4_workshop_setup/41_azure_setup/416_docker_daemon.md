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

2. When this complete, execute the following to configure Azure Cloud Shell to use this remote Docker daemon machine.

``
eval $(docker-machine env docker-vm --shell bash)
``

