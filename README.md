
## Deploying

Manually, using Helm:
* Clone this repo
* Download a customized version of flowmill.yaml from app.flowmill.com or manually edit the flowmill.yaml file
* Run
```
helm install ./ --name flowmill-k8s --namespace flowmill --values flowmill.yaml
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
helm upgrade flowmill-k8s ./ -f flowmill.yaml --namespace flowmill
```

Using Ship:
```
ship watch && ship update
```
