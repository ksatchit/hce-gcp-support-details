## Cluster Requirements 

- Kubernetes Vers: GKE Min. Is Supported. If setting up a self-managed Kubernetes cluster on compute instances, 1.22+ 
- Node Count: Min. 3
- OS: Preferably Ubuntu 20.04+ with Containerd or Container-Optimized OS 
- Resources: 32 vCPU / 64GB Mem / 600GB Disk
- Loadbalancer: Required (alternatively nginx ingress controller)

## List Of Images

*Note: The tags are subject to changes. Please check with the team before installation* 

```
    docker.io/harness/helm-init-container:latest
    docker.io/harness/accesscontrol-service-signed:77801
    docker.io/harness/cdcdata-signed:78109
    docker.io/chaosnative/harness-smp-chaos-driver:0.7.0
    docker.io/chaosnative/harness-smp-chaos-manager:0.7.3
    docker.io/chaosnative/harness-smp-chaos-web:0.7.1
    docker.io/harness/cv-nextgen-signed:78109
    k8s.gcr.io/defaultbackend-amd64:1.5
    docker.io/harness/delegate-proxy-signed:78108
    docker.io/harness/gateway-signed:2000137
    us.gcr.io/k8s-artifacts-prod/ingress-nginx/controller:v1.0.0-alpha.2
    docker.io/harness/manager-signed:78109
    docker.io/harness/le-nextgen-signed:67300
    docker.io/harness/log-service-signed:release-18
    docker.io/bitnami/minio:2022.8.22-debian-11-r0
    docker.io/harness/nextgenui-signed:0.336.3
    docker.io/harness/ng-auth-ui-signed:0.45.0
    docker.io/harness/ng-manager-signed:78109
    docker.io/harness/pipeline-service-signed:1.19.3
    docker.io/harness/platform-service-signed:77901
    docker.io/harness/policy-mgmt:v1.49.0
    docker.io/harness/ci-scm-signed:release-88-ubi
    docker.io/harness/template-service-signed:78109
    docker.io/harness/ti-service-signed:release-149
    docker.io/timescale/timescaledb-ha:pg13-ts2.6-oss-latest
    docker.io/bitnami/mongodb:4.2.19
    docker.io/bitnami/postgresql:14.4.0-debian-11-r9
    docker.io/harness/redis:6.2.7-alpine
    docker.io/curlimages/curl
    docker.io/harness/ti-service-signed:release-149
```
