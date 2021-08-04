# Move2Kube Helm Chart

Move2Kube helps speed up the journey to Kubernetes.

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

5. The helm chart will output the URL where you can access Move2Kube.  
   You can also do `kubectl get ingress` to get find the url and open it in the browser.  
   Example: `https://m2krelease-mynamespace.my.k8s.cluster.domain.com`

## Discussion

* For any questions reach out to us on any of the communication channels given on our website https://move2kube.konveyor.io/.
