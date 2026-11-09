---
name: feed-hooks
description: >-
  Use when the work is a hook, a retention loop, a feed, a Reel or short
  video that has to earn the next watch, or a question about how social
  ranking, likes, watch time, or habits decide what gets seen. Triggers
  include hook, scroll, retention, watch time, algorithm, For You, feed,
  likes, habit, variable reward, and notification.
license: MIT
---

# Feed hooks

A hook is the first action a feed can reward. The reward has to be something the product, the film, or the account can actually give.

## Read this, then only what the job needs

| The job needs | Read |
| --- | --- |
| Why a person comes back, or which loops prolong use | `references/reward.md` |
| How a homepage, a For You page, or a ranked feed decides the next post | `references/ranking.md` |

Paths are relative to this skill folder. The PDFs live in `research/papers/` at the repo root. Open a PDF only when a number in the reference is not enough.

If the audience, company, or market is Indian, the `india-marketing` skill still decides language, claims, and what may be said. This skill does not replace it.

## What to write

Name the feed and the signal that feed rewards. Then write the hook.

- The signal is watch time, a like, a share, a reply, a follow, or a search. Say which one, and why that feed cares. `references/ranking.md` is the home of those signals.
- The first action is small enough to do in the moment: keep watching, tap, reply, save.
- The payoff is true. A price, a fact, a joke, or the next real step in the product. If the payoff is not in the brief, write `Missing` and do not invent one.
- Say what this loop will not do.

Do not forecast a view count, a chance of going viral, or a return on ad spend. Cascade size is mostly unpredictable even with rich data. The bound is in `references/ranking.md`.

## What this skill will not design

These are the loops the papers document, and they are not methods to copy.

- A feed with no end, autoplay the person did not choose, or a reward that arrives on a slot-machine schedule so they cannot stop.
- A read receipt, a streak, or a notification whose job is social pressure.
- An interrupted task, a life counter, or a "super hard" gate whose exit is a payment.
- Outrage, fear, or a false cliffhanger as the way to buy shares. Weighting likes and shares raises engagement and also raises misinformation and polarization.
- A variable-reward loop aimed at a child.

A refusal that names the loop and still ships a hook with a true payoff is finished. A refusal with no hook is not.
