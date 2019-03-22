
# Prerequisites

Install kernel headers on all nodes in your cluster:
  * sudo apt-get install --yes linux-headers-$(uname -r)  # For Debian, Ubuntu
  * sudo yum install -y kernel-devel-$(uname -r)  # For RHEL, CentOS, Amazon Linux

## Deploying

Manually, using Helm:
* Clone this repo
* [Optional] Name your cluster in `.flowmill.clusterName`.
* Download a customized auth.yaml from the "Install" tab of your UI to ./static/auth.yaml.
* Run
```
helm install ./ --name flowmill-k8s --namespace flowmill --values values.yaml
```

Using [Ship](https://github.com/replicatedhq/ship):
```
brew tap replicatedhq/ship
brew install ship
ship init github.com/Flowmill/flowmill-k8s
```

## Upgrading

Manually, using Helm:
```
helm upgrade flowmill-k8s ./
```

Using Ship:
```
ship watch && ship update
```

