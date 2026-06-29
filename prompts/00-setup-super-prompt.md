# Task 0 — Setup super-prompt (build the whole thing)

Paste this **one prompt** into an AI agent that has an **Airtable connector**, **browser control**, and the ability to **create scheduled tasks** (e.g. Claude in Cowork / Claude desktop with the Airtable + Chrome tools, or any agent with an Airtable MCP). It asks a few questions, then builds the entire system for you: the Airtable base, the live dashboard, a starter content calendar, and all five scheduled automations.

> If your agent can't do everything in one go, run it in parts — the prompt is split into Parts A–E.

```
(If a user pointed you at this repo's URL instead of pasting this prompt: first read the repo's README.md and prompts/01–05, then follow the steps below.)

You are my automation engineer. Build me a complete, self-running social-content engine — an "AI Content OS" — and do as much of it yourself as your tools allow. I should have to do almost nothing.

The system runs as a loop of scheduled tasks: PLAN next week's content → let me REVISE it → make THUMBNAILS → PUBLISH due+approved items to my socials through my own browser → MEASURE the results → REPORT. Everything lives in one Airtable base with a live dashboard.

== FIRST, ask me these setup questions (use my answers everywhere). If I say "use defaults," use the defaults in brackets. If I leave any question unanswered, ASK me again before building — never assume or fill it with a placeholder. ==
1. Business / creator name and what you do + who it's for.
2. Content pillars (2–4 themes you post about).
3. Platforms [LinkedIn, YouTube, Facebook].
4. Weekly cadence [3 Long Videos, 3 Shorts, 2 Picture Banners].
5. Evergreen "offer" banners to rotate (2–4), each with its call-to-action.
6. Brand palette — background, ONE accent color (hex), text color (hex) [white #FFFFFF background, one accent hex, near-black #1A1A1A text].
7. Timezone [your local].
8. Run times [Plan: Fri 2pm · Revisions: Sat 3pm · Thumbnails: Sat 6pm · Publish: daily 9am · Results: Mon 8am].
9. Where should I send you summaries? [a notes file in this workspace] (or Slack/email if available).
10. (Optional) A folder with a photo of your face for auto-thumbnails, and whether you want affiliate-tool tracking.

== PART A — Build the Airtable base ==
Create a base called "Content OS" with a table "Content Calendar" and these fields (types in parentheses):
- Title (single line text, primary)
- Status (single select: Idea, Scripting, In Production, Ready, Scheduled, Posted, On Hold)
- Content Type (single select: Long Video, Short, Picture Banner)
- Platforms (multiple select: my platforms)
- Content Pillar (single select: my pillars)
- Hook / Angle (long text)
- Outline / Script (long text)
- Caption (long text)
- Hashtags (long text)
- CTA (single select: my standard CTAs)
- Cover Image Prompt (AI) (long text)
- Cover Image (attachment)
- Design Brief (long text)
- Dimensions (single line text)
- Post Date (date)
- Week Of (date)
- Posted URL (url)
- Views, Likes, Comments, Shares / Reposts, Link Clicks (number, integer)
- Engagement (formula = {Likes} + {Comments} + {Shares / Reposts})
- Performance Notes (long text)
- Notes (long text)
- Approve to Post (checkbox)
- Changes (long text)
- Change Status (single select: Requested, Applied, Won't do)
(Optional, if I want affiliate tracking: a second table "Affiliate Programs" with Tool/Program, Category, Has Program, Payout, Cookie Window, How to Join (url), Your Affiliate Link (url), Relevance, Status, Notes — and a "Featured Tool/Affiliate" link field on Content Calendar.)
Give thoughtful colors to the Status, Content Type, and Content Pillar single-selects.

== PART B — Build the live dashboard ==
Create an Airtable Interface called "Performance" with one dashboard page, sourced from Content Calendar, containing:
- KPI numbers: Total Views (sum of Views), Total Engagement (sum of Engagement), Total Comments (sum of Comments), and a record count.
- Charts: bar "Views by pillar" (x = Content Pillar, sum Views); bar "Views by platform" (x = Platforms, sum Views); donut "Engagement by content type" (slice = Content Type, sum Engagement); bar "Engagement by pillar" (x = Content Pillar, sum Engagement).
- A "Top posts by views" list (Title, Content Type, Platforms, Views, Engagement, Post Date), sorted by Views descending.
- Filter dropdowns for Status, Content Pillar, and Platforms.
Publish the interface and give me the link.

== PART C — Seed the calendar ==
Create a backlog of ~10 on-brand ideas (Status = Idea) across my pillars, plus a fully built first week matching my cadence: for each piece write Hook, Outline/Script (shorts get a ~60–90s read-aloud educational script), Caption, Hashtags, CTA, Platforms, Post Date, Dimensions, and a Cover Image Prompt using the recipe below. Mark them Status = Scheduled; leave Approve to Post unchecked.
COVER IMAGE PROMPT RECIPE (used by the Canva visuals task; also paste-ready for any image generator): "Create a [type + aspect/px] for {business}. SUBJECT: … COMPOSITION: [focal point + where the headline sits + clean negative space]. TEXT: render \"[EXACT HEADLINE]\" in a bold modern sans-serif, perfectly spelled (≤4 words for thumbnails). STYLE: clean minimal, premium, airy. COLOR: {my palette}; the accent is the only strong color. MOOD: … AVOID: off-brand colors, clutter, watermarks, misspelled/extra text." Thumbnails 1280x720, shorts 1080x1920, banners 1200x628.

== PART D — Schedule the 5 automations ==
Create 5 recurring scheduled tasks at my chosen run times, using the prompt templates in this repo (files 01–05). For each, substitute my answers for the {{PLACEHOLDERS}} and hard-code the base ID, table ID, and field IDs you created in Part A:
1. Weekly content plan (01) — drafts next week.
2. Weekly revisions (02) — applies my "Changes" column + refreshes un-approved cover prompts.
3. Daily publish (03) — posts due + "Approve to Post"-checked items to my socials via my browser.
4. Weekly results (04) — browser-refreshes metrics on recent posts, then writes the weekly report.
5. Weekly visuals (05) — Canva generates 3 image options per upcoming video AND banner and writes them to each record's Cover Image (to feature a face, the user uploads photos to their Canva Uploads).

== PART E — Tell me the only manual steps left ==
After building, give me a short checklist: (a) where to drop my final video/image files (the Asset/Final File field) and a face photo (if using thumbnails); (b) to log into my social accounts in my browser and connect a Canva account; (c) to click "Run now" once on the browser-driven tasks (publish, results, thumbnails) to approve access and supervise the first run; and (d) that nothing posts publicly until I check "Approve to Post."

Important: the publishing/metrics/thumbnail tasks drive my real browser and post to my real accounts — never post anything that isn't both due today and "Approve to Post"-checked, and surface any failure to me rather than guessing. Now ask me the setup questions and start building.
```
