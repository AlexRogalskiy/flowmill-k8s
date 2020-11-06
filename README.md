
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
| `flowmill.clusterName`                      | Name of the cluster that will appear on the Flowmill dashboard.                                  | `<required>`                                              |
| `flowmill.tenantName`                       | Name of the tenant you want agents to send their metrics to. Must match name in Flowmill DB      | `<required>`                                              |
| `flowmill.version`                          | Agent version that should be deployed                                                            | `latest-v0.8`                                             |
| `flowmill.services.host`                    | URL to Flowmill dashboard where your data will be shown                                          | `app.flowmill.com`                                        |
| `flowmill.intake.host`                      | Flowmill intake component url                                                                    | `intake.flowmill.com`                                     |
| `flowmill.proxy.host`                       | Host to proxy via which to connect to Flowmill intake and services                               | `nil`                                                     |
| `flowmill.proxy.port`                       | Port for proxy via which to connect to Flowmill intake and services                              | `nil`                                                     |
| ------------------------------------------- | -----------------------------------------------                                                  | --------------------------------------------------------- |
| `agent.repository`                          | Image repository where Flowmill agents are located                                               | `gcr.io/flowmill-gcr/agent`                               |
| `agent.pullPolicy`                          | Pull policy for agent container images                                                           | `Always`                                                  |
| `agent.installKernelHeaders`                | Enable automatic kernel header fetching                                                          | `True`                                                    |
| `agent.useDockerMetadata`                   | Assumes docker is being used for kubernetes containers                                           | `True`                                                    |
| `agent.collectNomadMetadata`                | Automatically detect and enable enrichment using Nomad metadata if present                       | `True`                                                    |
| `agent.log.level`                           | Minimum log level of agent containers, possible are error, warn, info                            | `warn`                                                    |
| ------------------------------------------- | -----------------------------------------------                                                  | --------------------------------------------------------- |
| `awsCollector.repository`                   | Image repository where AWS collector images are located                                          | `gcr.io/flowmill-gcr/agent`                               |
| `awsCollector.pullPolicy`                   | Pull policy for AWS collector container images                                                   | `Always`                                                  |
| `awsCollector.log.level`                    | Minimum log level of AWS collector containers, possible are error, warn, info                    | `warn`                                                    |
| ------------------------------------------- | -----------------------------------------------                                                  | --------------------------------------------------------- |
| `relay.repository`                          | Image repository where kubernetes relay images are located                                       | `gcr.io/flowmill-gcr/agent`                               |
| `relay.pullPolicy`                          | Pull policy for kubernetes relay container images                                                | `Always`                                                  |
| `relay.log.level`                           | Minimum log level of kubernetes relay containers, possible are error, warn, info                 | `warn`                                                    |
| ------------------------------------------- | -----------------------------------------------                                                  | --------------------------------------------------------- |
| `watcher.repository`                        | Image repository where kubernetes watcher images are located                                     | `gcr.io/flowmill-gcr/agent`                               |
| `watcher.pullPolicy`                        | Pull policy for kubernetes watcher container images                                              | `Always`                                                  |
| `watcher.log.level`                         | Minimum log level of kubernetes watcher containers, possible are error, warn, info               | `warn`                                                    |
| ------------------------------------------- | -----------------------------------------------                                                  | --------------------------------------------------------- |
| `nodeSelector`                              | Node labels for pod assignment                                                                   | `{}`                                                      |
| `tolerations`                               | Toleration labels for pod assignment                                                             | `Exists = NoExecute, Exists = Noschedule`                 |
| `affinity`                                  | Affinity settings for pod assignment                                                             | `{}`                                                      |
| `rbac.create`                               | Create and use RBAC resources                                                                    | `true`                                                    |
| ------------------------------------------- | -----------------------------------------------                                                  | --------------------------------------------------------- |
