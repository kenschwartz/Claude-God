# AGENTS

Claude God: Ken's fork of the Claude usage-monitor macOS app (Swift/SwiftUI). Development guidelines live in [CLAUDE.md](CLAUDE.md). This file carries repo-local agent rules that are not upstream (kept here to avoid conflicts when syncing the upstream Lcharvol/Claude-God repo).

## Doc frontmatter

Markdown files in this repo may carry YAML frontmatter (title, status,
project, tags, maps). It feeds an Obsidian vault that mirrors these docs.

- PRESERVE it when editing. Do not strip it. Do not reformat it.
- New docs should include it. Copy the shape from a sibling doc.
- `maps:` values are Obsidian wikilinks. They look inert here. They are not
  dead - leave them alone.

## Links in docs

Use relative markdown links: [design](./docs/DESIGN.md)
NEVER use [[wikilinks]] in this repo. These docs render on GitHub, where
[[foo]] appears as literal text.

## Fork-local code delta

The fork is docs-only EXCEPT one patch (2026-09-01): Sources/UsageManager.swift
re-registers the login item at the end of init() when launchAtLogin is on and the
app runs from /Applications. Upstream only registers on a Settings toggle flip,
so a bundle deploy strands a stale Background Task Management entry and the app
silently stops starting at login. Expect a merge conflict near init's closing
lines when upstream touches init; keep our block.
