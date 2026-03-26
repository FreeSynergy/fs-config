# CLAUDE.md – fs-config

## What is this?

FreeSynergy Config — TOML configuration loader and saver with schema validation,
auto-repair, and backup support. Used by all FreeSynergy programs to load and
persist their configuration files.

## Rules

- Language in files: **English** (comments, code, variable names)
- Language in chat: **German**
- OOP everywhere: traits over match blocks, types carry their own behavior
- No CHANGELOG.md
- After every feature: commit directly

## Architecture

- `ConfigLoader` — file-based TOML loader/saver with base-dir resolution and `.bak` backup
- `FeatureFlags` — JSON-based runtime feature flags
- `ConfigSchema` / `FieldSchema` / `FieldKind` — declarative schema description
- `SchemaValidator` — validates `toml::Value` against a `ConfigSchema`
- `TomlRepair` — suggests and applies repair actions for schema violations
- `load_toml` / `save_toml` / `parse_str` — standalone helpers for one-off use

## Dependencies

- **fs-libs** (`../fs-libs/`) — `fs-error` (FsError, Repairable, RepairOutcome, etc.)

## Config path convention

Config files are stored under `~/.config/fsn/<program>.toml`
