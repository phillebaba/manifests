# manifests
This repository contains a collection of Kubernetes manifests meant to be used with [kustomize](https://kustomize.io/) as remote targets.

The purpose of this project is to mimic the function that [helm charts stable](https://github.com/helm/charts/tree/master/stable) fills. Gathering manifests for popular applications in a central location, the difference being that these manifests are stripped down and meant to be kustomized when used. This is totally opposite to how Helm works, as it tries to offer a parameter for every possible use case, creating in some cases large complex charts that have to deal with many requirements. On the other hand this solution will require a lot more knowledge into how each application works and the manifests it requires, some of this complexity can be solved with overlays but they should be kept as generic as possible to avoid accumulating large amounts of overlays.

## Usage
Using an application base is easy, simply reference it as a remote target and apply your own kustomization.
```yml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
bases:
  - github.com/phillebaba/manifests//traefik/base
nameSuffix: -private
```

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
