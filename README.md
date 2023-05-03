## 1. HCE Platform Essentials

### 1.1. HCE High-Level Architecture

- [x] HCE SMP Architecture Diagram On GCP [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-SMP-Architecture-Diagram-On-GCP.png)] [[Live Collaboration Link](https://excalidraw.com/#room=68a28ae7f6ac0df63cc9,VfK45r0Ku-EMdCSEvjLNeg)]

### 1.2. Chaos Experiment Functional Flow Diagrams 

- [x] HCE Experiment Execution Functional Flow (Linux/GCP Compute Instances) [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-Linux-Chaos-Experiment-Flow.png)][[Live Collaboration Link](https://excalidraw.com/#room=0140424485a7f1245b69,VQKNny2RueeCcYq-KaY8eg)]

### 1.3. HCE Setup Prerequisites

- [x] HCE SMP Setup Prerequisites [[Link](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-SMP-Prerequisites.md)]
- [x] Sample Roles/Permissions Required for GCP Chaos [[Link](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Permissions.md)]
- [x] Setting up SSO access using Azure AD [[Link](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/harness-provisioning-tutorial)]

## 2. Example DRT Chaos Experiment: Simulation Of Availability Zone Failure 

### 2.1. Approach 

- [x] Google's suggestions for simulating zone failure [[Link](https://cloud.google.com/compute/docs/instance-groups/regional-mig-simulate-zonal-outage)]
  - Involves preconfiguring VMs with scripts and shutting down instances 
- [x] HCE Approaches to GCP AZ Failure for DRT
  - [x] **Approach-1**: Inject Network Blackhole On All Service Replicas In A Given Availability Zone [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-AZ-Failure-Simulation-Approach-1.png)][[Live Collaboration Link](https://excalidraw.com/#room=a4771ec76bfd4b2ffad3,ctv8jW6pJ07YfS7VdhlaAA)]
  - [x] **Approach-2**: Manipulate state (Scale down/Shut down) Cloud Resources In A Given Availability Zone [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-AZ-Failure-Simulation-Approach-2.png)][[Live Collaboration Link](https://excalidraw.com/#room=cf92d9fcd245f786a462,bRROwBoYl6LJ7tYEf-hnKA)]

### 2.2. Sample Implementation Of HCE Approach-1 (Blackhole) 

- [ ] GCP AZ Access Loss/Failure Experiment for DRT 
  - [x] Test Application Composition Diagram [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Bank-Of-Anthos.png)]
  - [x] Test Bed Deployment Diagram - Setup Without Redundancy to Illustrate Application Downtime Upon AZ Failure Simulation [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/App-Setup-Without-Redundancy.png)][[Live Collaboration Link](https://excalidraw.com/#room=a1e41248ac23284542f6,p190EVKJurRAMTerRJSzWw)]
  - [x] Test Bed Deployment Diagram - Setup With Redundancy to Illustrate Functional Application Upon AZ Failure Simulation [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/App-Setup-With-Redundancy.png)][[Live Collaboration Link](https://excalidraw.com/#room=438dd3cbeb5b0160ed7e,9wNjAzWlk3fJJHOh7LRAHw)]
  - [x] Experiment Execution Approach Schematic [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Experiment-Execution-Approach-Schematic.png)][[Live Collaboration Link](https://excalidraw.com/#room=ce19994b332c23537ea6,ORPUILw7vEiq9zPnNchBVw)]


## 3. Observability Integrations 

- [x] **Native Chaos Metrics**   
  - [x] Chaos Prometheus Metrics [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Chaos-Prometheus-Metrics.png)]
  - [x] Screenshot for chaos-annotated Grafana dashboard [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Chaos-Annotated-Dashboard-On-Grafana.png)]
- [x] **Observability Integrations via Pipelines** 
  - [x] Continuous Verification Step in Harness Pipelines [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Continuous-Verification-Pipeline-Step.png)] 
  - [x] Anomaly Detection via CV [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Anomaly-Detection-Via-CV.png)]
  - [x] Possible Observability Integrations/Health Sources In Harness [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Possible-Observability-Integrations-In-Harness.png)]
- [x] **Chaos Integration With SRM**
  - [x] Opt-In Model To Generate SRM Events Upon Chaos [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Opt-In-Mechanism-For-SRM-Events.png)]
  - [x] Chaos As A Change Event Source To Track SLO/Error Budget [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Chaos-As-A-Change-Event-Source-In-SRM.png)]

## 4. Fault Support for GCP Infra Components & Managed Services

### Available 

  - **GCP Compute Instance**
    - [x] Stop/Start Unmanaged Instance  
    - [x] Stop/Start Managed Instance
  - **GPD Block Devices**
    - [x] Detach/Reattach GPD to Specific Instances 
    
### In-Progress (near-term) 

  - **CloudSQL**
    - [x] Stop/Start Instance [master, failover (legacy config scheme), read-only]
    - [x] Trigger Failover (new config scheme with synchronous mirroring on disks) 

### Roadmap (mid-term)

*Note: Using the current network, dns and http experiments in Kubernetes, failed dependencies involving the below services can already be injected/simulated. This approach also has a low-blast radius.* 

*The faults described in the below list are mostly misconfiguration/state manipulation/access control faults on the services, which have a global impact.*  

  - **GCS**
    - [x] Modify ACLs    
  - **Pub/Sub** 
    - [x] Modify Message Deadlines
    - [x] Delete Topics
    - [x] Modify ACLs
  - **Cloud Run/Fns**
    - [x] Modify ACLs

## 5. SRE Aids for DRT: Guided Gameday, Reports & Dashboards 

- [x] Guided Gameday Support In DRT Context 
  - [x] Gameday Journey [[gameday-1](https://github.com/ksatchit/hce-gcp-support-details/blob/main/gameday-1.png)] [[gameday-2](https://github.com/ksatchit/hce-gcp-support-details/blob/main/gameday-2.png)] [[gameday-3](https://github.com/ksatchit/hce-gcp-support-details/blob/main/gameday-3.png)] [[gameday-4](https://github.com/ksatchit/hce-gcp-support-details/blob/main/gameday-4.png)] [[gameday-5](https://github.com/ksatchit/hce-gcp-support-details/blob/main/gameday-5.png)]  
- [x] Experiment History [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Experiment-Run-History.png)]
- [x] Overall Chaos Statistics [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Chaos-Statistics.png)]
   
