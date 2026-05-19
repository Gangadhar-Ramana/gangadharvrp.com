# Website Deployment and Custom Domain Setup

## Current Deployment Plan

This website is a static HTML site. It can be hosted directly with GitHub Pages from the repository's `main` branch.

Planned GitHub Pages settings:

- Source: Deploy from a branch
- Branch: `main`
- Folder: `/`
- Custom domain: `www.gangadharvrp.com`
- HTTPS: Enabled after DNS is detected by GitHub

The `CNAME` file in this repository contains:

```text
www.gangadharvrp.com
```

GitHub Pages uses this file to bind the Pages site to the custom domain.

## DNS Records Required From Domain Provider

At the DNS provider for `gangadharvrp.com`, create or update these records.

### Required record for `www.gangadharvrp.com`

| Type | Name / Host | Value / Target | TTL |
| --- | --- | --- | --- |
| CNAME | `www` | `gangadhar-ramana.github.io` | Automatic or 3600 |

This makes `www.gangadharvrp.com` point to the GitHub Pages host for the GitHub account `Gangadhar-Ramana`.

### Optional records for root domain `gangadharvrp.com`

If you also want `gangadharvrp.com` to work without `www`, add these `A` records:

| Type | Name / Host | Value | TTL |
| --- | --- | --- | --- |
| A | `@` | `185.199.108.153` | Automatic or 3600 |
| A | `@` | `185.199.109.153` | Automatic or 3600 |
| A | `@` | `185.199.110.153` | Automatic or 3600 |
| A | `@` | `185.199.111.153` | Automatic or 3600 |

Optional IPv6 records:

| Type | Name / Host | Value | TTL |
| --- | --- | --- | --- |
| AAAA | `@` | `2606:50c0:8000::153` | Automatic or 3600 |
| AAAA | `@` | `2606:50c0:8001::153` | Automatic or 3600 |
| AAAA | `@` | `2606:50c0:8002::153` | Automatic or 3600 |
| AAAA | `@` | `2606:50c0:8003::153` | Automatic or 3600 |

## Details Needed From Domain Provider

If you want me to complete or verify the domain connection, provide one of these:

1. A screenshot or text export of the DNS records for `gangadharvrp.com`.
2. The DNS provider name and the current records for `@` and `www`.
3. Confirmation that the `www` CNAME record was added as shown above.

Do not send passwords or private login details. DNS record names, types, and values are enough.

## Verification Steps

After DNS is updated, verify with:

```powershell
nslookup www.gangadharvrp.com
nslookup gangadharvrp.com
```

Expected result for `www.gangadharvrp.com`:

```text
www.gangadharvrp.com canonical name = gangadhar-ramana.github.io
```

Then check the GitHub Pages settings page and enable `Enforce HTTPS` once GitHub finishes issuing the certificate.

