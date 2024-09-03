Useful Commands
===============

1. Generate dhparam with openssl:
```
$ openssl dhparam -out dhparam.pem 2048
```

2. Curl with verbose:
```
$ curl -v https://app.srwx.tech
```

3. Get RSA cert with acme.sh:
```
$ acme.sh --issue -d app.srwx.tech -w /opt/www/ --server letsencrypt --keylength 2048
```

4. Get ECC cert with acme.sh:
```
$ acme.sh --issue -d app.srwx.tech -w /opt/www/ --server letsencrypt --keylength ec-256
```

5. Get ECC 384 cert with acme.sh:
```
$ acme.sh --issue -d app.srwx.tech -w /opt/www/ --server letsencrypt --keylength ec-384
```

6. Openssl save and reuse session:
```
$ openssl s_client -connect app.srwx.tech:443 -sess_out session.pem

Ctrl+D

$ openssl s_client -connect app.srwx.tech:443 -sess_in session.pem

Ctrl+D

```

7. Openssl send early_data:
```
$ cat > request.txt << EOF
GET / HTTP/1.1
Host: app.srwx.tech

EOF

$ openssl s_client -connect app.srwx.tech:443 -sess_out session.pem

Ctrl+D

$ openssl s_client -connect app.srwx.tech:443 -sess_in session.pem -early_data request.txt

Ctrl+D


```
