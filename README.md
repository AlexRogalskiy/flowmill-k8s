
# Prerequisites

Install kernel headers on all nodes in your cluster:
  * sudo apt-get install --yes linux-headers-$(uname -r)  # For Debian, Ubuntu
  * sudo yum install -y kernel-devel-$(uname -r)  # For RHEL, CentOS, Amazon Linux

## Deploying

Manually, using Helm:
* Make sure you have access to the Flowmill frontend.  
* In the agents tab, create an agent key id and agent secret.
* Clone this repo
* Edit the values.yaml file.
- [Optional] Comment out the awsCollector for non-AWS environments
- Update the flowmill section with proper "customer" name
* Create a secret with your agent key id and agent secret
```
kubectl -n flowmill create secret generic flowmill-k8s-agent-key \
     --from-literal=flowmill_agent_key_id=KEY_ID_GOES_HERE \
     --from-literal=flowmill_agent_secret=SECRET_GOES_HERE
```
* Deploy the agents
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

