# resume

Minimalistic cli to manage your claude & codex sessions in one place.

https://github.com/user-attachments/assets/ad007fed-744a-4595-a548-85a071793054

[![PyPI version](https://img.shields.io/pypi/v/pennyroyaltea-resume.svg)](https://pypi.org/project/pennyroyaltea-resume/)
[![Homebrew tap](https://img.shields.io/badge/Homebrew-pennyroyaltea%2Ftap-FBB040?logo=homebrew&logoColor=white)](https://github.com/PennyroyalTea/homebrew-tap)

`resume` reads local session metadata from `~/.codex` and `~/.claude`, shows a single sorted picker, then dispatches to the matching CLI:

```sh
codex resume <session-id>
claude --resume <session-id>
```

## Install

GitHub Releases via curl:

```sh
mkdir -p ~/.local/bin
curl -fsSL https://github.com/PennyroyalTea/resume/releases/latest/download/resume -o ~/.local/bin/resume
chmod +x ~/.local/bin/resume
```

Homebrew:

```sh
brew install pennyroyaltea/tap/resume
```

PyPI via pipx:

```sh
pipx install pennyroyaltea-resume
```

## Usage

```sh
resume                    # merged Codex + Claude picker
resume --last             # resume the most recent merged session
resume --provider codex   # only Codex sessions
resume --provider claude  # only Claude sessions
resume around world       # filter sessions by words
resume --fork             # fork selected session instead of resuming
resume --dry-run          # print the command instead of running it
resume --plain            # use the numbered prompt
resume --version          # print the installed version
```

In the built-in picker:

```text
Enter: resume selected   /: filter   up/down or j/k: move   q: quit
```

## Dependencies & Security

No third-party Python dependencies. The script uses Python's standard library.

Runtime expectations:

- `python3`
- `codex` and/or `claude`
- optional: `fzf`, only when using `--fzf`

The script imports only Python standard library modules. It reads local session files and executes either `codex` or `claude` from `PATH` for the selected session.

## Release

Releases are tag-driven:

```sh
git tag v0.1.0
git push origin v0.1.0
```

CI validates the script on every push and pull request. Tags matching `v*` create a GitHub Release with `resume` and `resume.sha256`.
