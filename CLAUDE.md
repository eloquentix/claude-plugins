# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Claude Code plugin that integrates the [Metals](https://scalameta.org/metals/) Scala language server. It is a configuration-only plugin with no build system, tests, or source code — just JSON manifests and documentation.

## How the Plugin Works

The plugin declares an LSP server in `.lsp.json` (at the plugin root). Claude Code uses this to launch the external `metals` binary via stdio and route LSP requests for `.scala`, `.sc`, and `.sbt` files. The Metals binary must be installed separately (`cs install metals` or `brew install scalameta/tap/metals`).

## Making Changes

- **LSP server config** — `.lsp.json` (plugin root): command, args, transport, `extensionToLanguage` mappings, `initializationOptions`, `startupTimeout` (currently 90s), `maxRestarts`
- **Plugin metadata** — `.claude-plugin/plugin.json`: name, version, description, author, keywords
- **Marketplace entry** — `.claude-plugin/marketplace.json`: local marketplace definition for `/plugin marketplace add`
