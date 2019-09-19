# NFS Provisioner

**IMPORTANT NOTE**
This base does not work out of the box. It requires you to configure a var for `NFS_SERVER` that the provisioner should connect to. This can either be done by configuring a var in your kustomization.

```yml
vars:
- name: NFS_SERVER
  objref:
    kind: Service
    name: nfs-server
    apiVersion: v1
  fieldref:
    fieldpath: spec.clusterIP
```
 Or by patching the manifests and overriding the parameters where the variable is used.
