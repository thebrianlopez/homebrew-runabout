# thebrianlopez/runabout

Homebrew tap for the **runabout** CLI suite — developer tools for shell productivity, content intelligence, and workflow automation.

---

## Install

### macOS

```bash
brew install thebrianlopez/runabout/runabout
```

Installs all 14 binaries to your PATH. Upgrade any time with:

```bash
brew upgrade thebrianlopez/runabout/runabout
```

For tree-sitter-based Go source analysis (macOS only — CGo required):

```bash
brew install thebrianlopez/runabout/ts-go
```

---

### Linux

[Homebrew on Linux](https://docs.brew.sh/Homebrew-on-Linux) is fully supported:

```bash
# Install Homebrew if needed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Tap and install
brew install thebrianlopez/runabout/runabout
```

> `ts-go` is macOS-only. On Linux, install from source:
> ```bash
> go install github.com/thebrianlopez/runabout/cmd/ts-go@latest
> ```

**Prefer raw binaries?** Download directly from [releases](https://github.com/thebrianlopez/runabout/releases/latest) — `linux_amd64` and `linux_arm64` archives available.

---

### Windows

No native Windows builds. Use [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install) and follow the Linux instructions inside your WSL environment.

```powershell
# In PowerShell (one-time WSL setup)
wsl --install
```

Then inside WSL:

```bash
brew install thebrianlopez/runabout/runabout
```

---

### Android (Termux)

Install [Termux from F-Droid](https://f-droid.org/packages/com.termux/) (not the Play Store — that version is outdated), then:

```bash
# Download the linux_arm64 release directly — no Go toolchain needed
pkg install curl jq

VERSION=$(curl -s https://api.github.com/repos/thebrianlopez/runabout/releases/latest | jq -r .tag_name)
curl -fsSL \
  "https://github.com/thebrianlopez/runabout/releases/download/${VERSION}/runabout_${VERSION#v}_linux_arm64.tar.gz" \
  | tar xz -C "$PREFIX/bin"
```

Or install from source if you prefer:

```bash
pkg install golang
go install github.com/thebrianlopez/runabout/cmd/...@latest
```

> Note: `ts-go` requires CGo and cannot be built in Termux without a cross-toolchain. The other 14 tools are pure Go and install cleanly.

---

## What you get

| Tool | What it does |
|------|-------------|
| `mdq` | Query fields, tables, and headings across markdown files |
| `bmux` | Remote tmux session manager over SSH |
| `workctl` | Fetch and export Atlassian & GitHub work data — weekly summaries, career reports |
| `ghwatch` | Stream GitHub repository activity to the terminal (push, PRs, workflow runs) |
| `linkari` | Android/Chrome share → AI triage scoring webhook server |
| `runway` | JD match intelligence — score resumes against job descriptions |
| `wasend` | Send WhatsApp messages from the command line |
| `perfgate` | Statistical before/after performance gating for benchmarks |
| `shellprof` | Fish shell function profiler with call graphs |
| `hookval` | Validate Claude Code hook signal schema |
| `effiscore` | Claude API efficiency scoring via Datadog metrics |
| `protonexport` | Export ProtonMail conversations to markdown |
| `jira-poller` | Jira issue change poller with SQLite dedup |
| `ts-go` *(macOS)* | Tree-sitter structural Go analysis — signatures, types, body extraction |

---

## Shell completions

`linkari` and `bmux` generate completions for your shell:

```bash
# Fish
linkari completion fish > ~/.config/fish/completions/linkari.fish
bmux completion fish > ~/.config/fish/completions/bmux.fish

# Zsh
linkari completion zsh > "${fpath[1]}/_linkari"
bmux completion zsh > "${fpath[1]}/_bmux"

# Bash
linkari completion bash > /etc/bash_completion.d/linkari
bmux completion bash > /etc/bash_completion.d/bmux
```

---

## Requirements

| Platform | Requirement |
|----------|-------------|
| macOS | 12.0+ (Monterey or later) |
| Linux | glibc 2.17+ (most distros since 2013) |
| Windows | WSL2 with a Linux distro |
| Android | Termux from F-Droid |
| `ts-go` | macOS only — CGo + Xcode CLT |

---

## Build from source

Requires Go 1.26+:

```bash
git clone https://github.com/thebrianlopez/runabout
cd runabout
make install   # installs all tools to ~/go/bin/
```

---

## Source

[github.com/thebrianlopez/runabout](https://github.com/thebrianlopez/runabout)
