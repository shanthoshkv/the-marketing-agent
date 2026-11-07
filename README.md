# India Marketing

A Claude Code plugin, and a portable agent skill, for marketing to Indian audiences and Indian companies. It covers brand, product, performance, video, creators, content, B2B, and idea work.

It will not invent a recipe, a delivery area, a cure, or a rate card to make the brief feel finished.

## Install

In Claude Code:

```
/plugin marketplace add shanthoshkv/the-marketing-agent
/plugin install india-marketing@the-marketing-agent
```

Restart Claude Code, then describe the brief or run `/india-marketing:india-marketing`.

To load this folder without installing:

```
claude --plugin-dir .
```

Codex, Cursor, and Grok Build read the skill folder directly. On Windows, junction it so they share this copy:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills" | Out-Null
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills" | Out-Null
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.grok\skills" | Out-Null
$src = Join-Path (Get-Location) "skills\india-marketing"
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\india-marketing" -Target $src
New-Item -ItemType Junction -Path "$env:USERPROFILE\.agents\skills\india-marketing" -Target $src
New-Item -ItemType Junction -Path "$env:USERPROFILE\.grok\skills\india-marketing" -Target $src
```

Run that from the repo root. Use `/india-marketing`, or ask for marketing aimed at an Indian audience, company, or city.

## What a run writes

The agent fills one template:

| Template | Use it when |
| --- | --- |
| `assets/brief.md` | The job is still unclear |
| `assets/campaign.md` | You want the strategy or the media sketch |
| `assets/script.md` | You want a film, a Reel, a Short, or a creator brief |

Audience-facing lines are in the audience language. A figure from the benchmarks file carries its source and month. A price or city the agent added is marked `Assumption:`.

## What this version does not do

No media buying, no ad-account login, and no finished film. The skill writes the plan, the script, the shot list, and the review. It is marketing guidance, not legal advice.

## Layout

```
.claude-plugin/plugin.json
skills/india-marketing/    the skill
  references/              market, channels, compliance, calendar, craft, plays, benchmarks
  assets/                  brief, campaign, script, review
```

Figures in `skills/india-marketing/references/benchmarks.md` are dated November 2026.
