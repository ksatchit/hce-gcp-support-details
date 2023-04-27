## 1. HCE Platform Essentials

### 1.1. HCE High-Level Architecture

- [x] HCE SMP Architecture Diagram On GCP [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-SMP-Architecture-Diagram-On-GCP.png)] [[Live Collaboration Link](https://excalidraw.com/#room=68a28ae7f6ac0df63cc9,VfK45r0Ku-EMdCSEvjLNeg)]

### 1.2. Chaos Experiment Functional Flow Diagrams 

- [ ] HCE Experiment Execution Functional Flow (Kubernetes & GCP Managed Services)[[image](link)][[Live Collaboration Link]()]
- [x] HCE Experiment Execution Functional Flow (Linux/GCP Compute Instances) [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-Linux-Chaos-Experiment-Flow.png)][[Live Collaboration Link](https://excalidraw.com/#room=0140424485a7f1245b69,VQKNny2RueeCcYq-KaY8eg)]

### 1.3. HCE Setup Prerequisites

- [ ] HCE SMP Setup Prerequisites
- [x] Sample Roles/Permissions Required for GCP Chaos [Link](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Permissions.md)

## 2. Example DRT Chaos Experiment: Simulation Of Availability Zone Failure 

### 2.1. Approach 

- [x] Google's suggestions for simulating zone failure [[Link](https://cloud.google.com/compute/docs/instance-groups/regional-mig-simulate-zonal-outage)]
  - Involves preconfiguring VMs with scripts and shutting down instances 
- [x] HCE Approaches to GCP AZ Failure for DRT
  - [x] Approach-1: Inject Network Blackhole On All Service Replicas In A Given Availability Zone [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-AZ-Failure-Simulation-Approach-1.png)][[Live Collaboration Link](https://excalidraw.com/#room=a4771ec76bfd4b2ffad3,ctv8jW6pJ07YfS7VdhlaAA)]
  - [x] Approach-2: Manipulate state (Scale down/Shut down) Cloud Resources In A Given Availability Zone [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-AZ-Failure-Simulation-Approach-2.png)][[Live Collaboration Link](https://excalidraw.com/#room=cf92d9fcd245f786a462,bRROwBoYl6LJ7tYEf-hnKA)]

### 2.2. Sample Implementation Of HCE Approach-1 (Blackhole) 

- [ ] GCP AZ Access Loss/Failure Experiment for DRT 
  - [x] Test Application Composition Diagram [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Bank-Of-Anthos.png)]
  - [x] Test Bed Deployment Diagram - Setup Without Redundancy to Illustrate Application Downtime Upon AZ Failure Simulation [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/App-Setup-Without-Redundancy.png)][[Live Collaboration Link](https://excalidraw.com/#room=a1e41248ac23284542f6,p190EVKJurRAMTerRJSzWw)]
  - [x] Test Bed Deployment Diagram - Setup With Redundancy to Illustrate Functional Application Upon AZ Failure Simulation [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/App-Setup-With-Redundancy.png)][[Live Collaboration Link](https://excalidraw.com/#room=438dd3cbeb5b0160ed7e,9wNjAzWlk3fJJHOh7LRAHw)]
  - [x] Experiment Execution Approach Schematic [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/Experiment-Execution-Approach-Schematic.png)][[Live Collaboration Link](https://excalidraw.com/#room=ce19994b332c23537ea6,ORPUILw7vEiq9zPnNchBVw)]
  - [ ] Experiment Configuration & Execution Screenshots (from HCE platform)

## 3. Observability Integrations 

- [ ] HCE Chaos & Observability  
   - [ ] Integration/Capabilities Summary 
   - [ ] Screenshots for chaos-annotated dashboards

## 4. Fault Support 
 
- [ ] Chaos Support for GCP Infra components & Managed Services 
  - [ ] Fault Support
    - [ ] GCP Compute Instance
    - [ ] GPD Block Devices
    - [ ] CloudSQL
    - [ ] GCS
    - [ ] Cloud Run Fns

## 5. SRE Aids for DRT: Guided Gameday, Reports & Dashboards 

- [ ] Guided Gameday Support In DRT Context 
   
