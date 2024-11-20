# Guestbook Application - Kubernetes and Docker Project

This project demonstrates building, deploying, autoscaling, and managing updates for a simple Guestbook application using Docker and Kubernetes.

Project Objectives
  1. Build and deploy a simple Guestbook application.
  2. Implement autoscaling using Horizontal Pod Autoscaler.
  3. Perform rolling updates and rollbacks to manage application changes.
  
Course: [Introduction to Containers w/ Docker, Kubernetes & OpenShift](https://www.coursera.org/learn/ibm-containers-docker-kubernetes-openshift?specialization=ibm-full-stack-cloud-developer) - [IBM Full Stack Software Developer](https://www.coursera.org/professional-certificates/ibm-full-stack-cloud-developer)


## Table of contents

- [Overview](#overview)
- [Technologies Used](#technologies-used)
- [Setup and Commands](#setup-and-commands)
  - [Build and Deploy](#build-and-deploy)
  - [Autoscaling](#autoscaling)
  - [Rolling Updates and Rollbacks](#rolling-updates-and-rollbacks)


## Overview
The Guestbook application is a lightweight web app with a text input for submitting messages. It demonstrates containerization, deployment, and scaling with Kubernetes.

## Technologies Used
- **Docker:** Containerizes the Guestbook application.
- **Kubernetes:** Orchestrates deployments, scaling, and updates.
- **IBM Cloud Container Registry:** Hosts the Docker images.

## Setup and Commands

1. Build and Deploy
  - Build the Guestbook Application
    ``` bash
    docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1
    ```
  - Push the Docker Image to IBM Cloud Container Registry
    ``` bash
    docker push us.icr.io/$MY_NAMESPACE/guestbook:v1
    ```
  - Verify the Image
    ``` bash
    ibmcloud cr images
    ```
  - Apply the Deployment
    ``` bash
    kubectl apply -f deployment.yml
    ```
  - Forward the port to access the app locally
    ``` bash
    kubectl port-forward deployment.apps/guestbook 3000:3000
    ```
   
2. Autoscaling
  - Apply the Horizontal Pod Autoscaler
    ``` bash
    kubectl autoscale deployment guestbook --cpu-percent=5 --min=1 --max=10
    ```
  - Check Autoscaler Status
    ``` bash
    kubectl get hpa guestbook
    ```
  - Generate Load to Observe Autoscaling
    ``` bash
    kubectl run -i --tty load-generator --rm --image=busybox:1.36.0 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- <your app URL>; done"
    ```
  - Monitor Replica Scaling
    ``` bash
    kubectl get hpa guestbook --watch
    ```
  - Check the details of the Horizontal Pod Autoscaler
    ``` bash
    kubectl get hpa guestbook
    ```
    
3. Rolling Updates and Rollbacks
  - Make changes to index.html or other components
  - Rebuild the Docker Image
    ``` bash
    docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1 && docker push us.icr.io/$MY_NAMESPACE/guestbook:v1
    ```
  - Update the deployment.yaml file and apply changes
    ``` bash
    kubectl apply -f deployment.yml
    ```
  - Restart the Application
    ``` bash
    kubectl port-forward deployment.apps/guestbook 3000:3000
    ```
  - View Deployment Rollout History
    ``` bash
    kubectl rollout history deployment/guestbook
    ```
  - View Deployment Revision Details
    ``` bash
    kubectl rollout history deployments guestbook --revision=2
    ```
  - Undo the Deployment
    ``` bash
    kubectl rollout undo deployment/guestbook --to-revision=1
    ```
  - Verify the Rollback
    ``` bash
    kubectl get rs
    ```
