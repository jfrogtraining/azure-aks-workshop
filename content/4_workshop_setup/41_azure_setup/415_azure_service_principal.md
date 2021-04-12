---
title: "Create a Service Principal"
chapter: false
weight: 415
pre: "<b>4.1.5 </b>"
---

To deploy our application with our CI/CD pipeline, we need Azure credentials. To do this, we will create an Azure service principal.

{{% notice info %}}
When you have applications, hosted services, or automated tools that needs to access or modify resources, you can create an identity for the app. This identity is known as a service principal. Access to resources is restricted by the roles assigned to the service principal, giving you control over which resources can be accessed and at which level. For security reasons, it's always recommended to use service principals with automated tools rather than allowing them to log in with a user identity.
{{% /notice %}}

1. In your Azure Cloud Shell, let's create an Azure Service Principal using the CLI.

```
az ad sp create-for-rbac
```






