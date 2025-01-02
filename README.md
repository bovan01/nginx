# DKP Custom Catalog Application: Nginx

1. Set the K8s context to the DKP management cluster.
2. Set the namespace to the relevant project as an environmental variable:

```bash
export NAMESPACE=[your_namespace]
````

Copy and paste the following into the terminal to deploy to the DKP catalog:

```bash
kubectl apply -f - <<EOF
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: nginx
  namespace: ${NAMESPACE}
  labels:
    kommander.d2iq.io/gitapps-gitrepository-type: catalog
    kommander.d2iq.io/gitrepository-type: catalog
spec:
  interval: 1m0s
  ref:
    branch: main
  timeout: 1m0s
  url: https://github.com/bovan01/nginx
EOF
```
