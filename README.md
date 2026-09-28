# lua-nvim-config

My Neovim configuration. A fork of [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)
kept deliberately close to upstream — single-file `init.lua`, everything documented inline,
with a small set of personal additions rather than a rewrite.

Clones straight to `~/.config/nvim`:

```bash
git clone https://github.com/srirams1003/lua-nvim-config.git \
  "${XDG_CONFIG_HOME:-$HOME/.config}"/nvim
```

Open `nvim` and lazy.nvim installs everything on first launch. `:checkhealth` afterwards.

Upstream's own documentation — install notes, FAQ, how the file is organised — is kept
verbatim in [`KICKSTART.md`](KICKSTART.md).

---

## Requirements

`git`, `make`, `unzip`, a C compiler, [ripgrep](https://github.com/BurntSushi/ripgrep),
and a [Nerd Font](https://www.nerdfonts.com/) (`vim.g.have_nerd_font = true` is set, so
icons are expected).

The language servers this config attaches to are installed by `secondScript.sh` in
[`srirams1003/dotfiles`](https://github.com/srirams1003/dotfiles): pyright,
typescript-language-server, clangd, gopls, and the HTML/CSS servers.

---

## What differs from stock kickstart

Leader is `<Space>`.

### Added plugins — `lua/custom/plugins/`

| File | Plugin | Why |
|---|---|---|
| `filetree.lua` | [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim) | file tree, bound to `<leader>z` |
| `autopairs.lua` | [nvim-autopairs](https://github.com/windwp/nvim-autopairs) | bracket pairing, wired into nvim-cmp so `(` is added after completing a function |

### Custom keymaps

| Key | Does |
|---|---|
| `<leader>z` | toggle Neotree |
| `<leader>x` | `:qa` — quit all |
| `<leader>sc` | toggle spellcheck (prints the new state) |

Plus a mouse toggle, for when you want clean terminal text selection instead of Neovim's
own mouse handling.

Everything else — `<leader>e`, `<leader>q`, `[d`/`]d`, the Telescope and LSP maps — is
stock kickstart; see [`KICKSTART.md`](KICKSTART.md).

### Other settings

- `vim.g.mkdp_browser` — which browser markdown-preview opens. Set per machine; both
  `firefox` and `google-chrome` are in the file with one commented out.
- The optional kickstart modules (`debug`, `indent_line`, `lint`) are left commented out in
  `init.lua`. Uncomment in the plugin list at the bottom to enable them.

---

## Layout

```
init.lua                      # the whole config, kickstart-style
lua/custom/plugins/           # my additions — lazy.nvim picks up everything here
lua/kickstart/plugins/        # upstream optional modules (opt-in)
lua/kickstart/health.lua
doc/kickstart.txt             # upstream :help docs
lazy-lock.json                # plugin lockfile — commit changes after :Lazy update
KICKSTART.md                  # upstream README
```

---

## Related

- [`srirams1003/dotfiles`](https://github.com/srirams1003/dotfiles) — install scripts that set this up
- [`srirams1003/i3-dotfiles`](https://github.com/srirams1003/i3-dotfiles) — i3wm, zsh, tmux, terminal *(private)*

Upstream: [nvim-lua/kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) (MIT, see
[`LICENSE.md`](LICENSE.md)).
