# GitOps - Manage K8s resources via git

This repository holds all definitions to operate the Kubernetes cluster hosted in TBZ in a GitOps way.

## GitOps How?

The GitOps process in this repository is powered by ArgoCD. ArgoCD allows you to compare the defined resources in git with those in the Kubernetes cluster, ensuring that the single source of truth is in git.

![gitops](images/gitops.png)

This means that the git repositories for the source code and the Kubernetes definitions can be separated. This allows for a clear separation of duties. The repository for the application has its own CI/CD pipeline and stops at publishing an Open Container Image (OCI). The repository for Kubernetes starts with this OCI and deploys it onto the cluster using ArgoCD.

ArgoCD is kept up to date with `dependabot`, which opens a pull request when a new version is available. The owner of the service can then merge the pull request to deploy the new version. After the merge ArgoCD will update the cluster to keep in sync with the git definitions.

## Contents & Applications

The following applications and definitions can be found in this repository:

| Application Name | Namespace   | Description                                                                                               |
| ---------------- | ----------- | --------------------------------------------------------------------------------------------------------- |
| myblog-yaml      | myblog-yaml | Sample blog application, forked at [devops_blog](https://github.com/Cloud-native-engineering/devops_blog) |
|  |
| another-app      | default     | Another example application                                                                               |

## Deployment instructions

An ArgoCD application can be created using the UI or more easily with the following CLI command:

```sh
 argocd app create myblog-yaml --repo https://github.com/Cloud-native-engineering/gitops_k8s_maas.git --path myblog-yaml --dest-server https://kubernetes.default.svc --dest-namespace myblog-yaml
 ```

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the [LICENSE](LICENSE) file for details.

## Author Information

This code was created in 2024 by [Yves Wetter](mailto:yves.wetter@edu.tbz.ch).
