# My Neovim config

Built on top of kickstart.nvim.

## Keymaps

`<leader>` is `<Space>`. Everything here is defined in `init.lua`, or comes from
Neovim and the plugins it installs. `<leader>sk` searches all live keymaps, and
`which-key` shows what follows any prefix you have started typing.

### Added by this config

| Key | Does |
| --- | --- |
| `<leader>fs` | Save this file (only writes when modified) |
| `<leader>S` | Save every changed file |
| `<leader>w` | Close this buffer, leaving Neovim open |
| `<leader>W` | Close every other buffer |
| `<Tab>` / `<S-Tab>` | Next / previous buffer |
| `<leader>y` | Yank `path:line`, or `path:12-15` from a selection |
| `<leader>d` | Jump to the next diagnostic, wrapping |
| `J` / `K` | Down / up 5 lines, in normal and visual mode |
| `<C-->` | Jump back, same as `<C-o>` |
| `<C-h/j/k/l>` | Move focus between splits |
| `gd` | Go to definition (alias for `grd`) |
| `gh` | Hover documentation |
| `<leader>gg` | lazygit in a floating window |
| `<leader>gd` | lazydocker in a floating window |
| `<leader>mp` / `:MdPreview` | Render this Markdown file, Mermaid included, in the browser |
| `<leader>mc` | Toggle centring text at 120 columns |

Trade-offs worth remembering: `J` replaces join-lines (use `gJ`), `K` replaces
LSP hover (now `gh`), and `<Tab>` is only distinct from `<C-i>` in terminals
speaking the kitty keyboard protocol, such as Ghostty.

### Files and search (Telescope, neo-tree)

| Key | Does |
| --- | --- |
| `<leader>sf` | Search files |
| `<leader>sg` | Search by grep across the project |
| `<leader>sw` | Search the word under the cursor |
| `<leader>sd` | Search diagnostics |
| `<leader>sr` | Resume the last picker |
| `<leader>s.` | Recent files |
| `<leader>sh` / `<leader>sk` | Search help / keymaps |
| `<leader>sn` | Search files in the Neovim config |
| `<leader><leader>` | Open buffers |
| `<leader>/` | Fuzzy find in this buffer |
| `<C-v>` / `<C-x>` / `<C-t>` | In a picker: open in vsplit / split / tab |
| `<C-/>` or `?` | In a picker: show its own mappings |
| `\` | Reveal the current file in neo-tree, or close it |
| `s` / `S` / `t` / `w` | In neo-tree: open in vsplit / split / tab / picked window |

### Code (LSP, diagnostics, formatting)

| Key | Does |
| --- | --- |
| `grd` / `gd` | Go to definition |
| `grD` | Go to declaration |
| `grt` | Go to type definition |
| `grr` / `gri` | References / implementations |
| `gra` | Code action |
| `grn` | Rename symbol |
| `gO` / `gW` | Document / workspace symbols |
| `<leader>th` | Toggle inlay hints |
| `<leader>q` | All diagnostics into a quickfix list |
| `[d` / `]d` | Previous / next diagnostic |
| `<C-w>d` | Show the diagnostic under the cursor |
| `<leader>f` | Format the buffer now |

Formatting also happens on save: Biome in projects with a `biome.json`, the
project's Prettier otherwise.

### Git (gitsigns)

| Key | Does |
| --- | --- |
| `]c` / `[c` | Next / previous changed hunk, unstaged only |
| `<leader>hs` / `<leader>hr` | Stage / reset the hunk, or the selection |
| `<leader>hS` / `<leader>hR` | Stage / reset the whole buffer |
| `<leader>hp` / `<leader>hi` | Preview the hunk in a float / inline |
| `<leader>hb` | Full blame for this line |
| `<leader>tb` | Toggle the per-line blame annotation |
| `<leader>tw` | Toggle intra-line word diff |
| `<leader>hd` / `<leader>hD` | Diff against the index / last commit |
| `<leader>hq` / `<leader>hQ` | Hunks to quickfix: this file / whole repo |
| `ih` | Hunk text object, as in `dih` or `vih` |

Bright gutter signs are unstaged, muted ones staged.

### Editing (mini.ai, mini.surround, treesitter)

| Key | Does |
| --- | --- |
| `gcc` / `gc{motion}` | Toggle comment for the line / motion, `gc` in visual mode |
| `sa{motion}{char}` | Add a surrounding, e.g. `saiw)` |
| `sd{char}` / `sr{old}{new}` | Delete / replace a surrounding |
| `va)` `vi"` `dii` | mini.ai text objects; `aa` and `ii` target the *next* one |
| `an` / `in` | Select the parent / child treesitter node |
| `]n` / `[n` | Next / previous treesitter node |
| `]N` / `[N` | Next / previous sibling node |
| `[<Space>` / `]<Space>` | Add an empty line above / below |
| `gx` | Open the URL or path under the cursor |
| `<Esc>` | Clear the search highlight |
| `<Esc><Esc>` | Leave terminal mode |

### Sessions (auto-session)

Sessions are saved per directory, buffers and split layout included.

| Command | Does |
| --- | --- |
| `:qa` | Quit; the layout is saved |
| `nvim` | In that directory again, restores it. `nvim file.ts` skips the restore |
| `:SessionSearch` | Pick a saved session |
| `:AutoSession save` / `delete` | Snapshot without quitting / drop this session |

