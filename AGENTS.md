# Repository Guidelines

This public repository contains the standalone Cloudflare deployment template
for the SimplySync relay and the shared `host-relay` agent skill.

- Keep `apps/relay-cloudflare` independently installable; Deploy to Cloudflare
  treats that subdirectory as a new repository root.
- Preserve the existing SimplySync HTTP contract and ciphertext-only threat
  model. Never add readable finance fields or receive recovery phrases.
- Run `npm install`, `npm run typecheck`, and
  `npx wrangler deploy --dry-run` from `apps/relay-cloudflare` after changes.
- Keep `.agents/skills/host-relay` usable by ChatGPT/Codex and the
  `.claude/skills/host-relay` symlink usable by Claude Code.
