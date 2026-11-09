# India Marketing

A Claude Code plugin, and a portable agent skill, for marketing to Indian audiences and Indian companies. It covers brand, product, performance, video, creators, content, B2B, and idea work.

It will not invent a recipe, a delivery area, a cure, or a rate card to make the brief feel finished.

Sectors: D2C, FMCG, commerce, restaurants, education, clinics, property, finance, B2B, apps, travel, jewellery and weddings, auto, and causes. Changes per version are in `CHANGELOG.md`.

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
$hooks = Join-Path (Get-Location) "skills\feed-hooks"
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\feed-hooks" -Target $hooks
New-Item -ItemType Junction -Path "$env:USERPROFILE\.agents\skills\feed-hooks" -Target $hooks
New-Item -ItemType Junction -Path "$env:USERPROFILE\.grok\skills\feed-hooks" -Target $hooks
```

Run that from the repo root. Use `/india-marketing`, or ask for marketing aimed at an Indian audience, company, or city.

## Example

```
/india-marketing:kit Reel for my sweet shop in Lucknow. Kaju katli ₹960 a kilo. Diwali. Orders on WhatsApp 9 am to 9 pm.
```

Returns a founder kit in Hindi (marked as an assumption) with an English working translation, three hooks, a 14-second film table, the first WhatsApp reply, and `Missing` for the shop name, number, and delivery area. Full output: `examples/founder-kit.md`. A critic pass: `examples/critic-pass.md`.

## Commands

| Command | Writes |
| --- | --- |
| `/india-marketing:brief` | A brief from a rough idea |
| `/india-marketing:kit` | Full campaign kit |
| `/india-marketing:campaign` | Strategy only |
| `/india-marketing:script` | Film or creator script |
| `/india-marketing:critique` | Scores a draft, does not rewrite |
| `/india-marketing:calendar` | Festival and category calendar |
| `/india-marketing:readout` | Planned vs actual, scale or kill |

## What a run writes

Founder mode is one city and a short kit. Agency mode is the full kit plus a critic pass. A month of content is eight slots, not thirty invented claims. A hook, or a question about how a feed ranks a post, uses `skills/feed-hooks`.

| Template | Use it when |
| --- | --- |
| `assets/brief.md` | The job is still unclear |
| `assets/kit.md` | You want the campaign: idea, hooks, film, WhatsApp, creator |
| `assets/campaign.md` | You want the strategy only |
| `assets/script.md` | You want a film or a creator script only |
| `assets/critic.md` | You want the draft scored, not rewritten |
| `assets/readout.md` | A flight ended and you want scale, fix, or kill |

Audience-facing lines are in the audience language. A figure from the benchmarks file carries its source and month. A row older than a year is context. A price or city the agent added is marked `Assumption:`.

Two agents sit beside the skill. `marketing-critic` scores a draft. `marketing-researcher` fetches a live number or date and does not write the ad.

## Evals

```
claude plugin eval .
```

Each folder in `evals/` is one pressure case: `prompt.md` plus an LLM grader. Results land in `evals/results/`, which git ignores.

## What this version does not do

No media buying, no ad-account login, and no finished film. The skill writes the plan, the script, the shot list, and the review. It is marketing guidance, not legal advice.

## Layout

```
.claude-plugin/plugin.json
agents/                    critic, researcher
commands/                  slash commands
evals/                     claude plugin eval suite
examples/                  golden outputs
research/papers/           open papers on hooks and ranking
skills/feed-hooks/         skill built from those papers
skills/india-marketing/
  references/              market, sectors, languages, offers, and the rest
  assets/                  brief, kit, campaign, script, review, critic
```

Figures in `skills/india-marketing/references/benchmarks.md` are dated November 2026.
