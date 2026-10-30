# Upstream Sync & Fork Rules

## Repository Metadata
- **Origin**: `git@github.com:armand0w/docker-controller-bot.git`
- **Upstream**: `https://github.com/dgongut/docker-controller-bot.git`

## Fork Specifications & Scope
- **Removed Features**: `/donate` and `/donors` commands in `src/commands.py`, helper functions (`print_donors`, `get_array_donors_online`) in `src/core.py`, command registration in `src/core.py`, `DONORS_URL` in `src/config.py`, and mentions in README files.
- **Telemetry Configuration**: Anonymous statistics are disabled by default in `src/store.py` (`DEFAULTS["bot"]["telemetry"] = False`) and in `compose.yaml` (`TELEMETRY=false`).
- **Policy**:
  - NEVER re-introduce `/donate` or `/donors` handlers into `src/commands.py`, `src/core.py`, `src/config.py`, or documentation.
  - Keep telemetry disabled by default.

## Upstream Update Procedure for AGY
When asked to update this codebase from upstream:
1. Ensure the `upstream` remote is configured:
   `git remote add upstream https://github.com/dgongut/docker-controller-bot.git` (if not already added).
2. Sync upstream changes via `gh repo sync armand0w/docker-controller-bot --branch main` or `git fetch upstream`.
3. Merge or rebase changes into the working branch.
4. Verify and maintain feature removals:
   - Check `src/commands.py` does not contain `cmd_donate`, `cmd_donors` or their mappings.
   - Check `src/core.py` does not contain `print_donors`, `get_array_donors_online`, or `/donate`/`/donors` in command lists.
   - Check `src/config.py` does not contain `DONORS_URL`.
   - Check `src/store.py` has `"telemetry": False`.
   - Check `compose.yaml` includes `TELEMETRY=false`, `py3-paramiko openssh-client`, and the config volume mount (`./config:/app/config`).
5. Test python files for syntax validity (`python3 -m py_compile src/*.py dev/*.py tests/*.py`).
