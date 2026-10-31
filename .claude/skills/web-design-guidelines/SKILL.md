---
name: web-design-guidelines
description: Review UI code for Web Interface Guidelines compliance. Use when asked to "review my UI", "check accessibility", "audit design", "review UX", or "check my site against best practices".
metadata:
  author: vercel
  version: "1.0.0"
  argument-hint: <file-or-pattern>
---

# Web Interface Guidelines

Review files for compliance with Web Interface Guidelines.

This copy works offline. The rules are in `guidelines.md` next to this file: a local copy of Vercel's `command.md` from `vercel-labs/web-interface-guidelines` (MIT), taken 2026-10-30. Do not fetch the rules from the network, and never send the reviewed files anywhere.

## How It Works

1. Read `guidelines.md` in this skill's folder
2. Read the specified files (or ask the user which files to review)
3. Check against all rules in `guidelines.md`
4. Output findings in the terse `file:line` format it specifies

Where a rule disagrees with the project's `CLAUDE.md` or `DESIGN.md` (for example Title Case headings, or preconnecting to a CDN when the project self-hosts everything), the project wins.

## Updating the rules

Only when AJ asks: download `https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md`, read all of it, and replace the rules in `guidelines.md` below its header. That downloads one file and sends nothing.
