# Keycloak Secrets via Vault

## Setup

https://www.vaultproject.io/docs/plugin

### Config

```
vault write keycloak/config/connection \
    server_url="http://localhost:8080" \
    realm="master" \
    client_id="vault" \
    client_secret="sec3t"
```

You can provsion the keycloak realm with our terraform module:

https://github.com/Serviceware/terraform-vaultkeycloak-keycloak-client


### Usage

```
vault read keycloak/client-secret/my-client

```

## Test Setup

First run `mockery`

## Test Run

```bash
export VAULT_ADDR="http://127.0.0.1:8200
```

```bash
make build && make start
```

```
make enable
vault write keycloak/config/connection \
    server_url="http://localhost:8080" \
    realm="master" \
    client_id="vault" \
    client_secret="sec3t"

vault read keycloak/client-secret/foo
```
