---
title: "Set up our JFrog Pipelines Integrations"
chapter: false
weight: 51
pre: "<b>5.1 </b>"
---

Our CI/CD pipeline requires access to GitHub to pull our code, access to JFrog Artifactory to publish our Docker image and build info and access to the AKS cluster to deploy our application. We will set up JFrog Pipelines integrations to enable these.

![Pipelines Integration](/images/pipeline-integrations-diagram.png)

{{% notice info %}}
An Integration connects Pipelines to an external service/tool. Each integration type defines the endpoint, credentials and any other configuration detail required for Pipelines to exchange information with the service. All credential information is encrypted and held in secure storage, in conformance with best security practices.
{{% /notice %}}


1. In your JFrog Platform instance, go to **Administration** > **Pipelines** > **Integrations**.

2. Click **Add an Integration**.

3. For the **Name**, enter _github_integration_.

4. For **Integration Type**, select **GitHub**.

5. Copy and paste your GitHub personal access token.

   Ensure it has these minimum GitHub permissions:

    - repo (all)
    - admin:repo_hook (read, write)
    - admin:public_key (read, write)
    
6. Click **Test connection** to validate. 

7. Click **Create** to create the integration.

![GitHub Integration](/images/github-integration.png)

8. Click **Add an Integration** again.

9. For the **Name**, enter _artifactory_integration_.

10. For **Integration Type**, select **Artifactory**.

11. Click **Get API Key** to generate an API key.

12. Click **Test connection** to validate.

13. Click **Create** to create the integration.

![Artifactory Integration](/images/artifactory-integration.png)

14. Click **Add an Integration** again.

15. For the **Name**, enter _aks_integration_.

16. For **Integration Type**, select **Kubernetes**.

17. Copy and paste your AKS Kubernetes cluster kubeconfig.

18. Click **Create** to create the integration.

![AKS Integration](/images/aks-integration.png)

Congratulations! We have created the integrations that are required for our CI/CD pipeline.
