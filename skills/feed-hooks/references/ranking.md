# Ranking

This file is how a feed chooses the next post. The person's return visit is in `reward.md`.

## What the big feeds optimise

Covington, Adams, and Sargin, RecSys 2016. File: `research/papers/02-covington-2016-youtube-dnn.pdf`. Local copy. The ACM notice allows personal or classroom use, not a public repo.

YouTube splits the job. A candidate network narrows millions of videos to hundreds, from watch history, search tokens, and demographics. A ranker then scores those hundreds. They train on watches, not on thumbs, because implicit history is dense and explicit feedback is sparse. The ranker predicts expected watch time, not click probability. Optimising click-through rate had produced clickbait thumbnails. An "example age" feature stops the model from only replaying the past, so new uploads can surface. Training examples are a fixed number per user, so a few heavy users do not own the loss. Offline precision did not reliably match live watch time. They ship on a live test.

Milli, Belli, and Hardt, FAccT 2021. File: `research/papers/06-milli-2021-optimizing-engagement.pdf`.

Engagement is not value. A reply can be anger, a click can be a person checking, a watch can be temptation. On Twitter, with "See less often" as the anchor for "not valued," the learned order was retweet, then reply, then click, as evidence that the person valued the post. A weighted sum of raw engagements hides that.

Write the hook for the signal the feed actually counts. On a watch-time feed, the first seconds have to be worth staying, not worth a false click. On a share-weighted feed, a share still has to be a thing a person would pass on after they knew the payoff.

## Engagement weight has a cost

Germano, Gómez, and Sobbrio, Barcelona School of Economics Working Paper 1501, revised December 2025. File: `research/papers/09-germano-2025-ranking-for-engagement.pdf`.

In their model, putting more weight on likes and shares raises engagement and also raises misinformation and polarization. Personalised ranking widens polarization further. They tie Facebook's 2018 Meaningful Social Interactions update, which raised the weight on comments, reshares, and reactions, to more ideological extremism and affective polarization in Italian and US survey data.

D'Ignazi, Fraxanet, Kaltenbrunner, Le Mens, Germano, and Gómez, KDD 2026. File: `research/papers/13-dignazi-2025-engagement-personalization.pdf`. CC BY.

People click what is near the top, prefer like-minded items, and more extreme users engage more. When the ranker rewards that engagement and personalises the list, extreme items become popular, then show up for milder users. The experiments measure consumption, not a lasting change of opinion.

Germano, Gómez, and Le Mens, WWW 2019. File: `research/papers/16-germano-2019-few-get-richer.pdf`. CC BY.

Under popularity ranking, the smaller class of items can collect more total clicks than the larger class. Clicks from people who want that class concentrate, the few items rise, and rank-followers then click them too. A scarce, loud variant can outrank a larger, quieter set. Do not treat rank as a quality score.

## What an audit can see

Habib, Stoldt, Maragh-Lloyd, Ekdale, and Nithyanand, 2024. File: `research/papers/04-interaction-equation-2024.pdf`.

Sock-puppet audits of YouTube, Reddit, and X homepages. YouTube personalises hard and is driven by what was watched. Reddit personalises from likes and from the communities a user joins. X personalises less. Follow is its strongest lever. YouTube exploits a known interest more than the other two. X downranked political content relative to other topics. The action (watch, like, follow) mattered more than the topic on it.

Huang, Ji, and Lin, 2025. File: `research/papers/03-huang-2025-algorithms-vs-peers.pdf`.

A WeChat experiment on 2.1 million users. People prefer redundant content. Both an algorithm and peer sharing pulled them toward newer items. The algorithm produced more engagement with novel content than peer sharing did, even when peer posts carried social cues. Do not tell a client that a personalised feed only narrows the diet. On this platform it widened engagement with new items.

Huszár, Ktena, O'Brien, Belli, Schlaikjer, and Hardt, 2021. File: `research/papers/11-huszar-2022-twitter-amplification.pdf`.

Twitter compared a personalised home timeline with a reverse-chronological control of about 1 percent of accounts. In 6 of 7 countries, mainstream right politicians were amplified more than mainstream left politicians. Right-leaning US news was amplified. They did not find that the far left or the far right were amplified more than moderates. The control group still sees tweets that personalised users reshare, so the gap is probably understated.

## The shape of the platform beats the knob

Saeed, Broniatowski, Simons, Gralla, Suri, and Ciampaglia, 2026. File: `research/papers/05-saeed-2026-platform-architecture.pdf`.

An agent simulation crosses architecture with ranking. On a tree like Reddit, swapping a chronological feed for a popularity feed did not move spread or quality. On a layered graph like Facebook and a network like Twitter, the popularity feed modestly raised both. On a complete graph like TikTok, the popularity feed produced winner-take-all, hurt spread and quality, and broke the link between quality and popularity. Say which shape the brief is posting into. A hook that assumes a follower graph will not behave the same way on an open For You page.

## Reach will not sit still for a forecast

Martin, Hofman, Sharma, Anderson, and Watts, 2016. File: `research/papers/15-martin-2016-limits-of-prediction.pdf`.

Predicting Twitter cascade size from user, content, and past performance, before the cascade runs, explained less than half the variance. Early "peeking" at the first minutes predicts the rest because of cumulative advantage. It does not tell you how to write the post. Mark a view target as `Assumption:` or leave it `Missing`. Do not present it as the model's output.
