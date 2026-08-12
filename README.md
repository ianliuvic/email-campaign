# email-campaign

静态邮件页面仓库，用于 Zoho Campaigns 营销活动（Hongxiu Swimwear / 红袖）。
每封邮件一个独立目录，Coolify 静态站点部署在 `https://email.wearhongxiu.com`。

## 结构

```
email-campaign/
├── index.html                  # 入口页：所有邮件的可视化索引
├── README.md                   # 活动清单（本文件）
├── images/                     # 共享图片素材（绝对 URL 引用）
├── templates/
│   └── base-template.html      # 基础邮件模板（复制它开新邮件）
└── campaigns/
    └── 2026-08-oem-odm-01/     # 每封邮件一个目录
        └── index.html
```

## 活动清单

| 活动 | 目录 | 页面 URL | Zoho campaign_id | 状态 |
|---|---|---|---|---|
| Hongxiu Swimwear OEM-ODM Campaign 01 | `campaigns/2026-08-oem-odm-01/` | <https://email.wearhongxiu.com/campaigns/2026-08-oem-odm-01/> | 31089000000164552 | Draft |
| Wholesale Swimwear Campaign 01 | `campaigns/2026-08-wholesale-swimwear/` | <https://email.wearhongxiu.com/campaigns/2026-08-wholesale-swimwear/> | —（Zoho 未创建） | 待预览确认 |

## 新建邮件的流程

1. 复制 `templates/base-template.html` 到 `campaigns/YYYY-MM-short-name/index.html`
2. 修改正文；保留合并标签 `$[FNAME|friend]$`（联系人名字）和 `$[LI:UNSUBSCRIBE]$`（退订链接）
3. 图片统一用绝对 URL：`https://email.wearhongxiu.com/images/<file>`
4. 提交并推送（Coolify 自动部署），确认页面可访问
5. 用 Zoho Campaigns API 以 `content_url` 创建草稿活动（不要直接发送）
6. 在本表登记映射，并把入口页 `index.html` 加上卡片

## 部署

Coolify 静态站点（nginx:alpine），域名 `https://email.wearhongxiu.com`。
修改任意文件后 push 到 `main` 分支，Coolify 自动重新部署；也可通过 API 手动触发。

## 注意

- 目录名即活动名，确定后不要改名（Zoho 内容在创建时抓取存储，无更新接口）
- 每个活动的 `content_url` 必须指向其独立目录 URL
- 邮件一律使用 table 布局 + 内联样式，保持邮件客户端兼容
