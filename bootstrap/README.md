# Permission fix
OpenShift GitOps has an expectation that the person applying applications at the cluster level is a kube-admin. The following allows for users that are in the cluster's RBAC group instructlab-admins to get the privileges needed to deploy this GitOps applicationset and view it in the argocd UI.

https://access.redhat.com/solutions/6989516


```
oc -n openshift-gitops patch argocd openshift-gitops --type=merge --patch "$(cat policies.yaml)"
```


## Clusterrole

Modify and add the following. This will allow for the management of knative and project assets.

```
oc create -f additional-cluster-role.yaml
```
