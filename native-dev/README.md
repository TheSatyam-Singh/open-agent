# Native dev certificates

These helpers let you generate self-signed certificates for local HTTPS development (no Docker required).

## Prerequisites (macOS only)

- macOS with `security` CLI available (used by install/uninstall in `cert.ts`)
- `openssl` on PATH
- Admin/sudo privileges for `yarn oa cert --install` / `--uninstall`
- Linux/Windows are not supported by these helpers (cert install/uninstall use macOS-specific commands)

## 1. Generate and install Root CA (macOS)

```bash
# the root CA will be stored under `./native-dev/certs/ca`
yarn oa cert --install
```

## 2. Generate domain certs

```bash
# certificates will be placed at `./native-dev/certs/${domain}`
yarn oa cert --domain open-agent.localhost
```

## 2b. Uninstall Root CA (macOS)

```bash
# removes the self-signed CA from macOS keychain (requires sudo)
yarn oa cert --uninstall
```

## 3. Wire into your local proxy (optional, macOS)

Rendered nginx snippets are written to `./native-dev/nginx/conf.d`. You can point a local nginx (or similar) at `./native-dev/nginx/nginx.conf` as a base and include the generated snippets to serve HTTPS locally.
