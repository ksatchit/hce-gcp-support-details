## Permissions Required For Chaos On GCP Resources/Services

### Compute Engine 

#### (Out Of Band) State Manipulation Chaos

```
compute.instances.get
compute.instances.list
compute.instances.stop
compute.instances.start
```
#### (In-VM) State, Network, Resource, API, DNS Chaos 

```
root/sudo user & usergroup
```

### Google Persistent Disks (GPD)

```
compute.disks.get
compute.instances.attachDisk
compute.instances.detachDisk
compute.disks.list
compute.instances.get
``` 

### CloudSQL State Manipulation Chaos

```
cloudsql.instances.get 
cloudsql.instances.update
cloudsql.instances.stopReplica
cloudsql.instances.startReplica
cloudsql.instances.failover
```

### GKE

```
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: litmus-admin
  namespace: #{INFRA_NAMESPACE}
  labels:
    name: litmus-admin
---
# Source: openebs/templates/clusterrole.yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: litmus-admin
  labels:
    name: litmus-admin
rules:
  # ***************************************************************************************
  # Permissions needed for preparing and monitor the chaos resources by chaos-runner
  # ***************************************************************************************

  # The chaos operator watches the chaosengine resource and orchestrates the chaos experiment..
  ## .. by creating the chaos-runner

  # for creating and monitoring the chaos-runner pods
  - apiGroups: [""]
    resources: ["pods"]
    verbs: ["create","delete","get","list","patch","update", "deletecollection"]
  - apiGroups: [""]
    resources: ["events"]
    verbs: ["create","get","list","patch","update"]

    # for fetching configmaps and secrets to inject into chaos-runner pod (if specified)
  - apiGroups: [""]
    resources: ["secrets", "configmaps"]
    verbs: ["get", "list"]

    # for tracking & getting logs of the pods created by chaos-runner to implement individual steps in the runner
  - apiGroups: [""]
    resources: ["pods/log"]
    verbs: ["get", "list", "watch"]

    # for configuring and monitor the experiment job by chaos-runner pod
  - apiGroups: ["batch"]
    resources: ["jobs"]
    verbs: ["create", "list", "get", "delete", "deletecollection"]

  # ********************************************************************
  # Permissions needed for creation and discovery of chaos experiments
  # ********************************************************************

  # The helper pods are created by experiment to perform the actual chaos injection ...
  # ... for a period of chaos duration

  # for creating and managing to execute comands inside target container
  - apiGroups: [""]
    resources: ["pods/exec","pods/eviction","replicationcontrollers"]
    verbs: ["get","list","create"]

    # for tracking & getting logs of the pods created by experiment pod to implement individual steps in the experiment
  - apiGroups: [""]
    resources: ["pods/log"]
    verbs: ["get", "list", "watch"]

  # for creating and monitoring liveness services or monitoring target app services during chaos injection
  - apiGroups: [""]
    resources: ["services"]
    verbs: ["create","get","list"]

    # for checking the app parent resources as deployments or sts and are eligible chaos candidates
  - apiGroups: ["apps"]
    resources: ["deployments", "statefulsets"]
    verbs: ["list", "get", "patch", "update"]

    # for checking the app parent resources as replicasets and are eligible chaos candidates
  - apiGroups: ["apps"]
    resources: ["replicasets"]
    verbs: ["list", "get"]

  # for checking the app parent resources as deamonsets and are eligible chaos candidates
  - apiGroups: ["apps"]
    resources: ["daemonsets"]
    verbs: ["list","get"]

    # for checking (openshift) app parent resources if they are eligible chaos candidates
  - apiGroups: ["apps.openshift.io"]
    resources: ["deploymentconfigs"]
    verbs: ["list", "get"]

    # for checking (argo) app parent resources if they are eligible chaos candidates
  - apiGroups: ["argoproj.io"]
    resources: ["rollouts"]
    verbs: ["list", "get"]

  # performs CRUD operations on the network policies
  - apiGroups: ["networking.k8s.io"]
    resources: ["networkpolicies"]
    verbs: ["create","delete","list","get"]

  # for creation, status polling and deletion of litmus chaos resources used within a chaos workflow
  - apiGroups: ["litmuschaos.io"]
    resources: ["chaosengines","chaosexperiments","chaosresults"]
    verbs: ["create","list","get","patch","update","delete"]

    # for experiment to perform node status checks and other node level operations like taint, drain in the experiment.
  - apiGroups: [""]
    resources: ["nodes"]
    verbs: ["patch", "get", "list", "update"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: litmus-admin
  labels:
    name: litmus-admin
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: litmus-admin
subjects:
  - kind: ServiceAccount
    name: litmus-admin
    namespace: #{INFRA_NAMESPACE}
    
```