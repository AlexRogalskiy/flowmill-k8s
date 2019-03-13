
# Prerequisites

Flowmill will provide (via the "install" tab on your UI) a customized values-<customer>.yaml file for you.

* Download your values-<customer>.yaml and save in this repo's root directory.
* [optional] Name your cluster in `.flowmill.clusterName`.
* Install kernel headers on all nodes in your cluster:
  * sudo apt-get install --yes linux-headers-$(uname -r)  # For Debian, Ubuntu
  * sudo yum install -y kernel-devel-$(uname -r)  # For RHEL, CentOS, Amazon Linux

## Deploying

Manually, using Helm:
Clone this repo and copy the values-<customer>.yaml file provided by Flowmill to the root of the repo, then run:
```
helm install ./ --name flowmill-k8s --namespace flowmill --values values-<customer>.yaml
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

