# kube-rsa

kube-rsa generates self-signed TLS certificates for Kubernetes.
kube-rsa does not manage TLS certificates and should only be used
for testing and basic bootstrapping.

The generated certs can be used to secure connections to the
Kubernetes API server and generate service account tokens.

kube-rsa should not be used to manage client TLS certificates for
authentication. Consider using a supported
[authentication method](http://kubernetes.io/docs/admin/authentication/)
to limit access to the Kubernetes API server over a secure connection.

## Usage

The following command will generate TLS certificates for serving
secure connections from the Kubernetes API server and managing
Kubernetes service account tokens.

```
$ kube-rsa --host=104.197.228.232,10.240.0.3
```

``` 
wrote ca.pem
wrote ca-key.pem
wrote apiserver.pem
wrote apiserver-key.pem
wrote service-account.pem
wrote service-account-key.pem
```

The first host entry set via the `--host` flag will be used as the
CN, otherwise the CN will be set to 127.0.0.1.

## Kubernetes Configuration Guide

### Kubernetes API Server

```
--service-account-key-file="service-account.pem"
--tls-cert-file="apiserver.pem"
--tls-private-key-file="apiserver-key.pem"
```

### Kubernetes Controller Manager

```
--service-account-private-key-file="service-account-key.pem"
```
