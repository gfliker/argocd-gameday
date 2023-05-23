# argocd-gameday
This repository is intended for training purposes with ArgoCD

## Activity #1 - Setup
Users should fork this repo and set it up so that ArgoCD is referencing their fork and NOT this repo (ie `jmmclean/argocd-gameday`). 

To start a local environment, engineers should first install minikube and start it using the below command (or similar):
```shell
minikube start --cpus 4 --memory 16384  # start minikube w/ 4 cores and 16GB of memory
```

We leverage Tilt to orchestrate bootstrapping our Minikube K8s cluster. To start managing our apps, teams should run the below command:
```shell
tilt up -- --with app-of-apps
```

## Activity #2 - Add a new application for Argo Rollouts
Create a new namespace called `demo-1` that will be used for deploying this new application. The Kubernetes manifests of the application to be deployed should be below:
```
https://github.com/argoproj/rollouts-demo/tree/master/examples/canary
```

This application needs to be managed by the Application of Applications before proceeding to the next step. Also, the ArgoCD Application Project should be `demo-1` and that project should ONLY have access to the `demo-1` namespace. 

> Tip: you should reference the existing ArgoCD structure for samples on where to put Application Project manifests

## Activity #3 - Add a new application for Argo Rollouts with Istio
Create a new namespace called `demo-2` that will be used for deploying this new application. The Kubernetes manifests of the application to be deployed should be below:
```
https://github.com/argoproj/rollouts-demo/tree/master/examples/istio-subset
```

This application needs to be managed by the Application of Applications before proceeding to the next step. Also, the ArgoCD Application Project should be `demo-2` and that project should ONLY have access to the `demo-2` namespace. 

> Hint: Istio is available in this repository, however it needs to be deployed via the ArgoCD application of applications

## Activity #4 - Upgrade ArgoCD
Currently, ArgoCD is sitting on version `2.5.4`. Engineers should examine existing patterns and upgrade ArgoCD to version `2.7.2`.
