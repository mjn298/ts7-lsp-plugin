# ts7-lsp

TypeScript/JavaScript language server for Claude Code backed by the **native TypeScript 7**
language server (`typescript@rc`).

This is a local alternative to the official `typescript-lsp` plugin, which launches the
Node-based `typescript-language-server` (a wrapper around the classic `tsserver`). TypeScript 7
is the native Go rewrite and implements LSP directly — no wrapper — so it starts faster and
uses less memory. It is still a **release candidate**: some refactors, completions, and
tsserver-plugin features may be incomplete.

> Naming note: the pre-RC nightlies shipped as `@typescript/native-preview` with a binary
> called `tsgo`. As of the 7.0 RC the package is just `typescript@rc` and the binary is
> **`tsc`**, which gained an `--lsp` mode. This plugin launches `tsc --lsp --stdio`.

## Supported Extensions
`.ts`, `.tsx`, `.js`, `.jsx`, `.mts`, `.cts`, `.mjs`, `.cjs`

## Prerequisite: install the TypeScript 7 RC

The plugin launches `tsc --lsp --stdio`, so a TypeScript 7 `tsc` must be on your `PATH`.

```bash
# global install (use your package manager of choice):
pnpm add -g typescript@rc
# or: npm install -g typescript@rc

# verify it's TS7 and speaks LSP:
tsc --version        # -> Version 7.x
tsc --lsp --help     # -> prints "Usage of lsp:"
```

> Note: `tsc` resolves to whichever copy is first on your `PATH`. Make sure that copy is
> TS7 — an older global TypeScript (5.x/6.x) does **not** support `--lsp` and will fail.

## Enable

```bash
# 1. Register this local marketplace (point at the plugin root, not the manifest):
/plugin marketplace add /path/to/ts7-lsp-plugin

# 2. Install the plugin:
/plugin install ts7-lsp@ts7-lsp-marketplace

# 3. Disable the official Node-based server so the two don't both claim TS files:
/plugin disable typescript-lsp@claude-plugins-official
```

Run `/reload-plugins` (or restart Claude Code) after enabling so the LSP host picks up the
launch command.

## Switching back

```bash
/plugin disable ts7-lsp@ts7-lsp-marketplace
/plugin enable typescript-lsp@claude-plugins-official
```

## More Information
- [Announcing TypeScript 7.0 RC](https://devblogs.microsoft.com/typescript/announcing-typescript-7-0-rc/)
- [microsoft/typescript-go](https://github.com/microsoft/typescript-go)
