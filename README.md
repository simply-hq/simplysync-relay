# SimplySync Relay

Host a personal, end-to-end-encrypted Simply Finance sync relay in your own
Cloudflare account. You do not need a domain, VPS, Docker, private network, or
server-administration experience.

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/simply-hq/simplysync-relay/tree/main/apps/relay-cloudflare)

Cloudflare creates the Worker, D1 database, and R2 bucket and gives you a public
`https://…workers.dev` address. Add that address under **Simply Finance →
Settings → Sync Relays**.

## Ask an AI agent

Open this repository in ChatGPT/Codex or Claude Code and say:

```text
Host my own SimplySync relay.
```

The repo-owned `host-relay` skill handles local tooling, Cloudflare signup or
authentication, resource provisioning, migrations, deployment, and health
verification. You only take over when Cloudflare needs credentials, MFA,
CAPTCHA, payment details, or acceptance of terms. Enter sensitive information
directly on Cloudflare; never paste it into chat.

## Why the public address is safe

Simply Finance encrypts events and attachment chunks on-device. The relay never
receives the recovery phrase or decryption key. Each owner also has a private,
recovery-phrase-derived write capability.

The template adds request and write rate limits, size caps, a global owner cap,
per-owner storage quotas, blob hash verification, and a read-only kill switch.
Cloudflare's managed DDoS protection applies automatically.

Keep the built-in relay enabled until you have verified a real two-device sync
and restore through your new relay.

## Development

The deployable template is in [`apps/relay-cloudflare`](apps/relay-cloudflare).

```bash
cd apps/relay-cloudflare
npm install
npm run typecheck
npx wrangler deploy --dry-run
```

For the beginner walkthrough, see
[simplyfinance.app/learn-self-host-cloudflare](https://simplyfinance.app/learn-self-host-cloudflare).
