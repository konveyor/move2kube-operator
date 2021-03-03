[![Build](https://github.com/konveyor/move2kube-operator/workflows/Build/badge.svg "Github Actions")](https://github.com/konveyor/move2kube-operator/actions?query=workflow%3ABuild)
[![Docker Repository on Quay](https://quay.io/repository/konveyor/move2kube-operator/status "Docker Repository on Quay")](https://quay.io/repository/konveyor/move2kube-operator)
[![License](https://img.shields.io/:license-apache-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/konveyor/move2kube-operator/pulls)
[<img src="https://img.shields.io/badge/slack-konveyor/move2kube-green.svg?logo=slack">](https://kubernetes.slack.com/archives/CR85S82A2)

# Move2Kube-Operator

Operator to orchestrate [Move2Kube UI](https://github.com/konveyor/move2kube-ui) and [API](https://github.com/konveyor/move2kube-api).

## Usage

### Helm chart

```
helm repo add move2kube https://move2kube.konveyor.io
helm repo update
helm install --set ingresshost='my.k8s.cluster.domain.com' m2krelease move2kube/move2kube
```
Then do `kubectl get ingress` to get find the url and open it in the browser.  
Example: `https://m2krelease-mynamespace.my.k8s.cluster.domain.com`

For TLS uncomment the line `#ingresstls: my-tls-secret` in `values.yaml` and replace with the name of the TLS secret.

## Discussion

* For any questions reach out to us on any of the communication channels given on our website https://move2kube.konveyor.io/.
