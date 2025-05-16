# Leadr

**Leadr** is a customizable CLI shortcut manager inspired by the leader key concept in (Neo)Vim.
Use memorable key sequences to quickly execute or insert commands in your terminal.

## ⚡️ Requirements

- bash or zsh
- [crossterm](https://docs.rs/crossterm/latest/crossterm/index.html) compatible terminal (see [their Readme for a list](https://github.com/crossterm-rs/crossterm?tab=readme-ov-file#tested-terminals))

Note: `leadr` works best inside a `tmux` session since it can utilize `tmux`'s `send-keys` to execute commands.
Outside of `tmux`, `leadr` will fallback to `eval` and manually appending the command to the shell's history.

## 📦 Installation

<details>
<summary>From pre-built binaries</summary>

You can download pre-built binaries from the [releases page](https://github.com/ll-nick/leadr/releases/latest).
Just copy the binary to a directory in your `PATH`, e.g. using the following command:
```bash
curl -L https://github.com/ll-nick/leadr/releases/latest/download/leadr -o ~/.local/bin/leadr
chmod +x ~/.local/bin/leadr
```

</details>

<details>
<summary>From crates.io</summary>

You can install `leadr` using cargo:
```bash
cargo install leadr
```
This will install the latest version of `leadr` from [crates.io](https://crates.io/crates/leadr).

</details>

<details>
<summary>From source</summary>

You can build `leadr` from source using cargo:

```bash
git clone https://github.com/ll-nick/leadr.git
cd leadr
cargo install --path .
```

</details>

## 🐚 Shell Integration

To use `leadr`, simply add the following line to your shell configuration file (e.g. `~/.bashrc` or `~/.zshrc`):

```bash
# For bash
source <(leadr --bash)
```

```zsh
# For zsh
source <(leadr --zsh)
```

## 🛠️ Configuration and Usage

`leadr` will automatically create a configuration file and fill it with some default shortcuts the first time you run it.
See [confy's Readme](https://github.com/rust-cli/confy?tab=readme-ov-file#config-file-location) for the location of the configuration file.

For a list of all available commands, run:
```bash
leadr --list
```

With the default config, you can e.g. execute `git status` by pressing `<Ctrl-Space>` followed by `gs`.
Similarly, you can pre-populate `git commit -m "` by pressing `<Ctrl-Space>` followed by `gc`.

Modify the configuration file to add your own shortcuts or adjust the `leadr` keybinding.
For a list of currently supported keybindings, see [src/keymap.rs](src/keymap.rs).

You can print the currently typed key sequence by setting `print_sequence = true`.
Be aware though that this is somewhat experimental and might lead to issues.
