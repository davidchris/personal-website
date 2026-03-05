---
title: "Why I Built My Own Transaction Categorizer"
date: 2026-03-04T13:02:11+01:00
draft: false
---

Every month, same ritual. Export CSV from the bank. Open the spreadsheet. Scroll through 80-odd transactions and manually tag each one: groceries, rent, insurance, that mystery debit from three weeks ago. Copy the numbers into the budget tracker. Close the laptop feeling like I just did someone else's homework.

I've been doing this for years. My wife and I track our household spending across maybe 20 categories, because we want to know where the money goes, likely this is a work habit from me to have factual information and not only gut feelings about what's going on.
And we want to be more deliberate about how we spend our money. The spreadsheet worked. It was just soul-crushingly tedious.

## Why not just use an app?

The obvious answer is: use Finanzguru, or Copilot, or YNAB. I tried. None of them stuck, and the reasons were always the same.

**Privacy.** Most of these tools want your banking credentials or connect through aggregators like Plaid. I work in cybersecurity. I spend my days developing ML solutions to detect breaches. The idea of handing my family's financial data to a third-party aggregator makes my eye twitch. Call it professional paranoia--I call it informed consent.

**German banking quirks.** Transaction descriptions from German banks are their own special language. A "Lastschrift" with a purpose field stuffed with SEPA reference numbers, merchant IDs, and truncated business names doesn't parse cleanly with tools built for Chase or Bank of America. The Purpose field alone can be a wall of text that most categorization engines choke on.

**Intelligence without the cloud.** I wanted something that could *learn* from my corrections. Not a static rule engine, not a cloud AI that phones home with every transaction, a model that runs locally, improves over time, and never sends my data anywhere.

Nothing on the market hit all three. So I built it.

## The build

I kept the stack deliberately boring. Python, Streamlit for the UI, LightGBM for the ML model, SQLite for storage. No microservices, no containers for the MVP, no separate API layer. Streamlit handles everything in one process. The KISS principle, applied aggressively.

The ML pipeline is straightforward: TF-IDF on transaction text (character n-grams work surprisingly well for German merchant names), a few engineered features like amount ranges and day-of-month patterns, and a LightGBM classifier. Before the model even runs, there's a merchant memory layer, if I've categorized "REWE MARKT" as groceries fifty times, the system just remembers that.

The interesting part was using AI-assisted development to build it. I started with Windsurf (Cursor's competitor) for the initial prototype, then switched to Claude Code for the heavy lifting. I tracked the API costs as I went:

- Initial working prototype: **$3.62**
- After first real use and bug fixes: **$6.37**
- After substantial refactoring and adding the analytics dashboard: **>$33**

That's the total development cost for a working, deployed application, a tool I now use every month. The experience of iterating with Claude Code was good enough that I ditched Windsurf and Cursor entirely and upgraded to the Max subscription.

## What I learned

**Traditional ML beats LLMs for this task.** This was the biggest surprise, and it deserves its own blog post (coming soon). The short version: with ~2,000-3,000 labeled transactions, a well-tuned LightGBM model with good feature engineering hits classification accuracy that an LLM can't match for this specific domain — and it runs in milliseconds, not seconds. When you're reviewing 80 transactions and want instant predictions as you correct mistakes, latency matters more than raw capability.

**Ship ugly, ship fast.** The first version of the UI was rough. Streamlit imposes real constraints on layout and interactivity. But it *worked*. I could import a CSV, get predictions, correct the wrong ones, and export the result in under ten minutes instead of an hour. That's the bar. Everything else is polish.

**AI tools change the economics of side projects.** The $33 I spent on Claude Code API calls replaced what would have been weeks of evenings building the Streamlit frontend, the analytics dashboard, the data pipeline. For a working parent with limited coding time, this is transformative. It doesn't write the code for you (you still need to know what you're building and why) but it compresses the tedious parts dramatically.

## Open-sourcing it

I released the web app under the [Apache License 2.0 on GitHub](https://github.com/davidchris/fafycat). The repo contains everything: the ML pipeline, the web app, sample data simulations for testing, and documentation to get started.

Why open-source it? Partly because I benefited from countless open-source tools building it. Partly because the privacy-first approach only works if people can verify the code actually stays local. And partly because I suspect other German-speaking households have the same spreadsheet problem I did.

A few caveats: this is a tool I built for my family's workflow. It's opinionated about CSV formats (German banks first), it assumes a specific category hierarchy, and the UI reflects my priorities, not a product designer's vision. It works well for what it does. It won't win any design awards.

## What's next

I'm exploring an Apple-native desktop app direction — SwiftUI with CoreML for on-device inference. The idea is to convert the LightGBM model to CoreML format and ship something that runs entirely on your Mac without needing Python installed. Privacy-first finance tooling for the Apple ecosystem, where "your data never leaves your device" isn't marketing copy but a technical guarantee.

That's a bigger project, and it's still in the planning phase. The open-source web-app version isn't going anywhere.

If you're interested in the technical details: why LightGBM outperforms an LLM for transaction categorization, how the feature engineering works for German bank data, the model retraining loop; I'll cover all of that in a follow-up post.

For now, you can find [FafyCat on GitHub](https://github.com/davidchris/fafycat). Try it, break it, tell me what you think.
