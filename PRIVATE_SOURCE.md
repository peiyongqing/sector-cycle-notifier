# Private Source Integration

The notifier polls a private Sector Cycle outbox every 5 minutes.

## Additional secret

Create one more repository secret in this **public notifier** repository:

- `SOURCE_REPO_TOKEN`

Use a **fine-grained personal access token** restricted to:

- Repository: `peiyongqing/sector-cycle-agent`
- Repository permissions: **Contents: Read-only**

The token does not need Actions, Issues, Pull Requests, or administration permissions.

## Privacy model

- Private message body stays in `peiyongqing/sector-cycle-agent/notifications/pending.json`.
- This public repository reads the private file at runtime.
- The message body is not committed here.
- Only `state/last-sent-id.txt` is persisted publicly to prevent duplicate sends.
- Feishu webhook and bot secret remain GitHub Actions Secrets.

## Runtime

`Sector Cycle Push` runs every 5 minutes. If the private outbox has a new `id` and `send=true`, it sends that event to Feishu once.
