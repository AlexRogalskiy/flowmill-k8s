
# Prerequisites

## Deploying

### Using Helm

* Add Flowmill helm repo

```console
helm repo add flowmill https://charts.flowmill.com

helm repo update
```

* Download a customized version of flowmill.yaml from app.flowmill.com

#### Helm 3

* Create a namespace for the flowmill agent if using Helm 3

```console
kubectl create namespace flowmill
```

* Install the agent

```console
helm install --namespace flowmill --values flowmill.yaml flowmill flowmill/flowmill-k8s
```

#### Helm 2

* Install the agent

```console
helm install flowmill/flowmill-k8s --name flowmill-k8s --namespace flowmill --values flowmill.yaml
```

### Using [Ship](https://github.com/replicatedhq/ship)

```console
brew tap replicatedhq/ship
brew install ship
ship init github.com/Flowmill/flowmill-k8s
```

## Upgrading

### Using Helm:

```console
# Get newest version of the chart
helm repo update

helm upgrade flowmill-k8s flowmill/flowmill-k8s -f flowmill.yaml --namespace flowmill
```

### Using Ship:

```console
ship watch && ship update
```
