
# Prerequisites

Install kernel headers on all nodes in your cluster:
  * `sudo apt-get install --yes "linux-headers-$(uname -r)"`  # For Debian, Ubuntu
  * `sudo yum install -y "kernel-devel-$(uname -r)"`  # For RHEL, CentOS, Amazon Linux

## Deploying

Manually, using Helm:
* Clone this repo
* Download a customized version of flowmill.yaml from app.flowmill.com or manually edit the flowmill.yaml file
* Run
```
helm install ./ --name flowmill-k8s --namespace flowmill --values flowmill.yaml --values values.yaml
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
helm upgrade flowmill-k8s -f flowmill.yaml -f values.yaml ./
```

Using Ship:
```
ship watch && ship update
```

