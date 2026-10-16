# Upstream Sync & Fork Rules

## Repository Metadata
- **Origin**: `git@github.com:armand0w/docker-controller-bot.git`
- **Upstream**: `https://github.com/dgongut/docker-controller-bot.git`

## Fork Specifications & Scope
- **Removed Features**: `/donate` and `/donors` commands in `commands.py`, helper functions (`print_donors`, `get_array_donors_online`) in `core.py`, command registration in `core.py`, `DONORS_URL` in `config.py`, and mentions in README files.
- **Telemetry Configuration**: Anonymous statistics are disabled by default in `store.py` (`SETTINGS_DEFAULTS["bot"]["telemetry"] = False`) and in `compose.yaml` (`TELEMETRY=false`).
- **Policy**:
  - NEVER re-introduce `/donate` or `/donors` handlers into `commands.py`, `core.py`, `config.py`, or documentation.
  - Keep telemetry disabled by default.

## Upstream Update Procedure for AGY
When asked to update this codebase from upstream:
1. Ensure the `upstream` remote is configured:
   `git remote add upstream https://github.com/dgongut/docker-controller-bot.git` (if not already added).
2. Sync upstream changes via `gh repo sync armand0w/docker-controller-bot --branch main` or `git fetch upstream`.
3. Merge or rebase changes into the working branch.
4. Verify and maintain feature removals:
   - Check `commands.py` does not contain `cmd_donate`, `cmd_donors` or their mappings.
   - Check `core.py` does not contain `print_donors`, `get_array_donors_online`, or `/donate`/`/donors` in command lists.
   - Check `config.py` does not contain `DONORS_URL`.
   - Check `store.py` has `"telemetry": False`.
   - Check `compose.yaml` includes `TELEMETRY=false`, `py3-paramiko openssh-client`, and the config volume mount (`./config:/app/config`).
5. Test python files for syntax validity (`python3 -m py_compile *.py`).
