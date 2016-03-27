# kube-rsa

kube-rsa is a CLI tool to generate TLS certificates for a Kubernetes cluster.

## Usage

```
$ kubecert --host=104.197.228.232,10.240.0.3
```

``` 
wrote ca.pem
wrote ca-key.pem
wrote apiserver.pem
wrote apiserver-key.pem
wrote service-account.pem
wrote service-account-key.pem
```

The first host entry will be used as the CN if set, otherwise
the CN will be set to 127.0.0.1.

```
$ openssl x509 -text -in apiserver.pem 
```

```
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            72:83:af:3c:ce:df:97:f0:a0:e8:08:dc:22:d7:1b:33
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: O=Kubernetes
        Validity
            Not Before: Mar 27 05:11:02 2016 GMT
            Not After : Mar 27 05:11:02 2017 GMT
        Subject: O=Kubernetes, CN=104.197.228.232
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
            RSA Public Key: (2048 bit)
                Modulus (2048 bit):
                    00:c3:08:8b:7b:d5:29:20:01:77:44:e7:1b:60:41:
                    74:c4:37:25:f5:b4:41:8d:43:2b:77:f6:14:d7:53:
                    01:89:06:b6:4c:e8:f3:cb:70:f1:a7:52:7a:a6:b4:
                    e6:15:57:74:a8:01:8c:33:98:f0:7a:10:db:d4:e0:
                    f8:13:56:3f:40:fb:c4:f8:00:ac:23:af:90:fd:84:
                    99:e9:fd:2b:9f:7f:ea:1c:cd:e9:28:d9:55:14:d1:
                    16:f9:02:32:4e:eb:46:7d:bf:30:3e:fd:58:33:82:
                    e3:1f:f6:2f:01:a9:19:13:c1:66:5e:95:92:9b:f0:
                    88:26:76:8c:1b:ed:bb:e6:74:7a:86:9a:06:e4:f8:
                    59:57:16:21:e7:42:d4:54:85:8b:e9:f0:23:97:df:
                    ae:e8:e8:9d:d5:b5:b3:6c:1c:69:07:5d:f1:32:76:
                    a3:d3:90:dc:48:f1:81:8f:68:3b:48:c8:00:50:45:
                    d7:d5:0d:e0:de:58:f8:db:90:c7:8a:20:fc:54:68:
                    5e:b3:6b:a6:51:63:b5:ef:06:c9:21:21:9c:9b:c5:
                    35:3f:64:78:6d:c1:7f:3a:ed:60:0a:35:22:5d:91:
                    39:3e:2b:a4:1f:9a:66:6b:d4:c0:40:66:1b:af:d6:
                    bd:71:ff:5f:18:47:26:4d:e8:25:5d:4a:fb:98:04:
                    71:55
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Key Usage: critical
                Digital Signature, Key Encipherment
            X509v3 Extended Key Usage: 
                TLS Web Server Authentication
            X509v3 Basic Constraints: critical
                CA:FALSE
            X509v3 Subject Alternative Name: 
                DNS:localhost, DNS:kubernetes, DNS:kubernetes.default, DNS:kubernetes.default.svc, IP Address:104.197.228.232, IP Address:10.240.0.3, IP Address:127.0.0.1
    Signature Algorithm: sha256WithRSAEncryption
        09:04:68:74:0c:53:4a:07:8a:b6:60:c1:30:a1:35:41:23:f3:
        e1:a8:30:2b:e0:62:2a:c8:d1:5b:d7:ee:b3:76:b7:e6:39:94:
        cc:8d:f7:3a:9f:a4:ba:57:02:e2:2b:75:91:f7:af:69:3c:02:
        01:ee:48:1b:f8:ba:e1:e5:36:03:39:c2:00:ef:cf:84:32:17:
        e6:2d:28:ee:96:69:f7:c8:99:4c:78:3e:45:b6:18:56:d9:81:
        54:b1:c3:9f:e0:2a:89:13:1e:0a:0b:1c:69:8d:f9:27:e6:24:
        ff:f6:06:77:f2:3b:0f:9f:61:ca:a6:03:60:34:90:09:cb:e1:
        7c:cc:70:0d:5c:27:94:26:ae:15:ce:5d:a4:df:b6:77:b6:30:
        88:69:f2:06:ae:05:6c:5d:b3:8d:20:a2:3d:9b:d0:e1:e3:f3:
        a0:77:b0:5a:22:af:3f:53:a4:81:80:02:4c:a8:10:8e:c0:9b:
        0c:59:be:41:23:1a:47:ad:38:c2:1b:27:3e:f1:69:79:e3:1f:
        ce:f6:8d:80:b9:ff:61:d0:af:c5:b5:09:79:12:5c:0d:d8:d9:
        90:e4:2a:e7:44:8c:0f:0e:10:79:d2:ec:93:94:13:a2:b6:c5:
        75:0a:43:61:87:1a:1e:0c:81:b6:f0:1d:84:96:74:c3:33:91:
        73:62:1c:91
-----BEGIN CERTIFICATE-----
MIIDZTCCAk2gAwIBAgIQcoOvPM7fl/Cg6AjcItcbMzANBgkqhkiG9w0BAQsFADAV
MRMwEQYDVQQKEwpLdWJlcm5ldGVzMB4XDTE2MDMyNzA1MTEwMloXDTE3MDMyNzA1
MTEwMlowLzETMBEGA1UEChMKS3ViZXJuZXRlczEYMBYGA1UEAxMPMTA0LjE5Ny4y
MjguMjMyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAwwiLe9UpIAF3
ROcbYEF0xDcl9bRBjUMrd/YU11MBiQa2TOjzy3Dxp1J6prTmFVd0qAGMM5jwehDb
1OD4E1Y/QPvE+ACsI6+Q/YSZ6f0rn3/qHM3pKNlVFNEW+QIyTutGfb8wPv1YM4Lj
H/YvAakZE8FmXpWSm/CIJnaMG+275nR6hpoG5PhZVxYh50LUVIWL6fAjl9+u6Oid
1bWzbBxpB13xMnaj05DcSPGBj2g7SMgAUEXX1Q3g3lj425DHiiD8VGhes2umUWO1
7wbJISGcm8U1P2R4bcF/Ou1gCjUiXZE5PiukH5pma9TAQGYbr9a9cf9fGEcmTegl
XUr7mARxVQIDAQABo4GWMIGTMA4GA1UdDwEB/wQEAwIFoDATBgNVHSUEDDAKBggr
BgEFBQcDATAMBgNVHRMBAf8EAjAAMF4GA1UdEQRXMFWCCWxvY2FsaG9zdIIKa3Vi
ZXJuZXRlc4ISa3ViZXJuZXRlcy5kZWZhdWx0ghZrdWJlcm5ldGVzLmRlZmF1bHQu
c3ZjhwRoxeTohwQK8AADhwR/AAABMA0GCSqGSIb3DQEBCwUAA4IBAQAJBGh0DFNK
B4q2YMEwoTVBI/PhqDAr4GIqyNFb1+6zdrfmOZTMjfc6n6S6VwLiK3WR969pPAIB
7kgb+Lrh5TYDOcIA78+EMhfmLSjulmn3yJlMeD5FthhW2YFUscOf4CqJEx4KCxxp
jfkn5iT/9gZ38jsPn2HKpgNgNJAJy+F8zHANXCeUJq4Vzl2k37Z3tjCIafIGrgVs
XbONIKI9m9Dh4/Ogd7BaIq8/U6SBgAJMqBCOwJsMWb5BIxpHrTjCGyc+8Wl54x/O
9o2Auf9h0K/FtQl5ElwN2NmQ5CrnRIwPDhB50uyTlBOitsV1CkNhhxoeDIG28B2E
lnTDM5FzYhyR
-----END CERTIFICATE-----
```
