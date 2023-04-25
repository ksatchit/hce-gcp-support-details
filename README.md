# HCE Support for GCP 

- [x] HCE SMP Architecture Diagram On GCP [[image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-SMP-Architecture-Diagram-On-GCP.png)] [[Live Collaboration Link](https://excalidraw.com/#room=68a28ae7f6ac0df63cc9,VfK45r0Ku-EMdCSEvjLNeg)]
- [x] Google's suggestions for simulating zone failure [[Link](https://cloud.google.com/compute/docs/instance-groups/regional-mig-simulate-zonal-outage)]
  - Involves preconfiguring VMs with scripts and shutting down instances 
- [x] HCE Approaches to GCP AZ Failure for DRT
  - [x] Approach-1: Inject Network Blackhole On All Service Replicas In A Given Availability Zone [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-AZ-Failure-Simulation-Approach-1.png)][[Live Collaboration Link](https://excalidraw.com/#room=a4771ec76bfd4b2ffad3,ctv8jW6pJ07YfS7VdhlaAA)]
  - [x] Approach-2: Manipulate state (Scale down/Shut down) Cloud Resources In A Given Availability Zone [[Image](https://github.com/ksatchit/hce-gcp-support-details/blob/main/HCE-AZ-Failure-Simulation-Approach-2.png)][[Live Collaboration Link](https://excalidraw.com/#room=cf92d9fcd245f786a462,bRROwBoYl6LJ7tYEf-hnKA)]
- [ ] GCP AZ Access Loss/Failure Experiment for DRT 
  - [x] Test Application Composition Diagram
  - [ ] Test Bed Deployment Diagram
  - [ ] Experiment Execution Approach Schematic
  - [ ] Experiment Configuration & Execution Screenshots (from HCE platform)
- [ ] HCE Chaos & Observability  
   - [ ] Integration/Capabilities Summary 
   - [ ] Screenshots for chaos-annotated dashboards
- [ ] HCE SMP Setup Prerequisites 
- [ ] Chaos Support for GCP Infra components & Managed Services 
  - [ ] Fault Support
    - [ ] GCP Compute Instance
    - [ ] GPD Block Devices
    - [ ] CloudSQL
    - [ ] GCS
    - [ ] Cloud Run Fns
  - [ ] Sample Roles/Permissions Required
- [ ] Guided Gameday Support In DRT Context 
   
