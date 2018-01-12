Generate TLS Certificate Authority, Server Certs and Client Certs.

Based off the guide for Rabbit MQ, but with `bash` scripts to make it easier to create a simple CA that can generate multiple server and client certs via a simple script. Simalar to [`tls-gen`](https://github.com/michaelklishin/tls-gen) but with no dependencies other than `bash` and `openssl`.


Generate self-signed root CA, clone this repo and run the following from the directory.

```
./bin/generate-ca-key-and-cert
```

This will create the following files:

- `ca/cacert.pem`
- `ca/private/root.key`

Those can then be used to create new certs.

### Server

```
./bin/generate-server-cert HOSTNAME
```

This will create the following files:

- `server-HOSTNAME/cert.pem`
- `server-HOSTNAME/key.pem`

### Client

```
./bin/generate-client-cert NAME
```

This will create the following files:

- `client-NAME/cert.pem`
- `client-NAME/key.pem`


---

Both options will but the name in the CN (common name) field in the cert subject.

If you want to change the orgnization you can set the env variable `ORGNIZATION`:

```
ORGNIZATION=MyOtherOrg ./bin/generate-client-cert NAME
```
