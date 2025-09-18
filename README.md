# Template EIDFGPU CLuster Workflow

This repository contains a template workflow for code development using K8s.

A rapid development cycle from code writing to testing requires some initial setup within k8s.

The first step is to automatically pull the latest code version before running any tests in a pod. 

This allows development to be conducted on any device/VM with access to the repo (GitHub/GitLab) and testing to be completed on the cluster with just one `kubectl create` command.

This allows custom code/models to be prototyped on the cluster, but typically within a standard base image. 

However, if the Docker container also needs to be developed then GitHub actions can be used to automatically build a new image and publish it to Docker Hub if any changes to a Dockerfile is detected.

This repo contains a GitHub action to automatically build and publish a Docker image given any detected changes to the Dockerfile in the code/docker folder.

The repo also contains an example k8s job specification file that downloads and runs the python code held within the repo.

You will need to create two [GitHub secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions) to securely provide your Docker Hub username and access token.
