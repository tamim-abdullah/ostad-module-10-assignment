# DevOps Course Assignment: Zero Downtime Kubernetes Deployments

Asignment Document: [Doc File](https://docs.google.com/document/d/1HAf6QVTrH0gFed75FXMC-xyQ11CIVBnT3fxNHPsRsiM/edit?usp=sharing)
## Objective
Deploy a containerized web application to Kubernetes using Blue-Green, Canary, and Rolling Update strategies, ensuring zero downtime during updates.

## Prerequisites
- Docker Hub account
- Kubernetes cluster (Minikube, kind, or cloud-based)
- Installed tools: kubectl, docker, helm (optional), argocd (if using Argo CD/Rollouts)

## Part 1: Create and Push Docker Image

### Steps
1. Built a web application displaying its version (e.g., “Version 1”).
2. Containerized the app using a Dockerfile.
3. Pushed two versions to Docker Hub:
   - `v1`
   - `v2`
   - Tagged each as `latest` when applicable.

### Docker Hub Link
[Docker Hub Repository URL]

### Screenshot
*Insert screenshot of Docker Hub repository showing v1, v2, and latest tags here*

## Part 2: Blue-Green Deployment

### Implementation
1. Created two Kubernetes Deployments:
   - `blue` using image `v1`
   - `green` using image `v2`
2. Configured a Service initially pointing to `blue`.
3. Updated the Service selector to switch to `green`.
4. Verified zero downtime during the switch.

### Zero Downtime
Achieved by updating the Service selector to point to `green` while both Deployments were running.

### Screenshot
*Insert screenshot of Service switch and curl/browser output showing zero downtime here*

## Part 3: Rolling Update Deployment

### Implementation
1. Created a Kubernetes Deployment with the `latest` image.
2. Configured rolling update strategy:
   - Set `maxSurge` and `maxUnavailable` to ensure zero downtime.
3. Simulated an update by pushing a new `latest` image and updating the Deployment.

### Zero Downtime
Ensured by `maxSurge` allowing new pods to start before old ones terminate, and `maxUnavailable` keeping sufficient pods running.

### Screenshot
*Insert screenshot of rolling update progress and curl/browser output showing zero downtime here*

## Part 4: Canary Deployment (Optional)

### Implementation
1. Installed Argo Rollouts in the cluster.
2. Converted Deployment to a Rollout resource.
3. Defined a Canary strategy with gradual traffic shifts and pause steps.
4. Pushed a new `latest` image and triggered the rollout.

### Zero Downtime
Achieved by Argo Rollouts gradually shifting traffic to the new version while monitoring stability.

### Screenshot
*Insert screenshot of Argo Rollouts status and curl/browser output showing zero downtime here*

## Deliverables
- GitHub Repository: [GitHub Repo URL]
  - Contains source code, Dockerfile, and Kubernetes manifests.
- Docker Hub: [Docker Hub Repo URL]
- Screenshots/Videos: Included above for each strategy.
- This report: Details implementation and zero downtime approach.
