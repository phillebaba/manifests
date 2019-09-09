# external-dns
Configure external DNS servers (AWS Route53, Google CloudDNS and others) for Kubernetes Ingresses and Services

[Base manifest](https://github.com/kubernetes-incubator/external-dns/tree/master/docs/tutorials)

## RFC2136
[Docs](https://github.com/kubernetes-incubator/external-dns/blob/master/docs/tutorials/rfc2136.md)

An additional secret is required for this manifest to work properly. This is to configure the tsig credentials.
```
apiVersion: v1
kind: Secret
metadata:
  name: external-dns
type: Opaque
stringData:
  rfc2136_tsig_keyname: "rndc-key"
  rfc2136_tsig_secret: "secret"
```
