---
title: "Build Machine"
chapter: false
weight: 42
pre: "<b>4.2 </b>"
---

In this section, we will setup our build machine for building our NPM application. We will:

- Provision an Azure Virtual Machine for our build machine.
- Install build tools on our build machine.

1. In your Azure Cloud Shell, execute the following command to create a new Azure Resource group for our workshop. This resource group will contain all the resources for our workshop.

``
az group create --name azureworkshop --location westus
``

{{% notice info %}}
A resource group is a container that holds related resources for an Azure solution. The resource group can include all the resources for the solution. Generally, add resources that share the same lifecycle to the same resource group so you can easily deploy, update, and delete them as a group.
{{% /notice %}}

2. Execute the following command to create the build machine. This will create an Azure Virtual Machine using Ubuntu LTS into the _azureworkshop_ resource group. It will provision the admin user and SSH keys.

```
az vm create \
  --resource-group azureworkshop \
  --name buildVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
```

This command should result in a successful response.
![Azure Create VM](/images/azure-vm-create.png)

3. In the JSON command response, look for the _publicIpAddress_ field. Use this to connect to this new build machine.


```
ssh azureuser@<publicIpAddress>
```

{{% notice info %}}
Your Azure Cloud Shell may time out and disconnect. You can always re-establish your Azure Cloud Shell and reconnect to the build machine with this SSH command.
{{% /notice %}}

4. Next, we will install the Azure CLI on this build machine. Execute the following command.

``
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
``

5. Now authenticate the Azure CLI with your account. 

``
az login
``

![Azure Login](/images/azure-az-login.png)

6. Follow the instructions to authenticate in a browser with the provided code.

![Azure Login Code](/images/azure-az-login-code.png)

7. Return to your Azure Cloud Shell and your build machine. Specify the Azure subscription that we are using. This is the Azure subscription that you specified in previous steps.

``
az account set --subscription <workshop subscription>
``

![Azure Subscription Set](/images/azure-az-subscription.png)

{{% notice info %}}
An Azure subscription serves as a single billing unit for Azure resources in that services used in Azure are billed to a subscription. An Azure subscription is linked to a single account, the one that was used to create the subscription and is used for billing purposes. Within the subscription, resources can be provisioned as instances of the many Azure products and services.
{{% /notice %}}

8. Execute the following commands to install the build tools.

```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt update
sudo apt-get install -y jq npm docker.io apt-transport-https kubectl
```

9. Update NPM to the latest version with the following command.

``
sudo npm install -g npm@latest
``

We have provisioned our build machine, authenticated it with Azure and installed build tools. Next, let's download the workshop code.



