## Deploying:

* Download your auth.yaml file from the UI; drop it in the config/ subdirectory
* Optional: update config/config.yaml with your Kubernetes cluster name
* Install kernel headers on all nodes in your cluster:
  * sudo apt-get install --yes linux-headers-$(uname -r)  # For Debian, Ubuntu
  * sudo yum install -y kernel-devel-$(uname -r)  # For RHEL, CentOS, Amazon Linux
* helm install ./ --name flowmill-k8s --namespace flowmill

## Upgrading:

* helm upgrade flowmill-k8s ./
