# OpenShift GitOps Argo CD Resources

## Overlays structure
Each folder is meant to be an overlay which collects all the resources
defined on a specific OpenShift GitOps instance.

Below a few structure examples.

* `<cluster>-<env>`
  ```
  .
  ├── ocp-lab-charlie
  │   ├── kustomization.yaml
  │   └── projects
  │       ├── dev
  │       │   ├── appproject.yaml
  │       │   ├── apps
  │       │   └── appsets
  │       └── sit
  │           ├── appproject.yaml
  │           ├── apps
  │           └── appsets
  ├── ocp-lab-mike
      ├── kustomization.yaml
      └── projects
          ├── prod
          │   ├── appproject.yaml
          │   ├── apps
          │   └── appsets
          └── uat
              ├── appproject.yaml
              ├── apps
              └── appsets
   
  ```
* `<env>`
  ```
  $ mkdir -p {prod,stage}/projects/{default,myproject}/{app,appset}
  $ touch {prod,stage}/kustomization.yaml
  $ tree
  .
  ├── prod
  │   ├── kustomization.yaml
  │   └── projects
  │       ├── default
  |       │   ├── kustomization.yaml
  │       │   ├── app
  │       │   └── appset
  │       └── myproject
  |           ├── kustomization.yaml
  |           ├── app-project-myproject.yaml
  │           ├── app
  │           └── appset
  └── stage
      ├── kustomization.yaml
      └── projects
          ├── default
          │   ├── kustomization.yaml
          │   ├── app
          │   └── appset
          └── myproject
              ├── kustomization.yaml
              ├── app-project-myproject.yaml
              ├── app
              └── appset
  ```

* `<platform>`
  ```
  $ mkdir -p {azure,gcp}/projects/{default,myproject}/{app,appset}
  $ touch {azure,gcp}/kustomization.yaml
  $ tree
  .
  ├── azure
  │   ├── kustomization.yaml
  │   └── projects
  │       ├── default
  |       |   ├── kustomization.yaml
  │       │   ├── app
  │       │   └── appset
  │       └── myproject
  |           ├── kustomization.yaml
  |           ├── app-project-myproject.yaml
  │           ├── app
  │           └── appset
  └── gcp
      ├── kustomization.yaml
      └── projects
          ├── default
          |   ├── kustomization.yaml
          │   ├── app
          │   └── appset
          └── myproject
              ├── kustomization.yaml
              ├── app-project-myproject.yaml
              ├── app
              └── appset
  ```

* `<env>-<platform>`
  ```
  $ mkdir -p {prod,stage}-{azure,gcp}/projects/{default,myproject}/{app,appset}
  $ touch {prod,stage}-{azure,gcp}/kustomization.yaml
  $ tree
  .
  ├── prod-azure
  │   ├── kustomization.yaml
  │   └── projects
  │       ├── default
  |       |   ├── kustomization.yaml
  │       │   ├── app
  │       │   └── appset
  │       └── myproject
  |           ├── kustomization.yaml
  |           ├── app-project-myproject.yaml
  │           ├── app
  │           └── appset
  ├── prod-gcp
  │   ├── kustomization.yaml
  │   └── projects
  │       ├── default
  |       |   ├── kustomization.yaml
  │       │   ├── app
  │       │   └── appset
  │       └── myproject
  |           ├── kustomization.yaml
  |           ├── app-project-myproject.yaml
  │           ├── app
  │           └── appset
  ├── stage-azure
  │   ├── kustomization.yaml
  │   └── projects
  │       ├── default
  |       |   ├── kustomization.yaml
  │       │   ├── app
  │       │   └── appset
  │       └── myproject
  |           ├── kustomization.yaml
  |           ├── app-project-myproject.yaml
  │           ├── app
  │           └── appset
  └── stage-gcp
      ├── kustomization.yaml
      └── projects
          ├── default
          |   ├── kustomization.yaml
          │   ├── app
          │   └── appset
          └── myproject
              ├── kustomization.yaml
              ├── app-project-myproject.yaml
              ├── app
              └── appset
  ```
