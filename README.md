# AI Content OS

A self-running social-content engine. One Airtable base + an AI agent + your own browser. It plans your week of content, lets you edit it, generates thumbnails, posts to your accounts, reads back the results, and reports — on a schedule, with no third-party scheduling SaaS.

```
   ┌─────────────────────────────────────────────────────────────┐
   │                      THE WEEKLY LOOP                          │
   │                                                              │
   │  PLAN ──► REVISE ──► THUMBNAILS ──► PUBLISH ──► MEASURE ──►   │
   │  (Fri)    (Sat)       (Sat)         (daily)     (Mon)     ┐   │
   │    ▲                                                      │   │
   │    └──────────────────  REPORT  ◄─────────────────────────┘   │
   │                                                              │
   │            All in one Airtable base + live dashboard         │
   └─────────────────────────────────────────────────────────────┘
```

## ⚡ Set it up in one message (no copy-paste)

Tell your AI assistant (Claude with an Airtable connector + browser control):

> **Set up the AI Content OS from `https://github.com/tom-saida/ai-content-os` — read the README and everything in `prompts/`, then build it for me: ask me the setup questions, create the Airtable base + live dashboard, seed a starter week, and schedule the 5 tasks.**

It reads this repo, asks you a handful of questions, and builds the whole thing — base, dashboard, and all five automations. No copying and pasting.

_Prefer to do it by hand? Paste [`prompts/00-setup-super-prompt.md`](prompts/00-setup-super-prompt.md) instead._

## What it does

- **Plans** next week's content into an Airtable "Content Calendar" (videos, shorts, banners) with hooks, scripts, captions, hashtags, and image prompts.
- **Revises** it from a simple `Changes` column you type into — the agent applies your edits.
- **Makes visuals** in **Canva** — video thumbnails (optionally with your face) and banners, 3 options each to choose from.
- **Publishes** the items that are due and that you've checked `Approve to Post`, straight to your accounts through your own logged-in browser.
- **Measures** by reading the engagement numbers back off each post and writing them to the records.
- **Reports** a weekly performance summary, and powers a **live Airtable dashboard** (KPIs + charts + top posts).

## What you need

- An **Airtable** account (free works to start).
- An **AI agent** with: an Airtable connector/MCP, browser control (e.g. the Claude-in-Chrome extension), and the ability to create scheduled tasks. (Built and tested with Claude.)
- A **browser** logged into your social accounts (LinkedIn / YouTube / Facebook / etc.).
- A connected **Canva** account if you want auto-generated thumbnails + banners (optional).

## Quick start

1. Open `prompts/00-setup-super-prompt.md` and paste it into your AI agent.
2. Answer its setup questions (business, pillars, platforms, cadence, offers, brand colors, timezone, run times). Say "use defaults" to move fast.
3. It builds the Airtable base, the live dashboard, a starter content calendar, and the 5 scheduled tasks.
4. Final manual steps it will give you: drop your finished video/image files into the `Asset/Final File` field, log into your socials, connect Canva, and click **"Run now"** once on the browser-driven tasks to approve access. Nothing posts publicly until you check **`Approve to Post`**.

## The 5 scheduled tasks

| # | Task | When | What it does |
|---|------|------|--------------|
| 1 | [Weekly content plan](prompts/01-weekly-content-plan.md) | Weekly (Fri) | Drafts next week's content |
| 2 | [Weekly revisions](prompts/02-weekly-revisions.md) | Weekly (Sat) | Applies your `Changes`; refreshes un-approved cover prompts |
| 3 | [Daily publish](prompts/03-daily-publish.md) | Daily | Posts due + approved items to your socials via your browser |
| 4 | [Weekly results](prompts/04-weekly-results.md) | Weekly (Mon) | Reads back metrics, writes the weekly report |
| 5 | [Weekly visuals](prompts/05-weekly-thumbnails.md) | Weekly (Sat) | Canva makes 3 image options per video + banner |

## Data model (Content Calendar)

Each row is one piece of content, moving `Idea → Scheduled → Posted`. Key fields: Content Type, Platforms, Content Pillar, Hook, Outline/Script, Caption, Hashtags, CTA, **Cover Image Prompt** + **Cover Image**, **Asset / Final File** (the finished video/image you drop in to publish), Post Date, Week Of, the metric fields (Views / Likes / Comments / Shares / **Engagement**), **Approve to Post** (the publish gate), and **Changes / Change Status** (your edit loop). Full schema is in the setup prompt.

## Placeholders to fill in

The task prompts use `{{PLACEHOLDERS}}`:

`{{BUSINESS_NAME}}` · `{{PILLARS}}` · `{{PLATFORMS}}` · `{{CADENCE}}` / `{{TOTAL}}` · `{{YOUR_CTAS}}` · `{{OFFER BANNERS}}` · `{{BRAND_COLORS}}` · `{{BASE_ID}}` / `{{TABLE_ID}}` (+ field IDs) · `{{NOTIFY_TARGET}}` · `{{FACE_PHOTO_FOLDER}}` / `{{THUMBNAIL_OUTPUT_FOLDER}}` · `{{today}}`.

The setup super-prompt fills most of these for you from your answers.

## Honest caveats

- **Browser posting/metrics** depend on staying logged in and the app being open; **video uploads** are the most failure-prone step — the tasks flag failures instead of guessing.
- **Link clicks** aren't visible from native analytics unless you post a trackable link.
- **Auto-thumbnails** use the Canva API (reliable, returns multiple candidates → exports PNG). To feature your face, upload a few photos to your Canva Uploads once.
- **The `Approve to Post` checkbox is the safety gate.** Nothing goes public unless it's due *and* checked.

---

## Publish your own copy to GitHub

This folder is a ready-to-publish repo. To put it on your GitHub as a public install link:

1. **github.com → New repository** → name it `ai-content-os`, set **Public**, click Create.
2. On the empty repo, click **"uploading an existing file"** → drag in everything from this folder: `README.md`, `flow-diagram.png`, `flow-diagram.svg`, and the whole `prompts/` folder.
3. **Commit**. That's it — your repo URL (`https://github.com/<you>/ai-content-os`) is now the link people use in the one-message setup above.

_(Prefer the command line or GitHub Desktop? Those work too — this is just plain files.)_

---

_A template for building your own content automation. Customize the prompts to your brand and workflow._
