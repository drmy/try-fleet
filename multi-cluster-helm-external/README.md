# My Multi-Cluster Helm External Example

The app will be deployed into the `mariadb` namespace.

The application will be customized as follows per environment:

* bj1
* bj2

```yaml
kind: GitRepo
apiVersion: fleet.cattle.io/v1alpha1
metadata:
  name: mariadb-helm-external
  namespace: fleet-default
spec:
  repo: https://github.com/drmy/try-fleet
  paths:
  - multi-cluster-helm-external
  targets:
  - name: bj1
    clusterSelector:
      matchLabels:
        env: bj1

  - name: bj2
    clusterSelector:
      matchLabels:
        env: bj2

```
