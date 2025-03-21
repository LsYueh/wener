---
title: Domain
---

# Domain

- 推荐 TLD
  - .app
  - .how
  - .dev
  - .name
  - .co - company
  - .me - 我的
  - .ws - Web Service
  - .tech
  - .tax - 财税、企业服务行业
- 参考
  - [It's official: .corp, .home, .mail will never be top-level domains on the 'net](https://forums.theregister.com/forum/all/2018/02/12/icann_corp_home_mail_gtlds/)
  - [google/nomulus](https://github.com/google/nomulus/)
    - Google tld 管理服务
  - [.internal](https://tools.ietf.org/html/draft-wkumari-dnsop-internal-00)
  - [List of Internet top-level domains](https://en.wikipedia.org/wiki/List_of_Internet_top-level_domains)
  - [List of Top-Level Domains](https://www.icann.org/resources/pages/tlds-2012-02-25-en)
    - [tlds-alpha-by-domain.txt](http://data.iana.org/TLD/tlds-alpha-by-domain.txt)

:::info

- [er](http://www.iana.org/domains/root/db/er.html) TLD 目前无法注册，但是有
  - https://www.101domain.com/er.htm

:::

## 中国 {#china}

- 中国互联网域名体系 https://domain.miit.gov.cn/
  - 列举了可备案的顶级域名和管理公司
- 阿里云域名列表 https://help.aliyun.com/zh/dws/support/list-of-suffixes-of-top-level-domain-names
- 阿里云域名价格 https://wanwang.aliyun.com/help/price.html
- 腾讯云域名价格列表 https://buy.cloud.tencent.com/domain/price

## Provider

- ~~[domains.google](https://domains.google)~~
  - Google Domains 定价和支持的 TLD
  - https://support.google.com/domains/answer/6010092
  - 被 squarespace 收购 - 20230907 18M$
- [registry.google](https://registry.google)
- [iwantmyname.com](https://iwantmyname.com)

## 本地域名

- [Private DNS Namespaces](https://tools.ietf.org/html/rfc6762#appendix-G)

| TLD        | RFC     | desc                     |
| ---------- | ------- | ------------------------ |
| .internal  | rfc6762 | 内部                     |
| .intranet  | rfc6762 | 内网                     |
| .lan       | rfc6762 | 本地局域网               |
| .corp      | rfc6762 | 企业内部                 |
| .home      | rfc6762 | 家庭                     |
| .private   | rfc6762 | 私有                     |
| .test      |         | 测试使用，不会被注册     |
| .example   |         | 示例站点                 |
| .invalid   |         | 无效域名示例             |
| .localhost |         | 本机                     |
| .local     |         | 本地, LAN, mDNS 发现域名 |
| .mail      |         | 邮件                     |

## 组织性域名

| TLD     | desc                            |
| ------- | ------------------------------- |
| .com    | 商业                            |
| .net    | 类似 .com ， 可区分用于内部系统 |
| .org    | 组织                            |
| .edu    | 教育                            |
| .cn     | 中国                            |
| .google | Google                          |

## 开发相关性域名

| TLD       | desc                  |
| --------- | --------------------- |
| .dev      | 开发站点，必须 HTTPS  |
| .app      | 应用                  |
| .me       | 个人站点              |
| .io       | 技术性项目、产品站点  |
| .rest     | RESTful               |
| .services | 服务                  |
| .ws       | WebService、WebSocket |
| .it       | IT                    |

## 如何为服务选择二级域名

- linode.com - 营销主页
  - cloud.linode.com - 后台
  - api.linode.com
- cloudflare.com - 主页
  - dash.cloudflare.com - 后台
  - api.cloudflare.com - 接口
  - developers.cloudflare.com
- github.com - 登录后的用户页面
  - github.com - 未登录显示另外的内容
- gitlab.com - 登录后的用户页面
  - about.gitlab.com - 未登录的主页
- google.com
  - myaccount.google.com - 当前用户账户
  - accounts.google.com - 登录、注销
  - cloud.google.com - GCP
  - `<服务>.googleapis.com` - API 域名
  - support.google.com
- twitter.com
  - developer.twitter.com
  - api.twitter.com
    - https://api.twitter.com/2/openapi.json
