# Permission fix
OpenShift GitOps has an expectation that the person applying applications at the cluster level is a kube-admin.

https://access.redhat.com/solutions/6989516


```
oc -n openshift-gitops patch argocd openshift-gitops --type=merge --patch "$(cat policies.yaml)"
```
