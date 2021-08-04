[![Build](https://github.com/konveyor/move2kube-operator/workflows/Build/badge.svg "Github Actions")](https://github.com/konveyor/move2kube-operator/actions?query=workflow%3ABuild)
[![Docker Repository on Quay](https://quay.io/repository/konveyor/move2kube-operator/status "Docker Repository on Quay")](https://quay.io/repository/konveyor/move2kube-operator)
[![License](https://img.shields.io/:license-apache-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/konveyor/move2kube-operator/pulls)
[<img src="https://img.shields.io/badge/slack-konveyor/move2kube-green.svg?logo=slack">](https://kubernetes.slack.com/archives/CR85S82A2)

# Move2Kube-Operator

Operator to orchestrate [Move2Kube UI](https://github.com/konveyor/move2kube-ui) and [API](https://github.com/konveyor/move2kube-api).  

## Prerequisites

- Kubectl
- Helm 3
- A Kubernetes cluster

## Usage

### Helm chart

1. Configure kubectl to contact the K8s API server for your cluster.
2. Create a namespace and configure kubectl to use it:
   ```
   kubectl create namespace my-namespace
   kubectl config set-context --current --namespace my-namespace
   ```
3. Add this helm repo:
   ```
   helm repo add move2kube https://move2kube.konveyor.io
   helm repo update
   ```
4. To install without authentication run:
   ```
   helm install --set ingresshost='my.k8s.cluster.domain.com' my-move2kube move2kube/move2kube
   ```
   Replace `my.k8s.cluster.domain.com` with the domain where you K8s cluster is deployed.  

   If you need authentication then put the required details in a JSON file and run:
   ```
   helm install --set ingresshost='my.k8s.cluster.domain.com' --set ingresstls='my-tls-secret' --set-file 'auth=path/to/my/file.json' my-move2kube move2kube/move2kube
   ```
   Replace `my-tls-secret` with the name of the K8s secret that contains the certificate and private key required for TLS.  
   The schema for the JSON file containing authentication details can be found here: https://github.com/konveyor/move2kube-ui/blob/main/server.js#L202-L341  
   Example: https://github.com/konveyor/move2kube-demos/blob/main/samples/auth/auth.json

5. The helm chart will output the URL where you can access Move2Kube.  
   You can also do `kubectl get ingress` to get find the url and open it in the browser.  
   Example: `https://m2krelease-mynamespace.my.k8s.cluster.domain.com`

## Discussion

* For any questions reach out to us on any of the communication channels given on our website https://move2kube.konveyor.io/.
