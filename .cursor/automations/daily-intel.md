# Cursor Automation - Cloude daily_intel

## Draft

| Field | Value |
|-------|-------|
| Name | Cloude daily_intel |
| Description | Daily web advisory + impact assessment (no patching) |
| Trigger | Weekdays 9:00 - cron 0 9 * * 1-5 (confirm timezone in editor) |
| Tools | None |
| Repository | Pick in editor - must include .cursor/agents/vuln-* and docs/security/ |
| Branch | main |
| Finish in editor | Repository, timezone, Cloud Agent |

## Prerequisite

Cloude workspace root is not a git repo. Push the full workspace to GitHub (or pick an equivalent monorepo) before saving the automation.

## Steps

1. Open Agents Window
2. Ask agent to open Automations editor with daily-intel.prefill.json as prefillWorkflowData
3. Set repository and JST schedule in editor, then save
4. Confirm Cloud Agent compute is enabled

## Instructions

Same as prompts field in daily-intel.prefill.json (Japanese).
