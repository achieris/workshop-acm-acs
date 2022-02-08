# Red Hat Advanced Cluster Management and OpenShift GitOps

An effective way to manage OpenShift Gitops instances and infrastructure configuration policies with RHACM.

## Why this approach is worth considering
This repo is designed to enhance GitOps approach leveraged by OpenShift GitOps
in a multi-cluster environment.

## How to use this repository
This is a boilerplate repository to quickly set up the initial resources. \
It provides:
  * Folder-based structure model
  * RHACM objects 
  * OpenShift GitOps example objects

## How to use Kustomize
This repo extensively uses [Kustomize](https://kustomize.io/) to patch resources to be applied to different environments.
Kustomize is a template-free solution for customizing Kubernetes resources based on the declarative patching of original YAML files.
The base files are located in **base** folders while their customizations can be defined inside **overlay** folders where users
can define multiple target environments and differenet customization behaviors, declared in a `kustomization.yaml` file.

For more informations about Kustomize, please refer to the following [guide](https://kubectl.docs.kubernetes.io/guides/introduction/kustomize/).

## Repository structure model
This is a GitOps folder-based structure model.

* [_rhacm-manifests_](rhacm-manifests): contains Red Hat Advanced Cluster Management manifests.
* [_gitops-manifests_](gitops-manifests): contains Argo CD resources, such as AppProjects, Applications and ApplicationSets.

### Why folder-based strategy and not branched-based
The folder-based approach has the following main advantages:
* The main branch is the Single Point of Truth for data
* Follows Git standard workflows
* Increase collaboration and the whole team enablement
* Avoids _independent_ branches proliferation
* Reduces time during troubleshooting

## Prerequisites
To use this repo you need to have in your enviroment:
* RHACM MultiClusterHub installed on an OpenShift Cluster and the openshift-gitops namespace created on the cluster.
* At least one OpenShift Cluster on which to install OpenShift Gitops operator.

## How to deploy resources on RHACM Hub
* Login into RHACM Hub cluster.
* Deploy this repository on RHACM:
  ```
  clone repository
  navigate to root folder 
  oc new-project openshift-gitops
  oc apply -k ./rhacm-manifests/overlays/your-env/
  ```

  This will create the following resources:
  * Channel for this repo
  * PlacementRules
  * Subscription for Argo CD resources (i.e. AppProjects, Applications, ApplicationSets)
  * ArgoCD Application
  * Channel namespaces
  * Policy for: 
    * OpenShift GitOps Operator installation, needed cluster role binding and namespace openshift-gitops creation;
    * Compliance checks on namespaces. 
