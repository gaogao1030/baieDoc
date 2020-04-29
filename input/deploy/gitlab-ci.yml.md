## .gitlab-ci.yml
```
include:
  - project: gaogao1030/Kubernetes
    file: /k8s-ci-templates/react/base.yaml
  - project: gaogao1030/Kubernetes
    file: /k8s-ci-templates/react/default.yaml
  - project: gaogao1030/Kubernetes
    file: /k8s-ci-templates/react/build_image.yaml
  - project: gaogao1030/Kubernetes
    file: /k8s-ci-templates/react/review.yaml
  - project: gaogao1030/Kubernetes
    file: /k8s-ci-templates/react/local.yaml
```
