# docker-goldfish

[![Docker Pulls](https://img.shields.io/docker/pulls/mvisonneau/goldfish.svg)](https://hub.docker.com/r/mvisonneau/goldfish/)

Allows you to build a runtime configurable container of the very good [Caiyeon/goldfish](https://github.com/Caiyeon/goldfish) project. An opensource Web UI for [Hashicorp Vault](https://vaultproject.io)

## Usage

```
~$ docker run -it --rm -e VAULT_ADDR=https://vault.rocks:8200 mvisonneau/goldfish:latest
```

In a few seconds, you will have a fully working version available at [https://localhost](https://localhost)

## Configuration

You can use the following environment variables in order to configure the container:

Name | Required | Description
--- | --- | ---
**GOLDFISH_APPROLE_ID**     | *false* | ID of the approle that Goldfish will use for authenticating itself against Vault (default: `goldfish`)
**GOLDFISH_APPROLE_LOGIN**  | *false* | Path of the approle auth backend on Vault (default: `auth/approle/login` )
**GOLDFISH_DISABLE_MLOCK**  | *false* | Disable mlock (default `1`)
**GOLDFISH_LISTEN_ADDRESS** | *false* | Listener address for Goldfish (default: `0.0.0.0:443`)
**GOLDFISH_RUNTIME_CONFIG** | *false* | KV path on Vault where Goldfish config will be stored (default: `secret/goldfish`)
**VAULT_ADDR**              | *false* | Vault Endpoint (default: `http://vault:8200`)
**VAULT_SKIP_VERIFY**       | *false* | Skip TLS verification on the Vault endpoint (default: `0`)

### SSL

This container will only use TLS endpoints. If not provided, it will generate dummy key/cert. If you want to use your owns, attach them on the following paths :

```
~$ docker run -it --rm \
     -v my_cert.crt:/etc/ssl/goldfish.crt
     -v my_cert.key:/etc/ssl/goldfish.key
     mvisonneau/goldfish
```

## Contribute

Contributions are more than welcome! Feel free to submit a [PR](https://github.com/mvisonneau/docker-goldfish/pulls).
