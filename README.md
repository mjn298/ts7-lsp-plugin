# ts7-lsp-plugin

A [Claude Code](https://claude.com/claude-code) marketplace that provides a TypeScript
language server backed by the **native TypeScript 7** server (`typescript@rc`), launched as
`tsc --lsp --stdio`.

It replaces the official `typescript-lsp` plugin (which uses the Node-based
`typescript-language-server` wrapper around the classic `tsserver`) with the faster native
Go implementation.

> **Unofficial.** This is a community project and is **not** affiliated with, endorsed by, or
> maintained by Microsoft or the TypeScript team. "TypeScript" and `tsc` are products of
> Microsoft; this repo just wires the `typescript@rc` LSP into Claude Code. Provided as-is.

## Layout

```
.claude-plugin/marketplace.json   # marketplace "ts7-lsp-marketplace" → plugin "ts7-lsp"
plugins/ts7-lsp/README.md         # install + enable instructions
```

## Quick start

```bash
npm install -g typescript@rc                       # a TS7 `tsc` on PATH — any package manager works
/plugin marketplace add mjn298/ts7-lsp-plugin      # add this marketplace straight from GitHub
/plugin install ts7-lsp@ts7-lsp-marketplace
/plugin disable typescript-lsp@claude-plugins-official   # ONLY if you'd already installed the official TS LSP
/reload-plugins
```

> `mjn298/ts7-lsp-plugin` is shorthand for this GitHub repo. You can also pass the full URL
> (`https://github.com/mjn298/ts7-lsp-plugin`), or a local checkout path if you're hacking on it.

See [`plugins/ts7-lsp/README.md`](plugins/ts7-lsp/README.md) for full details and the
switch-back instructions.
