# CLAUDE.md

Personal fork of kickstart.nvim. Everything lives in `init.lua`, apart from the
optional modules under `lua/kickstart/plugins/` and `lua/custom/plugins/`.
Plugins are managed by the built-in `vim.pack`, not lazy.nvim.

## Keep the README's keymaps current

`README.md` has a `## Keymaps` section documenting the shortcuts this config
adds and the plugin defaults worth knowing.

**Whenever you add, remove, or change a keymap, user command, or a formatting /
save-time behaviour, update that section in the same change.** A keymap that
only exists in `init.lua` is a keymap nobody remembers. This is not optional
follow-up work: the commit that changes the mapping is the commit that updates
the README.

Rules for the section:

- New shortcuts this config defines go in the **Added by this config** table.
  Plugin or Neovim defaults go in the relevant area table below it.
- Say what the key does, not how it is implemented, and keep rows one line.
- When a mapping shadows a useful default (`J` for join, `K` for hover), say so
  in the prose under the table, so the trade-off is not rediscovered painfully.
- Delete rows for mappings that are gone. A stale row is worse than none.

Verify against the running config rather than trusting the source, since
plugins add mappings of their own:

```bash
nvim --headless '+lua local r={} for _,m in ipairs(vim.api.nvim_get_keymap("n")) do if m.desc then r[#r+1]=m.lhs.."\t"..m.desc end end table.sort(r) print(table.concat(r,"\n"))' +qa
```

Buffer-local mappings (LSP, gitsigns) only appear when a relevant buffer is
open, so pass a real file and use `nvim_buf_get_keymap`. Mappings without a
`desc` (a few of kickstart's) will not show up in that dump.

## Conventions

- Match the surrounding style: two-space indent, single-quoted Lua strings,
  `vim.keymap.set` with a `desc`, comments that explain why rather than what.
- Prefer what is already installed. `mini.nvim`, Telescope, gitsigns and conform
  cover a lot; reach for a new plugin only when they genuinely cannot.
- Verify changes by running Neovim, not by reasoning about the config. Note that
  `--headless` disables auto-session and cannot host a terminal UI, so features
  like the lazygit float need a real pty to test.
