# Gippy

Gippy is a Python tool and library that syncs a local folder to a GitHub repository and keeps it updated. It watches for file changes and automatically commits + pushes updates when you save files.

## Features

- Initialize or connect a folder to a GitHub repo
- One-shot syncs for CI or manual runs
- Continuous watch mode with auto-commit and auto-push
- Configurable commit messages, branch, and ignore patterns

## Requirements

- Python 3.9+
- `git` installed and available on your PATH
- GitHub repository access (SSH key or HTTPS token)

## Installation

```bash
pip install gippy
```

## Quick start

```bash
# Initialize and connect a folder to a GitHub repo
gippy init --repo-path . --remote git@github.com:your-org/your-repo.git

# One-time sync
gippy sync --repo-path .

# Watch for changes and auto-sync
gippy watch --repo-path .
```

## CLI commands

### `gippy init`

Initializes a git repository (if missing) and sets the remote.

```bash
gippy init --repo-path /path/to/folder --remote git@github.com:your-org/repo.git --branch main
```

### `gippy sync`

Stages, commits, and pushes any changes.

```bash
gippy sync --repo-path /path/to/folder --message "Auto-sync" --branch main
```

### `gippy watch`

Runs a file watcher and syncs on changes.

```bash
gippy watch --repo-path /path/to/folder --message "Auto-sync" --branch main
```

## Library usage

```python
from gippy.sync import sync_once, watch

sync_once(repo_path=".", remote_url="git@github.com:your-org/repo.git")

watch(repo_path=".", remote_url="git@github.com:your-org/repo.git")
```

## Configuration

You can pass options via CLI flags or library arguments:

- `repo_path`: local folder to sync
- `remote_url`: GitHub repository URL
- `branch`: branch to push to
- `commit_message`: message used for auto-commits
- `ignore`: list of glob patterns to ignore

## License

MIT License. See [LICENSE](LICENSE).
