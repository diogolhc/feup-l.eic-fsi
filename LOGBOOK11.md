# Trabalho realizado na Semana #11

## Tarefa 1

Inicialmente, criou-se a estrutura de pastas e ficheiros necessários para a construção da autoridade certificada (demoCA, certs, crl, index, newcerts e serial). Seguidamente, correu-se o comando para a criação da CA.
Para testar a geração, usaram-se os comandos ```openssl x509 -in ca.crt -text -noout``` e ```openssl rsa -in ca.key -text -noout``` verifiicando o certificado e a chave criados para a autoridade de certificação. Obtiveram-se respetivamente os seguintes *outputs*

```
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            27:0e:62:2e:a1:bf:34:fe:d8:70:9e:76:4b:1b:e9:41:a7:04:e3:7f
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C = PT, ST = Portugal, L = Porto, O = FEUP, OU = FEUP, CN = fsi2162, emailAddress = fsi2162@fe.up.pt
        Validity
            Not Before: Jan 18 20:29:31 2022 GMT
            Not After : Jan 16 20:29:31 2032 GMT
        Subject: C = PT, ST = Portugal, L = Porto, O = FEUP, OU = FEUP, CN = fsi2162, emailAddress = fsi2162@fe.up.pt
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (4096 bit)
                Modulus:
                    00:c1:b1:d8:17:88:02:89:b1:ea:9d:e4:cd:6c:bf:
                    39:61:de:59:11:b8:90:14:83:d8:25:df:2c:ed:b9:
                    eb:ce:da:0d:37:8c:af:a3:72:9a:bf:41:cf:92:49:
                    ef:14:3c:2c:a3:cb:08:30:84:9e:13:73:4b:f1:45:
                    5b:8a:13:26:e6:ef:6a:3a:3c:02:57:33:37:c3:d0:
                    83:ca:5e:ec:8c:a5:b6:e4:36:3c:07:57:f0:21:4e:
                    88:04:80:30:6a:bb:9c:80:f3:55:ee:11:fd:ee:19:
                    52:23:80:dd:5b:79:e8:33:a8:5a:09:c7:e0:c3:77:
                    4f:43:0a:17:f0:eb:48:33:b9:33:d1:f0:1f:f7:67:
                    44:1d:e7:e0:d5:30:88:c4:4b:0c:91:a2:b8:e4:7b:
                    0c:fe:c1:e9:9e:07:e0:70:b7:4e:8e:bb:7a:b3:26:
                    46:20:b5:e3:9d:04:7e:5b:3b:5f:da:be:c3:86:10:
                    a7:2b:c1:f0:76:84:05:d0:de:2e:9d:fd:9c:c6:4b:
                    d8:ab:4c:2c:31:94:d1:00:6c:e5:c1:4b:f8:aa:4b:
                    5c:9f:dc:17:63:0e:03:cb:89:05:20:8f:28:93:2c:
                    52:0d:d1:97:43:cf:34:40:f6:b3:4a:8e:7d:25:44:
                    cb:f5:94:69:2c:96:4a:ac:10:97:aa:f5:5b:b0:83:
                    a2:fc:d5:cf:f5:96:64:41:f6:d0:b0:29:61:0c:68:
                    7d:82:29:e0:e2:4a:d0:a5:e6:fc:00:a0:84:9f:6d:
                    f5:04:d7:f5:9b:2f:91:9e:9d:40:a9:98:b9:2c:be:
                    36:36:2c:7a:da:9a:82:4f:c7:3b:66:ff:93:a9:7c:
                    0e:7d:dd:4e:20:93:e1:d9:79:a2:b5:86:23:8f:c0:
                    a5:ec:dd:77:ec:71:11:24:35:e2:40:20:25:fd:60:
                    5b:cd:7c:1e:c1:1a:68:52:95:77:47:8d:31:d3:1c:
                    ff:ca:05:66:df:1a:fc:7d:5c:43:55:ac:72:97:be:
                    ac:9d:c8:fc:e0:d5:8e:b5:c1:3a:f6:a8:77:a3:99:
                    7a:d9:95:70:9b:a2:83:56:68:fe:d2:94:3b:0e:2e:
                    26:4d:47:19:d8:f6:1a:9e:33:1c:f8:60:02:3e:3d:
                    78:7c:3b:9b:ad:83:cc:f3:9a:e4:86:51:6c:05:6f:
                    e0:9a:ae:1b:70:33:a7:1a:ef:cc:b5:fd:38:b0:58:
                    49:ea:7a:f2:bf:c0:0e:69:eb:9b:66:4b:ec:d4:4d:
                    27:ec:6f:29:25:67:6c:fd:22:79:2e:47:66:84:c3:
                    9b:2b:f4:b4:92:10:1e:d2:93:be:b3:c1:ad:c3:5f:
                    97:5e:cd:af:f8:00:07:49:5f:7a:5f:be:d2:2c:f1:
                    5f:b9:09
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Key Identifier: 
                9C:57:57:70:CB:B8:02:E8:E0:5D:C5:5E:49:F5:CD:DC:97:19:7F:5A
            X509v3 Authority Key Identifier: 
                keyid:9C:57:57:70:CB:B8:02:E8:E0:5D:C5:5E:49:F5:CD:DC:97:19:7F:5A

            X509v3 Basic Constraints: critical
                CA:TRUE
    Signature Algorithm: sha256WithRSAEncryption
         4d:66:10:ae:b8:f4:2e:aa:41:0d:94:f7:10:81:a7:92:e3:1a:
         e1:b2:08:e4:bb:d0:ed:95:78:b1:3e:20:40:47:1a:54:9a:3b:
         bd:5c:fa:64:fd:cc:f2:6f:86:95:7f:a0:df:81:a5:f5:a3:1c:
         7d:0d:4f:08:65:a0:24:2d:8b:f4:2a:c1:8c:ab:16:da:ca:9d:
         cc:54:6f:ce:37:a0:f6:59:bc:1e:0d:3b:f5:4e:47:cc:32:9a:
         da:2c:fe:d5:46:34:81:dc:45:4b:4b:82:54:01:e4:90:66:30:
         5d:88:38:fd:18:f3:d1:3b:eb:35:93:9a:39:8e:3c:17:38:72:
         5d:59:7a:5f:9e:6d:0d:5e:94:55:f7:c1:dc:3e:84:9a:5d:be:
         89:6b:6d:9a:f7:47:91:cc:5d:02:be:f8:e5:ea:17:5b:57:ad:
         db:af:31:ea:fe:10:67:24:6a:03:f0:b5:5b:5b:7b:82:57:e5:
         d3:99:ca:08:d2:21:da:88:c4:fc:54:25:27:44:85:a1:af:ac:
         51:41:2e:08:80:3f:78:2a:a2:a2:d9:ad:8f:26:24:17:41:c7:
         d5:69:b8:94:ab:07:a3:b3:25:b9:a9:9c:74:bb:eb:59:fa:c9:
         a6:95:d1:33:4c:1c:d7:2c:36:16:2f:68:94:d6:bb:0d:9c:a1:
         b6:84:cd:8e:b6:72:8b:dc:3b:83:ee:d4:fa:f9:25:61:6c:36:
         eb:a6:dc:3a:5e:80:06:c3:94:22:29:25:fc:2a:65:15:2a:d4:
         54:6e:cf:ad:93:75:86:8e:1b:92:9b:27:ca:34:40:64:ab:27:
         74:37:d9:7d:c7:45:8f:03:a1:00:d0:48:bd:30:76:fb:9f:df:
         24:44:de:f9:9c:4e:66:f9:f4:94:32:2c:30:b3:94:e3:64:72:
         4b:5f:23:89:71:80:32:63:25:36:8e:03:f6:61:1d:bd:70:57:
         7c:44:d5:91:19:94:6d:30:cc:3c:7b:ec:24:72:c1:00:6e:12:
         40:c7:9c:d6:39:81:e3:19:66:e1:af:82:6a:45:63:28:9f:68:
         59:0d:5f:31:65:21:f5:ad:0f:4f:f0:9c:82:10:fb:13:38:51:
         3e:49:24:66:1a:87:a3:a3:6d:c0:c9:1f:3a:d9:e5:a8:fa:38:
         53:18:62:c2:f9:ab:13:62:63:66:e2:e5:37:ca:e0:3d:62:45:
         cb:04:12:7f:38:03:a0:47:a5:c4:b7:af:56:1e:b1:71:18:91:
         ce:e6:09:99:68:59:27:32:cf:76:06:e8:98:9e:ca:b7:99:cd:
         a1:38:8d:a1:e1:ec:ac:c6:fb:cd:f9:2d:65:32:98:df:6a:59:
         86:49:89:1c:b6:54:44:29
```

```
RSA Private-Key: (4096 bit, 2 primes)
modulus:
    00:c1:b1:d8:17:88:02:89:b1:ea:9d:e4:cd:6c:bf:
    39:61:de:59:11:b8:90:14:83:d8:25:df:2c:ed:b9:
    eb:ce:da:0d:37:8c:af:a3:72:9a:bf:41:cf:92:49:
    ef:14:3c:2c:a3:cb:08:30:84:9e:13:73:4b:f1:45:
    5b:8a:13:26:e6:ef:6a:3a:3c:02:57:33:37:c3:d0:
    83:ca:5e:ec:8c:a5:b6:e4:36:3c:07:57:f0:21:4e:
    88:04:80:30:6a:bb:9c:80:f3:55:ee:11:fd:ee:19:
    52:23:80:dd:5b:79:e8:33:a8:5a:09:c7:e0:c3:77:
    4f:43:0a:17:f0:eb:48:33:b9:33:d1:f0:1f:f7:67:
    44:1d:e7:e0:d5:30:88:c4:4b:0c:91:a2:b8:e4:7b:
    0c:fe:c1:e9:9e:07:e0:70:b7:4e:8e:bb:7a:b3:26:
    46:20:b5:e3:9d:04:7e:5b:3b:5f:da:be:c3:86:10:
    a7:2b:c1:f0:76:84:05:d0:de:2e:9d:fd:9c:c6:4b:
    d8:ab:4c:2c:31:94:d1:00:6c:e5:c1:4b:f8:aa:4b:
    5c:9f:dc:17:63:0e:03:cb:89:05:20:8f:28:93:2c:
    52:0d:d1:97:43:cf:34:40:f6:b3:4a:8e:7d:25:44:
    cb:f5:94:69:2c:96:4a:ac:10:97:aa:f5:5b:b0:83:
    a2:fc:d5:cf:f5:96:64:41:f6:d0:b0:29:61:0c:68:
    7d:82:29:e0:e2:4a:d0:a5:e6:fc:00:a0:84:9f:6d:
    f5:04:d7:f5:9b:2f:91:9e:9d:40:a9:98:b9:2c:be:
    36:36:2c:7a:da:9a:82:4f:c7:3b:66:ff:93:a9:7c:
    0e:7d:dd:4e:20:93:e1:d9:79:a2:b5:86:23:8f:c0:
    a5:ec:dd:77:ec:71:11:24:35:e2:40:20:25:fd:60:
    5b:cd:7c:1e:c1:1a:68:52:95:77:47:8d:31:d3:1c:
    ff:ca:05:66:df:1a:fc:7d:5c:43:55:ac:72:97:be:
    ac:9d:c8:fc:e0:d5:8e:b5:c1:3a:f6:a8:77:a3:99:
    7a:d9:95:70:9b:a2:83:56:68:fe:d2:94:3b:0e:2e:
    26:4d:47:19:d8:f6:1a:9e:33:1c:f8:60:02:3e:3d:
    78:7c:3b:9b:ad:83:cc:f3:9a:e4:86:51:6c:05:6f:
    e0:9a:ae:1b:70:33:a7:1a:ef:cc:b5:fd:38:b0:58:
    49:ea:7a:f2:bf:c0:0e:69:eb:9b:66:4b:ec:d4:4d:
    27:ec:6f:29:25:67:6c:fd:22:79:2e:47:66:84:c3:
    9b:2b:f4:b4:92:10:1e:d2:93:be:b3:c1:ad:c3:5f:
    97:5e:cd:af:f8:00:07:49:5f:7a:5f:be:d2:2c:f1:
    5f:b9:09
publicExponent: 65537 (0x10001)
privateExponent:
    60:b1:f4:eb:c2:65:69:f2:1c:eb:18:07:09:6b:e9:
    2c:97:80:a5:9d:1a:a8:73:2d:5b:b2:af:4e:3a:4b:
    a3:27:2e:03:f6:42:d4:78:e9:11:e3:bb:c9:0f:09:
    c0:73:4d:e1:b3:00:f2:9f:b1:fe:89:c7:76:ba:26:
    39:a6:d7:fb:df:b7:8b:3c:db:fa:46:42:67:89:d7:
    d1:16:54:46:de:8f:90:1c:17:19:9f:67:ec:68:b4:
    f4:72:3e:39:7a:51:65:fa:94:82:56:0f:0b:67:2e:
    9f:34:bc:cc:e6:ed:e9:a3:f8:d6:fb:26:94:ce:22:
    0e:98:a2:5d:0e:48:2c:32:1f:d1:85:6b:9f:e9:b8:
    92:a9:68:8f:65:3c:51:aa:19:ab:36:ad:d0:ba:31:
    41:98:f2:94:86:e0:1f:c5:12:fd:a4:50:5b:d1:16:
    9f:4b:ce:46:5b:b0:ec:c0:96:58:b0:75:11:9f:8c:
    a5:06:9b:91:be:d4:dc:71:9e:9a:16:ba:c6:2f:a5:
    09:d6:ec:15:10:72:ca:20:93:0e:4d:6b:e5:2f:dc:
    1c:9e:16:3a:c8:0b:52:f7:a3:4c:9e:cb:25:b5:b1:
    7c:de:8e:02:37:15:a1:fc:c6:82:c8:e1:66:d2:92:
    73:95:d4:6f:82:d3:e2:54:22:33:21:6b:d5:91:d1:
    b2:40:c6:58:9c:6b:b7:9a:92:86:89:7a:ee:a4:88:
    26:52:b4:02:3c:78:e4:83:6b:51:5c:d2:b2:81:20:
    e3:c1:74:dd:0e:70:f5:9d:8c:37:be:b0:17:ba:2c:
    7c:87:93:e1:4c:1d:4d:87:47:27:92:64:8e:14:94:
    cf:ec:94:87:95:9d:53:b5:d0:bc:5e:8b:ea:70:ed:
    37:be:b8:d0:46:cc:86:2c:2f:98:fb:ea:5c:d5:63:
    2f:02:2f:96:81:7c:9d:24:b2:b3:4b:22:2f:f2:78:
    00:0d:9c:a1:27:de:2f:99:6a:2b:e2:68:e2:c9:f3:
    49:59:63:44:a9:df:32:f8:e4:d2:b9:e4:80:76:a6:
    4d:9b:18:ec:8b:0a:80:c5:10:d3:18:74:38:96:30:
    e2:e9:62:f1:e6:19:69:20:64:21:03:43:7a:67:8e:
    20:2a:4a:89:7d:0b:9e:66:3e:81:42:1e:47:54:04:
    a8:f0:0a:8b:e4:ae:42:e3:9d:ce:4b:5c:62:0e:10:
    9b:24:b3:b6:eb:b5:7b:9c:fc:dd:81:5b:3e:34:14:
    bf:85:54:7e:17:5b:50:09:58:43:ef:7f:ca:ed:24:
    81:45:4f:99:19:d4:5c:d2:ff:6a:f2:0f:57:73:4b:
    ee:d7:9c:8f:4a:7b:57:39:72:de:75:64:51:5b:a1:
    68:81
prime1:
    00:fc:46:5b:1a:0a:53:fe:68:70:16:90:52:2f:fc:
    bf:51:c3:4d:2f:72:83:4c:f5:82:cd:fa:6c:43:b1:
    27:fa:db:6a:c0:3d:dc:64:95:b7:7e:f9:9d:0d:00:
    6c:88:aa:15:4e:50:56:95:15:28:a9:41:ce:ce:c8:
    85:b4:13:ba:eb:b6:8d:58:4b:fa:ed:eb:fb:60:d2:
    0a:8c:fa:0e:13:af:87:08:d9:86:7d:58:83:fd:c1:
    4a:4a:71:46:cf:63:14:5f:37:2f:a5:8d:55:34:6f:
    fe:75:2c:32:d7:bf:d0:ce:7f:d7:78:3e:19:44:ce:
    c3:88:a7:7b:6e:b7:c4:3a:9b:6e:bf:83:0e:51:17:
    14:12:cf:93:75:47:9d:6a:bd:d6:4c:4c:1f:bc:89:
    e1:d8:c4:ea:a9:2e:54:d9:19:c7:9c:a4:7a:c1:4f:
    57:38:a1:e9:74:cd:da:ed:12:0c:3c:a6:00:e5:d4:
    c0:3d:39:d7:ea:69:e2:70:ef:95:06:a0:8d:4d:89:
    f5:f2:cf:1f:2a:52:47:07:44:29:6f:28:4c:06:d5:
    1e:82:5c:53:42:48:3f:c4:d6:8c:34:9f:27:3a:49:
    ae:8b:c2:90:bb:f3:26:d7:69:48:52:5c:d9:66:17:
    0e:2f:14:23:e1:b4:1c:20:bb:16:1a:46:71:91:ee:
    9c:71
prime2:
    00:c4:8e:0b:7b:d7:11:c8:18:be:2d:0c:3d:af:f4:
    c5:5b:69:3b:5e:a6:af:89:8e:44:5b:5c:98:56:ec:
    de:6f:09:18:99:38:6b:36:fc:9c:0d:a7:11:1a:3d:
    35:30:8a:05:5b:ba:f6:7d:e9:10:42:dd:d9:82:89:
    27:eb:78:e2:39:83:62:93:ff:85:7a:7d:2a:1f:cf:
    0f:0c:6f:a2:b2:61:e1:56:c5:d0:a2:f0:d5:f9:fe:
    cc:5c:17:2f:06:e1:da:da:09:aa:3c:47:40:98:d2:
    20:f3:06:ac:02:24:0d:cf:50:11:9d:c7:04:75:93:
    fe:39:51:5d:b1:7c:f5:fc:36:ca:f0:3b:06:a3:40:
    70:ec:20:01:7c:a3:44:a0:c0:8a:c8:27:62:db:2b:
    88:3f:44:77:2b:5e:4c:53:98:1f:4b:9f:12:2b:71:
    ec:91:a7:35:9b:12:b1:99:06:61:c1:d5:e5:f9:46:
    31:c6:46:a6:ae:85:44:0f:b7:74:21:65:d6:2b:39:
    92:92:7e:09:5c:a2:94:10:7d:df:45:08:94:44:74:
    28:02:89:74:76:1e:31:f8:c7:d8:56:df:0a:1e:35:
    f3:9c:68:c5:d3:9b:84:fe:2d:2b:82:e4:23:9d:30:
    c4:a5:bf:de:ac:72:8a:54:41:ab:c7:1f:f4:ee:7a:
    92:19
exponent1:
    1c:7f:2a:0d:4f:fb:5a:f2:9b:2e:c1:50:b7:60:fa:
    8f:96:db:22:2f:f2:4b:00:34:ad:65:cb:52:fe:31:
    00:f2:46:25:bf:17:25:39:90:47:c4:94:8c:02:6f:
    40:24:ce:51:51:5b:e6:6d:44:71:92:20:75:55:4b:
    5d:23:19:6b:44:ec:c4:7b:98:b5:c5:81:58:d7:81:
    1f:99:a3:7b:6f:c9:76:23:74:40:b6:7d:fa:6d:1a:
    22:3c:97:7e:17:b8:16:65:5a:79:7d:f4:90:fe:d1:
    a4:94:c0:8d:84:7a:66:c9:24:22:ce:08:f6:af:d0:
    80:a0:42:9e:28:1d:ff:6c:cd:5e:ce:c4:10:3e:e6:
    22:95:d6:17:5a:66:9a:c7:24:ec:eb:70:6e:50:b8:
    f5:4e:91:1f:59:3f:76:62:a6:1c:b8:ab:b1:28:70:
    36:d2:7b:57:99:65:50:80:48:67:95:6c:e6:89:58:
    c9:d1:bd:e5:19:de:dd:59:02:e1:83:c3:52:6d:f2:
    1d:62:6e:27:ce:b1:7d:4d:a2:cc:8e:a5:bf:e3:d5:
    15:6e:ae:6c:ff:52:4c:be:db:89:9a:2c:c9:35:c7:
    84:bc:0e:b3:5c:6d:17:ca:29:c4:3b:fe:c6:bc:75:
    fa:b5:70:b4:2f:2f:3a:37:47:f0:e1:e2:34:54:da:
    d1
exponent2:
    00:86:40:ef:9f:1a:fb:ce:4c:f8:39:14:cf:5d:cc:
    36:b1:85:63:43:f7:5e:96:fa:51:be:85:b4:98:4b:
    1a:73:85:27:04:21:01:3a:81:b8:a5:aa:a3:87:e4:
    9e:dc:14:aa:2c:49:bb:eb:ac:b1:aa:ba:95:c3:0f:
    a3:f0:b6:94:ee:eb:ca:fd:83:de:cc:17:8a:1a:47:
    f7:e3:6a:ad:1a:62:b8:e3:e8:21:e5:e9:d2:7d:fb:
    87:e2:af:03:34:14:38:c4:0d:2d:f6:16:45:0d:1d:
    19:dc:65:86:3f:c0:18:9e:ad:f6:1a:6a:c1:a4:fd:
    fc:fb:71:94:29:93:4d:01:84:fb:80:b3:10:89:99:
    8e:87:fa:24:89:d9:8b:1a:b1:e9:19:65:ad:a4:3e:
    4b:c5:cb:22:0a:c1:52:29:17:12:e9:38:31:d4:f2:
    ef:bf:5d:12:c4:65:34:61:6d:76:80:4b:75:d5:9a:
    18:8d:71:dc:8f:ff:fe:c9:2d:69:69:16:81:fe:ec:
    48:2d:3f:61:6d:a0:ae:b9:c5:00:27:cb:00:5a:f1:
    6c:12:af:88:98:d5:6f:14:9a:8c:2e:6a:12:23:28:
    7e:c9:2a:d7:54:fe:39:0c:d4:15:90:45:fb:fd:76:
    3e:1b:68:be:d3:d3:38:a0:ec:6a:44:8c:93:64:00:
    dc:a1
coefficient:
    00:c2:34:c5:af:a9:86:4f:7e:a6:c4:da:4f:67:1b:
    ae:ef:ab:31:a6:56:5e:9a:ac:51:d0:be:89:f2:e6:
    e2:72:16:65:34:c5:8c:b8:dc:89:98:66:36:a1:91:
    23:cf:1b:fb:87:98:2b:61:69:cb:fa:d3:3b:a9:28:
    01:6b:ba:1b:74:a7:b8:36:a7:e1:85:08:77:29:00:
    72:b7:77:ad:21:b9:f8:aa:0f:8d:c8:41:8e:6c:7b:
    8a:eb:1a:ae:b0:05:21:9b:46:83:29:9e:bf:b4:c0:
    d4:6d:72:e2:64:4c:11:97:e6:24:de:59:7f:07:79:
    e3:ca:bf:ac:6b:1d:14:e1:4b:2c:8f:ce:98:0a:67:
    1b:34:9d:91:e4:d1:0c:c8:d7:24:60:23:f5:42:5c:
    77:84:8b:22:28:e1:c3:3d:ef:b2:b6:28:aa:11:95:
    25:02:e8:75:14:98:76:0e:82:6d:38:5b:06:36:60:
    b2:f9:c0:6e:59:5e:44:89:74:25:3b:9f:4a:04:a9:
    c1:d1:b8:bb:1c:c8:a2:d5:41:2f:46:08:e7:5f:41:
    53:cc:cc:cd:77:0b:0c:b2:83:3c:01:9f:0c:36:b3:
    c1:ff:80:d4:67:bb:04:d2:cd:e5:be:dd:e9:80:c7:
    7b:4b:c8:27:a1:58:f7:c9:27:f2:c0:66:89:19:2c:
    1d:63

```
- Este certificado é um certicado de CA já que o *subject* e o *issuer* são o mesmo (https://sites.google.com/site/ddmwsst/digital-certificates)

- O certificado mostra-se *self-signed* com essa indicação em *CA:TRUE* (https://stackoverflow.com/questions/36999138/self-signed-certificate-with-catrue-and-key-usage-not-set-to-sign-certificates)

- No certificado, é possível identificar módulo e o expoente público.
```
Modulus:
                    00:c1:b1:d8:17:88:02:89:b1:ea:9d:e4:cd:6c:bf:
                    39:61:de:59:11:b8:90:14:83:d8:25:df:2c:ed:b9:
                    eb:ce:da:0d:37:8c:af:a3:72:9a:bf:41:cf:92:49:
                    ef:14:3c:2c:a3:cb:08:30:84:9e:13:73:4b:f1:45:
                    5b:8a:13:26:e6:ef:6a:3a:3c:02:57:33:37:c3:d0:
                    83:ca:5e:ec:8c:a5:b6:e4:36:3c:07:57:f0:21:4e:
                    88:04:80:30:6a:bb:9c:80:f3:55:ee:11:fd:ee:19:
                    52:23:80:dd:5b:79:e8:33:a8:5a:09:c7:e0:c3:77:
                    4f:43:0a:17:f0:eb:48:33:b9:33:d1:f0:1f:f7:67:
                    44:1d:e7:e0:d5:30:88:c4:4b:0c:91:a2:b8:e4:7b:
                    0c:fe:c1:e9:9e:07:e0:70:b7:4e:8e:bb:7a:b3:26:
                    46:20:b5:e3:9d:04:7e:5b:3b:5f:da:be:c3:86:10:
                    a7:2b:c1:f0:76:84:05:d0:de:2e:9d:fd:9c:c6:4b:
                    d8:ab:4c:2c:31:94:d1:00:6c:e5:c1:4b:f8:aa:4b:
                    5c:9f:dc:17:63:0e:03:cb:89:05:20:8f:28:93:2c:
                    52:0d:d1:97:43:cf:34:40:f6:b3:4a:8e:7d:25:44:
                    cb:f5:94:69:2c:96:4a:ac:10:97:aa:f5:5b:b0:83:
                    a2:fc:d5:cf:f5:96:64:41:f6:d0:b0:29:61:0c:68:
                    7d:82:29:e0:e2:4a:d0:a5:e6:fc:00:a0:84:9f:6d:
                    f5:04:d7:f5:9b:2f:91:9e:9d:40:a9:98:b9:2c:be:
                    36:36:2c:7a:da:9a:82:4f:c7:3b:66:ff:93:a9:7c:
                    0e:7d:dd:4e:20:93:e1:d9:79:a2:b5:86:23:8f:c0:
                    a5:ec:dd:77:ec:71:11:24:35:e2:40:20:25:fd:60:
                    5b:cd:7c:1e:c1:1a:68:52:95:77:47:8d:31:d3:1c:
                    ff:ca:05:66:df:1a:fc:7d:5c:43:55:ac:72:97:be:
                    ac:9d:c8:fc:e0:d5:8e:b5:c1:3a:f6:a8:77:a3:99:
                    7a:d9:95:70:9b:a2:83:56:68:fe:d2:94:3b:0e:2e:
                    26:4d:47:19:d8:f6:1a:9e:33:1c:f8:60:02:3e:3d:
                    78:7c:3b:9b:ad:83:cc:f3:9a:e4:86:51:6c:05:6f:
                    e0:9a:ae:1b:70:33:a7:1a:ef:cc:b5:fd:38:b0:58:
                    49:ea:7a:f2:bf:c0:0e:69:eb:9b:66:4b:ec:d4:4d:
                    27:ec:6f:29:25:67:6c:fd:22:79:2e:47:66:84:c3:
                    9b:2b:f4:b4:92:10:1e:d2:93:be:b3:c1:ad:c3:5f:
                    97:5e:cd:af:f8:00:07:49:5f:7a:5f:be:d2:2c:f1:
                    5f:b9:09
                Exponent: 65537 (0x10001)
```

- Já na chave, os primeiros 5 valores constituem respetivamente o módulo, o expoente público, o expoente privado e os dois primos p e q.

## Tarefa 2

Usando este comandos, é possível gerar um pedido de certificado para o *server* pretendido, neste caso, www.fsi622021.com:

```
openssl req -newkey rsa:2048 -sha256 \
-keyout server.key -out server.csr \
-subj "/CN=www.fsi622021.com/O=fsi6221/C=PT" \
-passout pass:dees
```

Obteve-se então este pedido de certificado (comprova-se que o é pela primeira linha)

```
Certificate Request:
    Data:
        Version: 1 (0x0)
        Subject: CN = www.fsi622021.com, O = fsi6221, C = PT
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (2048 bit)
                Modulus:
                    00:c7:24:f5:51:17:f2:17:2b:0b:25:e2:4a:f7:29:
                    1a:19:5c:5b:74:c0:c5:e8:f1:9d:68:db:44:9d:66:
                    c7:1b:9a:16:e9:37:88:b6:86:54:fb:21:ba:bd:d4:
                    e4:e4:2a:e4:18:b7:52:80:f2:73:14:e1:ab:6c:7e:
                    80:31:a2:5c:af:a6:56:0c:ac:24:8b:bb:1d:38:b2:
                    98:20:23:0b:72:a5:48:0c:49:41:b6:8e:cb:07:f3:
                    80:40:c7:3a:e6:39:16:7d:67:3a:ac:6e:df:d8:83:
                    b6:be:da:0a:56:37:ae:d9:3f:34:a3:67:57:16:72:
                    87:9f:8c:fe:84:d1:f5:2b:ce:82:7e:01:af:30:46:
                    c1:21:61:d7:61:72:1d:48:a4:6a:17:d4:e7:29:e0:
                    79:e5:60:9b:a7:47:e1:18:2f:ca:1e:58:67:8b:08:
                    26:a9:25:15:4f:37:a5:08:c8:9a:78:4b:4e:1a:41:
                    22:5b:49:e0:8c:4d:1f:02:8b:58:3f:9e:df:8e:57:
                    19:75:ac:01:2f:9a:81:55:b3:86:9b:8b:1f:c1:a0:
                    33:50:0d:f0:a6:6a:4c:a2:51:9c:81:ec:82:bd:f6:
                    25:58:dc:db:5f:78:fe:3b:b2:6c:3a:53:09:c1:9f:
                    ad:92:7a:01:8c:24:d4:10:46:9d:45:e6:c5:d7:85:
                    cc:27
                Exponent: 65537 (0x10001)
        Attributes:
            a0:00
    Signature Algorithm: sha256WithRSAEncryption
         93:b6:4b:d8:54:dc:5d:78:ed:88:91:fe:e8:3d:c2:11:36:49:
         90:09:70:2e:a3:6d:9b:d4:a6:25:9e:a2:84:21:f7:4a:f3:33:
         04:f4:46:46:43:8f:ab:45:50:aa:f1:23:4b:f9:7a:aa:fb:e3:
         5e:53:ce:19:d8:5a:06:c6:9c:51:64:88:7b:bb:05:8c:cb:9e:
         8d:a9:01:4e:e5:8e:f4:bd:93:2d:ea:8b:4e:91:2a:dd:7a:dd:
         4d:fa:e4:72:56:c7:c1:df:3b:97:60:89:b8:33:9b:c7:29:6c:
         ee:2b:f0:29:7c:5e:14:5c:12:6a:34:67:af:64:05:2b:e8:e9:
         6b:0b:d3:18:8f:25:30:ae:30:c3:8c:4d:40:7b:d4:e1:56:c4:
         25:d2:02:76:37:f4:4c:6e:3a:53:7d:94:b7:98:93:c4:e9:b1:
         33:bb:68:4c:c1:42:de:56:12:20:19:e9:5a:ce:2b:07:36:1b:
         ce:f2:6c:46:6f:ac:f8:44:a1:18:91:3d:f1:1d:e3:d4:d0:92:
         85:c1:41:0b:e4:05:76:3c:6d:14:13:a8:48:da:23:85:ad:84:
         52:80:05:6d:2d:57:d5:b6:7c:d4:55:56:0e:7e:61:b6:74:05:
         49:49:ec:e7:8c:2e:1d:e5:b2:fe:38:ca:e5:20:59:1c:8e:a1:
         79:5c:f1:5d
```

com esta chave:
```
RSA Private-Key: (2048 bit, 2 primes)
modulus:
    00:c7:24:f5:51:17:f2:17:2b:0b:25:e2:4a:f7:29:
    1a:19:5c:5b:74:c0:c5:e8:f1:9d:68:db:44:9d:66:
    c7:1b:9a:16:e9:37:88:b6:86:54:fb:21:ba:bd:d4:
    e4:e4:2a:e4:18:b7:52:80:f2:73:14:e1:ab:6c:7e:
    80:31:a2:5c:af:a6:56:0c:ac:24:8b:bb:1d:38:b2:
    98:20:23:0b:72:a5:48:0c:49:41:b6:8e:cb:07:f3:
    80:40:c7:3a:e6:39:16:7d:67:3a:ac:6e:df:d8:83:
    b6:be:da:0a:56:37:ae:d9:3f:34:a3:67:57:16:72:
    87:9f:8c:fe:84:d1:f5:2b:ce:82:7e:01:af:30:46:
    c1:21:61:d7:61:72:1d:48:a4:6a:17:d4:e7:29:e0:
    79:e5:60:9b:a7:47:e1:18:2f:ca:1e:58:67:8b:08:
    26:a9:25:15:4f:37:a5:08:c8:9a:78:4b:4e:1a:41:
    22:5b:49:e0:8c:4d:1f:02:8b:58:3f:9e:df:8e:57:
    19:75:ac:01:2f:9a:81:55:b3:86:9b:8b:1f:c1:a0:
    33:50:0d:f0:a6:6a:4c:a2:51:9c:81:ec:82:bd:f6:
    25:58:dc:db:5f:78:fe:3b:b2:6c:3a:53:09:c1:9f:
    ad:92:7a:01:8c:24:d4:10:46:9d:45:e6:c5:d7:85:
    cc:27
publicExponent: 65537 (0x10001)
privateExponent:
    2c:07:b5:dd:9a:27:c2:8b:97:c9:66:81:20:a8:8b:
    c6:b3:ae:dc:df:8a:62:78:99:4f:07:bb:e1:f9:49:
    68:86:e7:2d:e5:43:6a:e7:c4:7e:49:f4:d9:e7:ea:
    3b:b0:68:02:36:f6:1c:e0:7e:25:4d:c7:f3:12:fd:
    10:fc:4e:f5:df:17:03:72:44:1a:48:e2:ab:18:81:
    9e:09:61:8c:95:92:9a:74:cf:fc:a7:11:a8:ce:63:
    ba:ee:d1:cc:f9:2e:49:c7:bb:27:48:d4:61:30:ae:
    05:00:7c:6c:97:9f:27:15:5c:74:0c:73:2a:d9:63:
    b7:19:1b:65:0e:6e:e0:a2:42:42:9d:dd:b5:06:0e:
    6d:79:4d:1f:d9:d0:81:62:d4:bc:57:fa:19:c3:40:
    8e:90:b1:9b:e9:30:d4:db:57:a0:0a:f9:e0:87:26:
    91:76:5d:5c:b7:57:e7:8f:ec:8d:73:9b:ec:40:03:
    85:91:43:b7:39:6d:82:6c:26:9a:21:f6:8d:64:75:
    77:59:ba:55:76:c7:73:73:b0:73:72:b8:89:9d:61:
    a2:35:3a:23:76:01:07:2c:75:ae:19:16:5c:ed:fe:
    d7:4e:ee:af:37:31:be:16:41:58:7f:0a:1f:b6:96:
    f0:bc:f8:3b:19:5c:cf:c3:52:73:58:d3:4d:8f:be:
    71
prime1:
    00:e7:e4:e3:64:b4:6d:09:ae:d9:6b:01:ca:ba:b4:
    ad:1a:12:de:13:18:33:66:86:78:d4:22:29:30:55:
    5b:05:08:8a:e9:3f:d1:1f:9a:5c:f4:c7:bb:ab:13:
    a8:62:1a:f3:c2:29:a6:37:02:c2:6b:17:28:c5:6f:
    1f:26:01:32:ef:7a:89:11:4c:e2:7b:6f:d6:2f:b3:
    44:45:64:9d:d1:04:58:a9:87:dd:12:53:2e:0a:36:
    dc:65:72:37:c9:18:32:ca:cf:bc:32:6c:75:20:06:
    1c:f9:ca:f8:fa:d1:53:60:c9:37:9f:e4:c0:24:2c:
    0f:f5:cc:1e:4f:7f:2a:38:03
prime2:
    00:db:d8:8a:ba:3b:55:5c:c9:6c:fe:37:09:a5:05:
    79:0f:3a:e8:5e:5f:ab:d5:53:81:69:60:ac:f8:62:
    39:13:9c:19:6d:d6:2b:10:a8:6f:99:5a:d8:15:41:
    58:8a:ab:91:f7:4a:09:d6:c9:d5:6b:7c:0c:21:f6:
    30:6d:5a:92:cb:3c:11:8a:95:47:6c:f5:59:97:85:
    c2:0b:b2:9c:f4:e9:a0:3d:da:de:24:ce:44:b2:20:
    97:b8:d5:fd:a5:dc:19:ff:98:ad:c9:74:60:ac:e5:
    0e:56:4b:96:14:c1:6e:7e:0d:fc:a6:21:9f:8e:68:
    db:8e:ba:c6:c1:36:6a:fc:0d
exponent1:
    5f:2a:18:83:88:63:c2:f8:85:73:1b:8e:25:e6:e5:
    ae:f0:95:40:42:cb:3d:44:ec:2b:2a:45:ba:f7:1c:
    5e:49:6e:30:60:a7:22:90:07:9b:d0:a7:dc:82:39:
    b4:e1:18:ad:d2:c7:ca:85:90:61:c0:64:53:f9:d1:
    4f:98:68:5d:cc:ec:99:33:f3:31:f2:e8:74:34:de:
    4c:98:09:07:f0:ff:ad:ba:fa:e7:7d:49:44:99:d5:
    02:b0:c7:e1:f7:d3:48:55:ce:06:e7:69:7d:95:e4:
    a8:42:3a:c1:3b:cc:3a:c8:f8:d1:de:5f:57:b8:d9:
    67:e6:b7:7d:aa:53:1a:1f
exponent2:
    00:a8:d6:3d:7c:56:b2:f1:06:74:61:2b:ad:89:81:
    91:7e:63:d4:2f:1e:34:5e:29:ba:7a:4e:57:a8:8d:
    ee:9d:a3:c5:57:b8:21:ec:b2:1e:ba:dc:ac:94:6e:
    51:ec:75:65:2d:50:3c:0c:2b:87:6e:fb:9e:69:ba:
    a3:68:68:25:d2:55:38:77:80:bb:90:ef:40:36:00:
    f0:8c:81:48:cf:42:58:e1:08:24:90:89:a4:f2:53:
    db:91:85:2e:3e:61:b1:c9:bc:dc:c2:99:50:e1:97:
    2c:12:94:0c:17:b6:91:ff:d7:08:10:22:44:62:5f:
    1f:37:17:34:2b:10:7a:cb:45
coefficient:
    00:d6:ef:ba:1c:29:c9:28:9b:fc:c1:59:00:00:b1:
    57:67:19:2f:7c:26:20:21:38:0b:36:0c:1a:bd:74:
    9c:9e:61:cd:9c:f4:80:17:85:0f:bf:b3:cd:9b:84:
    f4:53:d7:e4:7e:4a:fa:28:d8:eb:77:58:19:17:0b:
    61:bd:84:df:51:c6:21:df:f1:c0:97:08:ad:7b:c3:
    36:ef:b9:4d:43:9a:3f:dc:5b:0e:c9:13:b1:b8:85:
    55:05:d9:71:53:93:ee:cb:69:87:63:7e:20:50:13:
    ba:75:91:8e:82:66:c3:09:4b:4f:5c:90:dc:90:10:
    a8:17:52:5a:06:7e:2e:74:2c
```

Para adicionar nomes alternativos, como pedido correu-se o seguinte comando:
```
openssl req -newkey rsa:2048 -sha256 \
-keyout server.key -out server.csr \
-subj "/CN=www.fsi622021.com/O=fsi6221/C=PT" \
-passout pass:dees
-addext "subjectAltName = DNS:www.fsi622021.com, \
DNS:www.fsi622021A.com, \
DNS:www.fsi622021B.com"
```

No certificado surgiu então a menção a tal:

![/imgs11/alternativeNames.png](/imgs11/alternativeNames.png)

## Tarefa 3

Correndo este comando, 
```
openssl ca -config openssl.cnf -policy policy_anything \
-md sha256 -days 3650 \
-in server.csr -out server.crt -batch \
-cert ca.crt -keyfile ca.key
```
foi gerado o certificado com os nomes alternativos adicionados.
![/imgs11/certificate.png](/imgs11/certificate.png)

## Tarefa 4

## Tarefa 5

## Tarefa 6

openssl req -newkey rsa:2048 -sha256 \
-keyout server.key -out server.csr \
-subj "/CN=www.google.com/O=google/C=PT" \
-passout pass:dees






