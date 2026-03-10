# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Claude Code plugin that integrates the [Metals](https://scalameta.org/metals/) Scala language server. It is a configuration-only plugin with no build system, tests, or source code — just `plugin.json` and documentation.

## Repository Structure

- `.claude-plugin/plugin.json` — Plugin manifest defining the Metals LSP server configuration (command, file extension mappings, startup timeout)
- `README.md` — Installation and usage instructions
- `LICENSE` — Apache 2.0

## How the Plugin Works

The plugin declares an LSP server entry in `plugin.json` under `lspServers`. Claude Code uses this to launch the external `metals` binary and route LSP requests for `.scala`, `.sc`, and `.sbt` files. The Metals binary must be installed separately (`cs install metals` or `brew install scalameta/tap/metals`).

## Making Changes

Any behavioral changes go into `.claude-plugin/plugin.json`. The schema fields that matter:
- `command` — the binary Claude Code invokes
- `extensionToLanguage` — maps file extensions to LSP language identifiers
- `startupTimeout` — milliseconds to wait for Metals to initialize (currently 120s)
