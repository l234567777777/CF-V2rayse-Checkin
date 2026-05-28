# 自动签到系统

> 基于 Cloudflare Workers 的通用网站自动签到脚本，支持 V2rayse、SSPanel 等多种网站类型，内置 Web 管理面板。

## 功能特性

- **多平台支持**：V2rayse、SSPanel 等网站自动签到
- **Web 管理面板**：可视化配置、手动触发签到、查看日志
- **Telegram 推送**：签到结果实时推送到 TG（支持自定义 Bot 或内置 Bot）
- **定时任务**：支持 Cloudflare Cron Trigger 自动执行
- **Cookie 自动管理**：登录态自动维护，无需手动干预
- **重试机制**：失败自动重试 3 次

## 快速开始

### 1. 部署到 Cloudflare Workers

1. 登录 [Cloudflare Workers](https://workers.cloudflare.com/)
2. 创建新 Worker
3. 将 `index.js` 内容复制到 Worker 编辑器中
4. 保存并部署

### 2. 配置环境变量

在 Worker 设置 → **Variables and Secrets** 中添加：

| 变量名 | 必填 | 说明 |
|--------|------|------|
| `JC` / `DOMAIN` | ✅ | 机场域名（如 `https://xxx.com`） |
| `ZH` / `USER` | ✅ | 登录邮箱 |
| `MM` / `PASS` | ✅ | 登录密码 |
| `TYPE` | ✅ | 网站类型：`v2rayse` 或 `sspanel` |
| `TGTOKEN` / `TG_TOKEN` | ❌ | Telegram Bot Token（自定义 Bot） |
| `TGID` / `TG_ID` | ❌ | Telegram Chat ID |

> **注意**：`TGTOKEN` 和 `TGID` 都不填时，使用内置 Bot 推送（需填写 `TGID`）。

### 3. 设置定时任务

在 Worker 设置 → **Triggers** → **Cron Triggers** 中添加：

```
0 6 * * *
```

表示每天早上 6:00 自动执行签到。

### 4. 访问管理面板

部署后访问 Worker 的 URL（如 `https://your-worker.your-subdomain.workers.dev/`），输入密码即可登录管理面板。

面板功能：
- 查看当前配置信息（脱敏显示）
- 手动触发签到
- 测试 Telegram 推送
- 实时查看签到日志

## 项目结构

```
├── index.js          # 主文件（Cloudflare Worker 入口）
├── README.md         # 项目说明
├── wrangler.toml     # Cloudflare Workers 配置文件（可选）
└── .gitignore        # Git 忽略规则
```

## 技术栈

- **Runtime**: Cloudflare Workers (V8 Isolate)
- **API**: Fetch API
- **Auth**: SHA-256 哈希验证
- **UI**: 原生 HTML/CSS/JS（无框架依赖）

## 安全说明

- 管理面板使用 SHA-256 哈希验证，密码不存储在客户端
- 配置信息在面板中脱敏显示
- Telegram 推送中的密码使用 `<tg-spoiler>` 标签隐藏

## 常见问题

**Q: 签到返回"签到失败"但实际成功了？**

A: 某些网站返回的 JSON 结构不同（如 `summary.points` 而非 `awardedPoints`）。代码已内置多种成功判定逻辑，如遇问题请查看日志中的原始响应。

**Q: 如何查看详细日志？**

A: 在管理面板点击"手动执行签到"，日志会实时显示在右侧控制台。也可在 Cloudflare Workers 的 **Logs** 中查看。

**Q: 支持多个机场同时签到吗？**

A: 当前版本每个 Worker 实例只支持一个机场。如需多机场，可部署多个 Worker 实例。

## License

MIT