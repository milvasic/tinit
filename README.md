# tinit

A single-file Bash CLI that sets up a Debian/Ubuntu terminal environment from scratch.

Run once on a fresh machine to get a fully configured zsh shell with a curated set of tools and plugins.

## What it sets up

- **Base packages** — `curl`, `git`, `zsh`, `ncdu`
- **oh-my-zsh** — framework for managing zsh configuration
- **zsh as default shell** — replaces bash
- **~/.zshrc** — pre-configured with [zinit](https://github.com/zdharma-continuum/zinit), plugins, and aliases
- **Zinit plugins** — [spaceship-prompt](https://github.com/spaceship-prompt/spaceship-prompt), [fast-syntax-highlighting](https://github.com/zdharma-continuum/fast-syntax-highlighting), [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions), [zsh-completions](https://github.com/zsh-users/zsh-completions)
- **~/.config/.spaceshiprc.zsh** — spaceship prompt configuration
- **[motd](https://github.com/milvasic/motd)** — message of the day on shell login
- **[mcli](https://github.com/milvasic/mcli)** — Docker Compose service manager

## Install

```sh
bash -c "$(curl -fsSL https://raw.githubusercontent.com/milvasic/tinit/refs/heads/main/install.sh)"
```

This places the `tinit` binary in `/usr/local/bin`. If a previous version is already installed, the installer will prompt you to upgrade.

For non-interactive environments (CI, scripts), pass `--yes` to auto-approve upgrades:

```sh
bash -c "$(curl -fsSL https://raw.githubusercontent.com/milvasic/tinit/refs/heads/main/install.sh)" -- --yes
```

`wget` is also supported if `curl` is not available.

## Uninstall

```sh
bash -c "$(curl -fsSL https://raw.githubusercontent.com/milvasic/tinit/refs/heads/main/install.sh)" -- --uninstall
```

This removes `tinit` from `/usr/local/bin`.

## Usage

### First-time setup

```sh
tinit ensure-tools
```

Installs all packages, oh-my-zsh, sets zsh as the default shell, writes config files, and installs motd and mcli.

### Update config files only

```sh
tinit ensure-config
```

Re-writes `~/.zshrc` and `~/.config/.spaceshiprc.zsh` (backs up existing files first). Safe to re-run at any time.

### Self-update the binary

```sh
bash -c "$(curl -fsSL https://raw.githubusercontent.com/milvasic/tinit/refs/heads/main/install.sh)" -- --yes
```

### Other commands

```sh
tinit version   # print version
tinit help      # show usage
```

Both commands are idempotent — steps already done are skipped, and existing config files are backed up before overwriting.

After running `ensure-tools`, restart your terminal or log out and back in to activate zsh.

## Requirements

- Debian or Ubuntu (requires `apt`)
- `curl` for the install one-liner

## Contributing

Issues and pull requests are welcome. Please keep changes minimal and focused.

## License

[MIT](LICENSE)
