# AGENTS / Project Guidelines

This repository is a fork of [dgongut/docker-controller-bot](https://github.com/dgongut/docker-controller-bot).

## Key Project Rules
- **Donate Feature**: `/donate` and `/donors` commands are intentionally removed from this fork.
- **Telemetry Policy**: Anonymous usage statistics must remain disabled by default in `store.py` (`"telemetry": False`) and `compose.yaml` (`TELEMETRY=false`).
- **Upstream Sync**: Upstream remote is `https://github.com/dgongut/docker-controller-bot.git`. Updates should preserve feature removals and default telemetry disabled.
- **Rules Reference**: Detailed rule instructions for AGY are located in `.agents/rules/upstream-sync.md`.
