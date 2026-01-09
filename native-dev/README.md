# Native dev certificates

These helpers let you generate self-signed certificates for local HTTPS development (no Docker required).

## 1. Generate and install Root CA

```bash
# the root CA will be stored under `./native-dev/certs/ca`
yarn oa cert --install
```

## 2. Generate domain certs

```bash
# certificates will be placed at `./native-dev/certs/${domain}`
yarn oa cert --domain open-agent.localhost
```

## 3. Wire into your local proxy (optional)

Rendered nginx snippets are written to `./native-dev/nginx/conf.d`. You can point a local nginx (or similar) at `./native-dev/nginx/nginx.conf` as a base and include the generated snippets to serve HTTPS locally.
