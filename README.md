# CNT371S: 3-Node High-Availability K3s Kubernetes Cluster on AWS

## Student Details
* **Student Name:** Jabu Mnguni
* **Student Number:** 221258639
* **Institution:** Cape Peninsula University of Technology (CPUT)
* **Module:** Communication Networks Theory 3 (CMT371S)
* **Submission Deadline:** 30 October 2026

---

## Architecture Overview
- AWS EC2 `t3.large` instances running Ubuntu 22.04 LTS.
- `k3s-master-1` (172.31.42.150): API Server Initializer & etcd bootstrap node.
- `k3s-master-2` & `k3s-master-3`: Control plane and worker nodes with shared etcd quorum.

---

## 1. Project Overview
This repository contains configuration manifests, troubleshooting documentation, and deployment guides for a 3-node High-Availability (HA) K3s Kubernetes cluster on AWS using embedded etcd.

---

## 2. Infrastructure Specifications
* **Cloud Provider:** AWS EC2 (`t3.large`)
* **Operating System:** Ubuntu 22.04 LTS
* **Kubernetes Distribution:** K3s with embedded `etcd`
* **Shared Cluster Token:** `1199add3f31b06e85d332dbc322cf8858bae67986e6dfd2d23a38a8d1b84e484`

---

## 3. Step-by-Step Deployment Guide

### Step 1: Initialize Master 1 (`k3s-master-1`)
```bash
curl -sfL [https://get.k3s.io](https://get.k3s.io) | K3S_TOKEN="1199add3f31b06e85d332dbc322cf8858bae67986e6dfd2d23a38a8d1b84e484" sh -s - server --cluster-init --node-ip=172.31.42.150 --tls-san=172.31.42.150
