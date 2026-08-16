---
title: Environment promotion using Kargo and Gitops
subtitle:
categories: [automation, containers]
---

![Kargo project promotion flow](/assets/img/24-kargo-ui.png)

## Intent

Manage Kubernetes manifests across different environments using GitOps.

## Kargo

Kargo is a promotion orchestration layer that complements Argo CD.

It runs as a Kubernetes controller and follows GitOps principles. It aims to
simplify the promotion of applications defined using Helm charts, raw
Kubernetes manifests, or Kustomize, while making promotions trackable and
reversible.

Kargo uses several concepts specific to the tool, which we will cover in the
sections below:

- Projects
- Warehouse
- Freight
- Stages

## Projects

A project is represented as a Kubernetes Project resource and contains all the
Kargo resources associated with it, including Warehouses, Freight, Stages, and
credentials.

## Warehouse

A Warehouse watches for and discovers various types of artifact sources,
including:

- Container image repositories
- Git repositories
- Helm chart repositories


## Freight
A single "piece of freight" is a set of references to one or more versioned
artifacts discovered by a Warehouse. These artifacts may include:

- Container images (from image repositories)
- Kubernetes manifests (from Git repositories)
- Helm charts (from chart repositories)


## Stages

Stages represent the different environments for a given project, such as test,
staging, and production.


## In practice

This [repository](https://github.com/ptran32/kargo-demo) was used to test Kargo.

Before trying the example, follow the [official quickstart
instructions](https://docs.kargo.io/quickstart) to deploy Kargo in your local
environment.


## What I want to explore next

Explore deeper integration with RBAC and identity management (SSO).

## Conclusion

Kargo is a solid tool; however, it introduces:

- Another infrastructure layer with its own terminology and mechanisms for a
  team to learn.
- Some interesting features are available only in the Enterprise plan, such as
  infrastructure-aware promotion of Terraform code, notifications, custom
  promotion steps and automatic rollbacks.
- I am not a fan of having a tool commit back to GitHub because it introduces a
  security risk. Kargo needs a GitHub PAT or a deployment key with write access
  to commit to the repository.
- A Kargo commit could accidentally trigger downstream CI/CD pipelines.
