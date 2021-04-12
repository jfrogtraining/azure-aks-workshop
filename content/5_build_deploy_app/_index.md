---
title: "Build and Deploy the App"
chapter: false
weight: 5
pre: "<b>5 </b>"
---

In this section, we will set up our CI/CD pipeline with JFrog Pipelines. Our pipeline, will take our application and build a docker image. Then it will promote it. Finally, it will deploy it to our Azure AKS Cluster. We will:

- Set up our JFrog Pipelines integrations to connect to GitHub, our Artifactory and Azure AKS Kubernetes cluster.
- Update our CI/CD pipeline.
- Add our CI/CD pipeline to JFrog Pipelines. Then build and deploy our app.

{{% notice info %}}
In this workshop, we use Docker, but the JFrog Platform is a universal solution supporting all major package formats including Alpine, Maven, Gradle, Docker, Conda, Conan, Debian, Go, Helm, Vagrant, YUM, P2, Ivy, NuGet, PHP, NPM, RubyGems, PyPI, Bower, CocoaPods, GitLFS, Opkg, SBT and more.
{{% /notice %}}

