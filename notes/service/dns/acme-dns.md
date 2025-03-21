---
title: acme-dns
---

# acme-dns

- [joohoi/acme-dns](https://github.com/joohoi/acme-dns) 是什么？
  - 专门用于辅助申请 cert 的 dns 服务 - 提供 HTTP 接口
  - 将现有 `_acme-challenge.domain.tld.` CNAME 到从该服务申请的二级域名 - 例如 `abc.auth.example.org`
  - 避免操作现有 DNS 服务
  - 支持 selfhost - acme-dns.io 国内不一定能访问
    - 支持 SQLite3 和 PostgreSQL
  - 适用于单个域名需要证书，域名使用的外部 DNS 服务且指向的内部 IP
  - 适用于泛域名证书 - `domain.tld`, `*.domain.tld`
- 支持客户端
  - [acme.sh](https://github.com/Neilpang/acme.sh)
  - [Certify The Web](https://github.com/webprofusion/certify)
  - [cert-manager](https://github.com/jetstack/cert-manager)
  - [Lego](https://github.com/xenolf/lego)
  - [Posh-ACME](https://github.com/rmbolger/Posh-ACME)
  - [Sewer](https://github.com/komuw/sewer)
  - [Traefik](https://github.com/containous/traefik)
  - [Windows ACME Simple (WACS)](https://www.win-acme.com)

:::caution 一个账号对应一个域名

- 因为一个账号只能处理两个 record - `domain.tld`,`*.domain.tld`
- **不能** 共享账号给不同域名
- [#110](https://github.com/joohoi/acme-dns/issues/110) Allow more than two records?
- [#233](https://github.com/joohoi/acme-dns/issues/233) Register multiple domains under single login?

:::

```bash title="注册生成账号"
curl -sX POST https://auth.acme-dns.io/register | jq
```

```json
{
  "username": "6f449871-18d4-4239-851c-8c221d56750f",
  "password": "1lBTiQ5MowHC1aJ1QmAYJh9PEe5dljFTEk0zXXJv",
  "fulldomain": "96afb9f9-93c2-4d3c-ad4a-e2ebfbf14f7b.auth.acme-dns.io",
  "subdomain": "96afb9f9-93c2-4d3c-ad4a-e2ebfbf14f7b",
  "allowfrom": []
}
```

```pre title="添加域名映射"
_acme-challenge.domain.tld 6f449871-18d4-4239-851c-8c221d56750f.auth.acme-dns.io
```

至此 可以配置工具 获取泛域名证书。

```bash
dig CNAME _acme-challenge.domain.tld # 检测 CNAME 正确
dig TXT _acme-challenge.domain.tld   # 检测正确设置 challenge
```

## API

```bash
docker run --rm --name acmedns \
  -p 53:53 \
  -p 53:53/udp \
  -p 80:80 \
  -v /path/to/your/config:/etc/acme-dns:ro \
  -v /path/to/your/data:/var/lib/acme-dns \
  -d joohoi/acme-dns
```

```http
POST /register
```

```json
{
  "allowfrom": ["0.0.0.0/0"]
}
```

```json
{
  "allowfrom": ["192.168.100.1/24", "1.2.3.4/32", "2002:c0a8:2a00::0/40"],
  "fulldomain": "8e5700ea-a4bf-41c7-8a77-e990661dcc6a.auth.acme-dns.io",
  "password": "htB9mR9DYgcu9bX_afHF62erXaH2TS7bg9KW3F7Z",
  "subdomain": "8e5700ea-a4bf-41c7-8a77-e990661dcc6a",
  "username": "c36f50e8-4632-44f0-83fe-e070fef28a10"
}
```

```http
POST /update
X-Api-User:
X-Api-Key:
```

```json
{
  "subdomain": "8e5700ea-a4bf-41c7-8a77-e990661dcc6a",
  "txt": "___validation_token_received_from_the_ca___"
}
```

```json
{
  "txt": "___validation_token_received_from_the_ca___"
}
```

```http
GET /health
```

## cert-manager

```yaml
apiVersion: cert-manager.io/v1
kind: Issuer
metadata:
  name: example-issuer
spec:
  acme:
    solvers:
      - dns01:
          acmeDNS:
            host: https://acme.example.com
            accountSecretRef:
              name: acme-dns
              key: acme-dns.json
```

acme-dns.json 支持配置多个域名

```json title="acme-dns.json"
{
  "dev.wener.me": {
    "username": "00000000-0000-0000-0000-000000000000",
    "password": "",
    "fulldomain": "00000000-0000-0000-0000-000000000000.auth.acme-dns.io",
    "subdomain": "00000000-0000-0000-0000-000000000000",
    "allowfrom": []
  },
  "test.wener.me": {
    "username": "00000000-0000-0000-0000-000000000000",
    "password": "",
    "fulldomain": "00000000-0000-0000-0000-000000000000.auth.acme-dns.io",
    "subdomain": "00000000-0000-0000-0000-000000000000",
    "allowfrom": []
  }
}
```
