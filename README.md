# manifests
[![Build Status](https://travis-ci.org/phillebaba/manifests.svg?branch=master)](https://travis-ci.org/phillebaba/manifests)

This repository contains a collection of Kubernetes manifests meant to be used with [kustomize](https://kustomize.io/) as remote targets.

The purpose of this project is to mimic the function that [helm charts stable](https://github.com/helm/charts/tree/master/stable) fills. Gathering manifests for popular applications in a central location, the difference being that these manifests are stripped down and meant to be kustomized when used. This is totally opposite to how Helm works, as it tries to offer a parameter for every possible use case, creating in some cases large complex charts that have to deal with many requirements. On the other hand this solution will require a lot more knowledge into how each application works and the manifests it requires, some of this complexity can be solved with overlays but they should be kept as generic as possible to avoid accumulating large amounts of overlays.

## Design Principles
Ingress resoureces are left out on purpose. This is due to two major reasons, the first being that they will never match anyones use case as everyone will have their own domain name for the ingress. This means that every one who uses the manifest needs to patch the ingress and change the host parameter. The second reason is because a lot of ingress controllers use their own CRD to implement ingress. Different implementations have created their own ingress resource to fit their needs, meaning that their is no one size fits all for this. It is currently not possible to kustomize and remove a resource from the base, so it is better to leave the ingress out.

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
