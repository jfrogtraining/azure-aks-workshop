---
title: "Get the Workshop Code"
chapter: false
weight: 416
pre: "<b>4.1.6 </b>"
---

The workshop code is located at [https://github.com/jfrogtraining/azure-aks-workshop](https://github.com/jfrogtraining/azureworkshop) GitHub repository. We will fork and clone this repository in order to pull the required workshop files and scripts.

1. Go to [https://github.com/jfrogtraining/azure-aks-workshop](https://github.com/jfrogtraining/azureworkshop) and fork this repository to your GitHub account. 

![GitHub Fork](/images/github-fork.png)

![GitHub Repo Forked](/images/github-repo-forked.png)

2. Clone the repo. You can do this locally in the Azure Cloud Shell. You can open another Azure Cloud Shell session.

``
git clone https://github.com/<your user name>/azure-aks-workshop.git
``

3. Set your GitHub username and email.

``
git config --global user.name <GitHub username>
``

``
git config --global user.email <GitHub email>
``

4. You can use the Azure Cloud Shell editor to explore the code.

![Azure Cloud Shell Editor](/images/azure-cloud-shell-editor.png)

5. We will also need a GitHub personal access token to make updates and for JFrog Pipelines CI/CD. You may already have one. If not, follow [these instructions](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token) to create one. Copy it to your notepad. 
   
    Ensure it has these minimum GitHub permissions:

    - repo (all)
    - admin:repo_hook (read, write)
    - admin:public_key (read, write)
