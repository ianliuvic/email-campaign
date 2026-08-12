# email-campaign

静态邮件页面，用于 Zoho Campaigns 营销活动（Hongxiu Swimwear / 红绣）。

## 结构

- `index.html` — 邮件正文（邮件客户端兼容：table 布局 + 内联样式，600px）
- `images/` — 图片素材（来自 wearhongxiu.com 官网）

## 部署

Coolify 静态站点（nginx:alpine），域名：`https://email.wearhongxiu.com`

## 个性化

正文使用 Zoho 合并标签 `$[FNAME|friend]$` 插入联系人名字（对应 CAM-01 列表的 First Name）。

## 更新

修改 `index.html` 或 `images/` 后 push 到 main 分支，Coolify 自动重新部署。
