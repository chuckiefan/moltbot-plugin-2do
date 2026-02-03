# moltbot-plugin-2do

一个 [Moltbot (OpenClaw)](https://docs.openclaw.ai) 插件，通过自然语言创建任务并发送到 [2Do](https://www.2doapp.com) app。

支持所有 Moltbot 消息渠道（QQ、企业微信、Slack、Telegram、WhatsApp、Discord 等），利用 2Do 的 [Email to 2Do](https://www.2doapp.com/kb/category/ios/email-to-2do/44/) 功能自动捕获邮件为任务。

## 功能

- 解析中文自然语言任务描述
- 支持指定目标列表和标签
- 通过 SMTP 邮件发送到 2Do
- 支持所有 Moltbot 消息渠道

## 使用示例

**基本任务：**

> 添加任务：明天去超市买牛奶

**指定列表：**

> 添加任务到工作列表：完成项目报告

**指定标签：**

> 添加任务：买菜，标签是家务和购物

**列表 + 标签：**

> 添加任务：周五前完成季度报告，列表是工作，标签是紧急和财务

## 安装

### 前置条件

- Node.js >= 22
- Moltbot (OpenClaw) 已安装
- 2Do app 已配置 Email to 2Do 功能
- 可用的 SMTP 邮箱账户

### 安装到 Moltbot

将本项目克隆到 Moltbot 的 skills 目录：

```bash
cd ~/.openclaw/skills
git clone https://github.com/chuckiefan/moltbot-plugin-2do.git
cd moltbot-plugin-2do
npm install
npm run build
```

### 配置

在 `~/.openclaw/openclaw.json` 中添加环境变量：

```json
{
  "skills": {
    "entries": {
      "moltbot-plugin-2do": {
        "enabled": true,
        "env": {
          "TWODO_EMAIL": "your-2do-email@example.com",
          "SMTP_HOST": "smtp.gmail.com",
          "SMTP_PORT": "587",
          "SMTP_USER": "your-email@gmail.com",
          "SMTP_PASS": "your-app-specific-password"
        }
      }
    }
  }
}
```

| 环境变量 | 说明 |
|---------|------|
| `TWODO_EMAIL` | 2Do 中配置的接收邮箱地址 |
| `SMTP_HOST` | SMTP 服务器地址 |
| `SMTP_PORT` | SMTP 端口（587 为 STARTTLS，465 为 SSL） |
| `SMTP_USER` | SMTP 用户名 |
| `SMTP_PASS` | SMTP 密码（推荐使用[应用专用密码](https://support.google.com/accounts/answer/185833)） |

### 配置 2Do App

1. 购买并启用 **Email to 2Do** 插件（iOS/Mac 应用内购买）
2. 在 2Do 设置 > Email to 2Do > Add Account 中添加邮箱
3. 配置捕获规则（推荐设置特定发件人规则）

详细指南参考 [2Do Email to 2Do 知识库](https://www.2doapp.com/kb/category/ios/email-to-2do/44/)。

## 开发

```bash
# 安装依赖
pnpm install

# 运行测试
pnpm test

# 构建
pnpm build

# 类型检查
pnpm typecheck
```

## License

[MIT](LICENSE)
