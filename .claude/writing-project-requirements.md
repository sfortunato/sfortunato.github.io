# Writing Project Requirements

## Overview

Build a full end-to-end blog post workflow on sfortunato.github.io, from blank page to published post and LinkedIn share. The writing section of the site will stay commented out until two posts are live.

---

## Goals

- Publish 2 blog posts before making the writing section visible
- All tooling lives as Claude Code skills (`/skill-name`)
- Posts authored primarily through conversation, not freeform writing
- LinkedIn posts generated automatically from blog content

---

## Website Changes

### Writing Section (already stubbed, not yet live)

The writing section exists in `index.html` at lines 416–435 but is wrapped in an HTML comment. It already has:
- Correct CSS (`#writing`, `.essay-list`, `.essay-title`, `.essay-date`) already in the stylesheet
- Three placeholder post titles (all showing "Coming soon")
- Proper position in the page — after the Work section

To go live, two things need to happen:
1. Uncomment the `#writing` section
2. Add `<a href="#writing">Writing</a>` to the `<nav>` in the header

### Individual Post Pages

Each post gets its own `.html` file in a `writing/` directory (e.g. `writing/post-slug.html`).

Must match the existing design system exactly:
- Same fonts: `DM Sans` (body) + `Lora` (headings)
- Same color tokens: `--bg: #F6F2EB`, `--ink: #1A1714`, `--accent: #8B4513`, etc.
- Same grain overlay (`body::before`)
- Same `max-width: 640px` centered layout
- Same fade-up animation

The essay-list `<span>` tags become `<a href="writing/post-slug.html">` links when a post is live. "Coming soon" entries stay as `<span>` until ready.

### Post page layout

- Header: post title (Lora), date, optional 1-line description
- Body: flowing paragraphs in DM Sans, same `--ink-mid` color
- Footer: link back to the main page
- No sidebar, no comments, no extras

---

## Skills to Build

### 1. `/interview` — Blog Post Interview Skill

**Purpose:** Generate raw blog post content through a back-and-forth interview.

**Behavior:**
- Loads a "Susanne profile" doc at the start (background, perspective, recurring themes)
- User provides the post topic and angle they want to take
- Starts with 3-5 targeted questions based on topic + profile
- Goes freeform based on responses — follows threads, asks follow-ups
- Ends by generating a full rough draft from the conversation
- Output: raw draft text (unpolished, not yet voice-adjusted)

**Open questions:**
- Where does the Susanne profile doc live? (Suggest: `.claude/susanne-profile.md`)
- Should the interview save a transcript alongside the draft?

---

### 2. `/susanne-voice` — Voice Rewrite Skill

**Purpose:** Rewrite a raw draft to sound like Susanne.

**Behavior:**
- Takes the raw draft as input (paste in or point to a file)
- Applies a learned style guide derived from sample writing
- Outputs a revised version
- Skill should also be able to evaluate its own output against the style guide

**Voice calibration (to do before building skill):**
- Susanne to collect writing samples (LinkedIn posts, notes, other writing — mix of sources)
- Samples pasted or provided as files in a future session
- Style guide will be codified into the skill's system prompt

**Open questions:**
- Should this skill iterate (draft → review → revise) or produce one output?
- Is there a preferred length/format for blog posts?

---

### 3. `/linkedin-post` — LinkedIn Post Generator

**Purpose:** Generate a LinkedIn post based on a finalized blog post.

**On Kagi "LinkedIn Speak":**
The feature is a URL parameter (`?to=LinkedIn+speak`) — it is LLM prompt engineering, not a proprietary translator. There is a private beta API (email `luis@kagi.com`), but the practical recommendation is to replicate the behavior natively in the skill. Same result, no external dependency.

**Behavior:**
- Takes the finalized blog post as input
- Generates a LinkedIn post in Susanne's voice adapted for LinkedIn conventions
- Skill decides appropriate length based on content
- Output includes the live post URL (linking back to susannefortunato.com)
- Optionally prompts for personal commentary to prepend

---

### 4. `/publish-post` — Publish to Website

**Purpose:** Take a finalized post and publish it to the site.

**Behavior:**
- Generates a styled `.html` file in `writing/` matching the site's design system
- Updates the essay-list entry in `index.html`: changes `<span>` to `<a href="...">` and sets the date
- On the first post: also uncomments the `#writing` section and adds Writing to the nav
- Commits and pushes to `master` (GitHub Pages auto-deploys)
- Updates `WRITING_BACKLOG.md` status to `published`

---

## Writing Backlog

**File:** `WRITING_BACKLOG.md` in repo root

**Fields per post:**
| Field | Notes |
|---|---|
| Title | Working title is fine |
| Status | `idea` → `drafted` → `voice-pass done` → `published` |
| Notes / Angle | Short description of the post's take or premise |

Three placeholder titles already exist in the commented-out writing section — these can seed the backlog.

---

## Workflow Summary

```
/interview      →  raw draft
/susanne-voice  →  polished draft
/publish-post   →  writing/post-slug.html created, index.html updated, pushed to master
/linkedin-post  →  LinkedIn post (with link to published post)
```

---

## Open Items / To-Dos Before Building

1. **Susanne profile doc** — write `.claude/susanne-profile.md` with background, perspective, recurring themes
2. **Writing samples** — collect examples to calibrate `/susanne-voice`
3. **Seed the backlog** — create `WRITING_BACKLOG.md` and populate with topic list (the three placeholder titles in the HTML are a starting point)
4. **Pick first two posts** — select from the backlog and kick off first `/interview`
