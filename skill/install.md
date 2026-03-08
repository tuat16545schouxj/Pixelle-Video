## Install Pixelle-Video Skill

Please follow these steps **exactly in order**. This project uses `uv` to manage Python and all dependencies — do NOT use system Python, pip, conda, or pyenv.

### Step 1: Install uv

`uv` automatically handles Python version and all dependencies. No need to install Python separately.

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env  # or restart your shell
```

Verify: `uv --version` should print a version number.

### Step 2: Clone the repository

```bash
git clone -b dev_skills https://github.com/AIDC-AI/Pixelle-Video.git
cd Pixelle-Video
```

### Step 3: Install dependencies

```bash
uv sync
```

This will automatically download the correct Python version (3.11+) and install all packages. No manual Python installation needed.

### Step 4: Start the API server

```bash
uv run python api/app.py &
```

Wait a few seconds for startup, then verify:

```bash
uv run python skill/pixelle.py health
```

If it prints "API is running." — installation is complete.

### Step 5: Quick test

```bash
uv run python skill/pixelle.py generate "The history of the Roman Empire"
```

This returns a task ID. Check progress with:

```bash
uv run python skill/pixelle.py status <task_id>
```

When status is "completed", the video URL will be shown.

### Important

- **All commands must use `uv run python` instead of `python`**. This ensures the correct Python version and dependencies are used.
- Do NOT attempt to install Python manually or use system Python.
- Read `skill/SKILL.md` for all available commands.