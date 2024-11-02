# Cloudflare

<https://www.cloudflare.com/>

<!-- INDEX_START -->

- [Summmary](#summmary)
- [Cloudflare API Scripts](#cloudflare-api-scripts)
- [Kubernetes Cert Manager + Cloudflare Integration](#kubernetes-cert-manager--cloudflare-integration)
- [Kubernetes External DNS + Cloudflare Integration](#kubernetes-external-dns--cloudflare-integration)
- [Cloudflare Workers](#cloudflare-workers)

<!-- INDEX_END -->

## Summmary

- DNS
- CDN
- Proxy protection (DDoS, WAF)
- Worker scripts (can return web pages for given URLs eg. maintenance page)

## Cloudflare API Scripts

[nholuongut/devops-bash-tools](https://github.com/nholuongut/devops-bash-tools#internet-services)

- List/Add/Update/Delete DNS records
- List zones, iterate zones
- Firewall rules
- Purge cache
- get Cloudflare IP Ranges for Proxied Protection for your firewall rules

`cloudflare/cloudflare_*.sh`

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=DevOps-Bash-tools&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/devops-bash-tools)

## Kubernetes Cert Manager + Cloudflare Integration

Integrates to generate the TXT validation records for [LetsEncrypt](https://letsencrypt.org/) to generate automatic free SSL certificates for Kubernetes ingresses.

[nholuongut/kubernetes-configs cert-manager](https://github.com/nholuongut/kubernetes-configs/blob/master/cert-manager/base/cert-manager-clusterissuer.yaml)

[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=nholuongut&repo=Kubernetes-configs&theme=ambient_gradient&description_lines_count=3)](https://github.com/nholuongut/kubernetes-configs)

## Kubernetes External DNS + Cloudflare Integration

Integrates to upsert DNS records to Cloudflare for Kubernetes ingresses.

[nholuongut/kubernetes-configs external-dns](https://github.com/nholuongut/kubernetes-configs/blob/54ad50efc573f7a69b36be1bd504d0e214fa73b5/external-dns/base/values.yaml#L159)

## Cloudflare Workers

List of workers:

```shell
curl -X GET "https://api.cloudflare.com/client/v4/zones/$ZONE_ID/workers/scripts" \
     -H "X-Auth-Email: $EMAIL" \
     -H "X-Auth-Key: $TOKEN"
```

List of workers routes:

```shell
curl -X GET "https://api.cloudflare.com/client/v4/zones/$ZONE_ID/workers/scripts" \
     -H "X-Auth-Email: $EMAIL" \
     -H "X-Auth-Key: $TOKEN"
```

Create route:

```shell
curl -X POST "https://api.cloudflare.com/client/v4/zones/$ZONE_ID/workers/routes" \
     -H "X-Auth-Email: $EMAIL" \
     -H "X-Auth-Key: $TOKEN" \
     -H "Content-Type: application/json" \
     --data '{"pattern":"*.mydomain.com/*","script":"maintenance"}'
```

Delete route:

```shell
curl -X DELETE "https://api.cloudflare.com/client/v4/zones/$ZONE_ID/workers/routes/$ROUTE_ID" \
     -H "X-Auth-Email: $EMAIL" \
     -H "X-Auth-Key: $TOKEN"
```

**Ported from private Knowledge Base page 2020+**
