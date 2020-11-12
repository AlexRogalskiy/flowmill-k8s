
# Prerequisites

## Deploying

### Using Helm

* Add Flowmill helm repo

```console
helm repo add flowmill https://charts.flowmill.com \
  && helm repo update
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
brew tap replicatedhq/ship \
  && brew install ship \
  && ship init github.com/Flowmill/flowmill-k8s
```

## Upgrading

### Using Helm:

```console
# Get newest version of the chart
helm repo update \
  && helm upgrade flowmill-k8s flowmill/flowmill-k8s -f flowmill.yaml --namespace flowmill
```

### Using Ship:

```console
ship watch \
  && ship update
```

# Configuration

| Parameter                                   | Description                                                                                      | Default                                                   |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `auth.keyId`                                | The keyId of your Flowmill agent key                                                             | `<required>`                                              |
| `auth.keySecret`                            | The secret of your Flowmill agent key                                                            | `<required>`                                              |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `flowmill.clusterName`                      | Name of the cluster that will appear on the Flowmill dashboard.                                  | `<required>`                                              |
| `flowmill.version`                          | Agent version that should be deployed                                                            | `latest`                                                  |
| `flowmill.services.host`                    | URL to Flowmill dashboard where your data will be shown                                          | `app.flowmill.com`                                        |
| `flowmill.intake.host`                      | Flowmill intake component url                                                                    | `intake.flowmill.com`                                     |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `images.repository`                         | Image repository for Flowmill container images                                                   | `gcr.io/flowmill-gcr`                                     |
| `images.pullPolicy`                         | Pull policy for container images                                                                 | `Always`                                                  |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `log.console`                               | Enable containers logging to stdout                                                              | `false`                                                   |
| `log.level`                                 | Minimum log level of Flowmill containers. Options are error, warn, info                          | `warn`                                                    |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `agent.imageName`                           | Name of the Flowmill agents image                                                                | `agent`                                                   |
| `agent.fetchKernelHeaders`                  | Enable automatic kernel header fetching                                                          | `true`                                                    |
| `agent.useDockerMetadata`                   | Assumes docker is being used for kubernetes containers                                           | `true`                                                    |
| `agent.collectNomadMetadata`                | Automatically detect and enable enrichment using Nomad metadata if present                       | `true`                                                    |
| `agent.cpuMemIo.enabled`                    | Enable collection of CPU/Mem/IO data                                                             | `false`                                                   |
| `agent.nodeSelector`                        | Node labels for pod assignment                                                                   | `{}`                                                      |
| `agent.tolerations`                         | Toleration labels for pod assignment                                                             | `Exists = NoExecute, Exists = Noschedule`                 |
| `agent.affinity`                            | Affinity settings for pod assignment                                                             | `{}`                                                      |
| `agent.resources`                           | Set the resource requests and limits for the flowmill agent                                      | `{}`                                                      |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `awsCollector.imageName`                    | Image repository where AWS collector images are located                                          | `aws-collector`                                           |
| `awsCollector.nodeSelector`                 | Node labels for pod assignment                                                                   | `{}`                                                      |
| `awsCollector.tolerations`                  | Toleration labels for pod assignment                                                             | `{}`                                                      |
| `awsCollector.affinity`                     | Affinity settings for pod assignment                                                             | `{}`                                                      |
| `awsCollector.resources`                    | Set the resource requests and limits for AWS collector                                           | `{}`                                                      |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `k8sCollector.relay.imageName`              | Image repository where kubernetes relay images are located                                       | `k8s-relay`                                               |
| `k8sCollector.watcher.imageName`            | Image repository where kubernetes watcher images are located                                     | `k8s-watcher`                                             |
| `k8sCollector.nodeSelector`                 | Node labels for pod assignment                                                                   | `{}`                                                      |
| `k8sCollector.tolerations`                  | Toleration labels for pod assignment                                                             | `{}`                                                      |
| `k8sCollector.affinity`                     | Affinity settings for pod assignment                                                             | `{}`                                                      |
| `k8sCollector.relay.resources`              | Set the resource requests and limits for the k8s-relay                                           | `{}`                                                      |
| `k8sCollector.watcher.resources`            | Set the resource requests and limits for the k8s-watcher                                         | `{}`                                                      |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `rbac.create`                               | Create and use RBAC resources                                                                    | `true`                                                    |
| `podSecurityPolicy.enabled`                 | Create a PodSecurityPolicy for the flowmill agent                                                | `true`                                                    |
| `podSecurityPolicy.annotations`             | Annotations to add to the PodSecurityPolicy                                                      | `{}`                                                      |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `proxy.enabled`                             | Enable using a proxy to connect to Flowmill                                                      | `false`                                                   |
| `proxy.host`                                | Host to proxy via which to connect to Flowmill intake and services                               | `nil`                                                     |
| `proxy.port`                                | Port to proxy via which to connect to Flowmill intake and services                               | `nil`                                                     |
| `proxy.basicAuth`                           | The basic auth (`<username>:<password>`) to use to connect to the proxy                          | `nil`                                                     |
|---------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------|


