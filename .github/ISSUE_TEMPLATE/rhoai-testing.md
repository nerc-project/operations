---
name: RHOAI Testing
about: Testing RHOAI Template
title: ''
labels: ''
assignees: ''

---

## RHOAI Upgrade Testing Checklist

Software Versions:
- OpenShift AI: 
- OpenShift: 
- Authorino Operator:
- Serverless Operator:
- Service Mesh Operator:
- NVIDIA GPU Operator:

## Operator Health

Verify all operators are installed and their Deployments are `Available`.

- [ ] Red Hat OpenShift AI
- [ ] Node Feature Discovery (NFD)
- [ ] NVIDIA GPU Operator
- [ ] OpenShift Serverless
- [ ] OpenShift Service Mesh
- [ ] Authorino

## Configuration & Component Readiness

### Core Configurations

All configurations must be in a Ready state.

- [ ] DataScienceCluster
- [ ] GPU ClusterPolicy
- [ ] NFD Instance

### DataScienceCluster Components

All components must report `Ready = True`.

- [ ] Dashboard 
- [ ] Workbenches 
- [ ] Data Science Pipelines 
- [ ] CodeFlare 
- [ ] KServe
- [ ] Ray
- [ ] TrustyAI 
- [ ] ModelMesh Serving 
- [ ] Kueue 
- [ ] ModelRegistry 

## GPU Validation

### Node Labels

- [ ] All GPU nodes have NFD labels
  - `feature.node.kubernetes.io/pci-10de.present` **or**
  - `feature.node.kubernetes.io/pci-0302_10de.present`
- [ ] All GPU nodes have NVIDIA GPU Operator labels

### Required Pods

- [ ] NFD worker pods running  
  - Namespace: `openshift-nfd`
- [ ] NVIDIA pods running  
  - Namespace: `nvidia-gpu-operator`

## Model Serving

- [ ] Deploy a model using vLLM ServingRuntime on GPU
- [ ] Deploy a model using OpenVino ServingRuntime
- [ ] Edit model configuration after deployment
- [ ] Inference endpoint reachable
  - [ ] Without token authentication
  - [ ] With token authentication enabled
- [ ] Route validation
  - [ ] External route accessible outside cluster
  - [ ] Internal route accessible only within cluster


## Pipelines

- [ ] Import pipeline via RHOAI UI
- [ ] Import pipeline from inside a workbench
- [ ] Pipeline run validation
  - [ ] Run starts successfully
  - [ ] Run completes without errors
  - [ ] Logs viewable for each step
  - [ ] Artifacts stored correctly in S3

## Workbenches

- [ ] Launch CPU-only workbench from RHOAI UI
- [ ] Launch GPU-enabled workbench
  - [ ] GPU visible inside notebook (`nvidia-smi`)
- [ ] Edit workbench after deployment

## Connections & Storage

- [ ] Create S3 connection in a Data Science Project
- [ ] Attach S3 connection to a workbench
- [ ] Deploy model using S3-backed storage
- [ ] PVCs provision correctly for workbenches

## Authentication & Authorization

- [ ] RHOAI Dashboard accessible via OpenShift OAuth
- [ ] RBAC behaves correctly
  - [ ] Admin user permissions
  - [ ] Regular user permissions

## Networking

- [ ] Service Mesh (Istio) control plane healthy

## Monitoring & Observability

- [ ] GPU metrics available (DCGM exporter)
