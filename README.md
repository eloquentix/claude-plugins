# metals-lsp

A Claude Code plugin that integrates [Metals](https://scalameta.org/metals/), the Scala language server, for code intelligence, refactoring, and analysis.

## Prerequisites

Install the Metals LSP binary:

```bash
# Via Coursier (recommended)
cs install metals

# Or via Homebrew
brew install scalameta/tap/metals
```

## Installation

Load the plugin when starting Claude Code:

```bash
claude --plugin-dir /path/to/metals-lsp
```

Or add it as a local marketplace for permanent installation:

```bash
# Inside Claude Code:
/plugin marketplace add /path/to/metals-lsp
/plugin install metals-lsp
```

## Supported file types

| Extension | Language |
|-----------|----------|
| `.scala`  | Scala    |
| `.sc`     | Scala    |
| `.sbt`    | sbt      |

## Troubleshooting

If Metals isn't responding or indexing fails, try resetting the workspace:

1. Delete caches:
   ```bash
   rm -rf .metals/ .bloop/ .bsp/metals.json
   ```
2. Regenerate Bloop project files:
   ```bash
   sbt bloopInstall
   ```
3. Trigger compilation by issuing any LSP request (e.g. hover or documentSymbol) — Metals then connects to Bloop, indexes the workspace (~22s), and compiles all sources (~71s total).

## Features

Once installed, Claude Code gains LSP-powered capabilities for Scala projects:

- Diagnostics (compiler errors and warnings)
- Hover information (types, documentation)
- Go-to-definition
- Find references
- Code completions
