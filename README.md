
# Prerequisites

## Deploying

### Using Helm

* Clone this repo

* Download a customized version of flowmill.yaml from app.flowmill.com or manually edit the flowmill.yaml file

### Helm 3

* Create a namespace for the flowmill agent if using Helm 3

```console
kubectl create namespace flowmill
```

* Install the agent

```console
helm install --namespace flowmill --values flowmill.yaml flowmill ./
```

### Helm 2

* Install the agent

```console
helm install ./ --name flowmill-k8s --namespace flowmill --values flowmill.yaml
```

### Using [Ship](https://github.com/replicatedhq/ship)

```console
brew tap replicatedhq/ship
brew install ship
ship init github.com/Flowmill/flowmill-k8s
```

## Upgrading

Manually, using Helm:

```console
helm upgrade flowmill-k8s ./ -f flowmill.yaml --namespace flowmill
```

Using Ship:

```console
ship watch && ship update
```
