# Sector Cycle Notifier

A tiny public notification relay for **Sector Cycle Agent**.

It uses GitHub Actions to send signed messages to a Feishu custom bot. No server is required.

## Secrets

In this repository, open:

`Settings -> Secrets and variables -> Actions -> New repository secret`

Create:

- `FEISHU_WEBHOOK_URL` — Feishu custom bot webhook URL
- `FEISHU_BOT_SECRET` — Feishu custom bot signing secret

Never commit either secret to this repository.

## Manual test

Open:

`Actions -> Feishu Notify -> Run workflow`

Example:

- **Notification title**: `Sector Cycle Agent`
- **Notification message**: `飞书通知链路测试：GitHub Actions -> 飞书`
- **Level**: `info`

Supported levels:

- `info`
- `opportunity`
- `risk`
- `close`

## Role in the architecture

```text
Sector Cycle Agent
       |
       | trigger notification
       v
GitHub Actions (this repo)
       |
       | signed HTTPS POST
       v
Feishu custom bot
```

This repository is intentionally public and contains **no Sector Cycle research data, webhook URL, or bot secret**.
