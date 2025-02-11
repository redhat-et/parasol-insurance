# Permission fix
OpenShift GitOps has an expectation that the person applying applications at the cluster level is a kube-admin.

https://access.redhat.com/solutions/6989516


```
oc -n openshift-gitops patch argocd openshift-gitops --type=merge --patch "$(cat policies.yaml)"
```


## Clusterrole

Modify and add the following 

```
oc edit ClusterRole/openshift-gitops-openshift-gitops-argocd-application-controller
```


```
- apiGroups:
  - project.openshift.io
  resources:
  - '*'
  verbs:
  - '*'
- apiGroups:
  - serving.kserve.io
  resources:
  - '*'
  verbs:
  - '*'
```
