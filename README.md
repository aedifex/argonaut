# 📌 Argonaut --- GitOps Manifests

A **GitOps‑centric repository of Kubernetes manifests** designed to
demonstrate declarative application delivery using **Argo CD**, with a
view toward importing and managing these deployments via **Harness
GitOps** --- the enterprise GitOps control plane that unifies and
governs Argo CD deployments at scale.

------------------------------------------------------------------------

## 🧭 Purpose

This repository exists to:

-   Demonstrate GitOps reconciliation using Argo CD
-   Externalize runtime configuration via Kubernetes ConfigMaps
-   Enable deterministic application version changes without rebuilding
    images
-   Establish a foundation for seamless import into Harness GitOps

The focus is clarity, determinism, and alignment with enterprise GitOps
patterns.

------------------------------------------------------------------------

## 🏗 Architecture Overview

Git (Argonaut repo)\
↓\
Argo CD (reconciliation engine)\
↓\
Kubernetes (Minikube)\
↓\
Running Application (ECR-backed container)

Git defines the desired state.\
Argo CD continuously reconciles cluster state to match Git.\
Runtime configuration is injected declaratively.

------------------------------------------------------------------------

## 🔄 GitOps Flow Demonstrated

1.  Modify configuration in Git (e.g., update BUILD_ID or deploy
    message)
2.  Commit and push changes
3.  Argo CD detects drift (OutOfSync)
4.  Sync application
5.  Pod restarts with updated runtime configuration
6.  Application metadata endpoint reflects the new state

No image rebuild required.

------------------------------------------------------------------------

## 🔐 Container Registry

-   Application image hosted in private AWS ECR
-   Kubernetes configured with imagePullSecret for ECR authentication
-   Designed to evolve toward IRSA-based auth in EKS environments

------------------------------------------------------------------------

## 📦 Stack

-   Kubernetes (Minikube for local sandbox)
-   Argo CD (vanilla install)
-   AWS ECR
-   ConfigMap-driven runtime configuration
-   Designed for Harness GitOps import and governance

------------------------------------------------------------------------

## 🚀 Forward Path

This repository is structured to support:

-   Import into Harness GitOps
-   Multi-environment overlays (dev / staging / prod)
-   Promotion workflows
-   Governance and policy enforcement at scale

------------------------------------------------------------------------

## 👤 Author

Christopher Black\
Senior Solutions Engineer\
GitOps \| Platform Engineering \| Declarative Delivery
