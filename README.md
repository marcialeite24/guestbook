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
  - Push the Docker Image to IBM Cloud Container Registry
  - Verify the Image
  - Apply the Deployment
  - Forward the port to access the app locally
   
2. Autoscaling
  - Apply the Horizontal Pod Autoscaler
  - Check Autoscaler Status
  - Generate Load to Observe Autoscaling
  - Monitor Replica Scaling
  - Check the details of the Horizontal Pod Autoscaler
    
3. Rolling Updates and Rollbacks
  - Make changes to index.html or other components
  - Rebuild the Docker Image
  - Update the deployment.yaml file and apply changes
  - Restart the Application
  - View Deployment Rollout History
  - View Deployment Revision Details
  - Undo the Deployment
  - Verify the Rollback












