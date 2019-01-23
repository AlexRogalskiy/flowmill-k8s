
# Prerequisites

Flowmill will provide (via the "install" tab on your UI) an auth.yaml file for you. You can deploy this to your cluster manually and update the `flowmill.authYamlExistingSecret` value to that secret name, or simply paste the contents of this file into the `Values.yaml`.

* Download your auth.yaml and paste into Values.yaml or deploy manually.
* Optionally name your cluster in `.flowmill.clusterName`.
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

