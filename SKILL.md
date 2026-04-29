---
name: skill-registry-builder
description: Use when the user mentions registry, skill registry, agent registry, skill catalog, skill marketplace, skill hub, or MCP directory. Also triggers when the user asks about structuring, organizing, or distributing skills or agents — categories, trust tiers, install flows, governance, curation, or benchmarking against an existing registry.
---

# Skill Registry Builder

Guides the user through designing and building a skill or agent registry.
**Output:** a finished, self-contained registry website (`registry.html`) the user can open in any browser and share internally — no technical setup required. The website IS the registry.

## When this skill applies

Use this skill when the user is:

- Scoping a new registry from a vague starting point
- Pressure-testing a partial list of pillars
- Benchmarking against an existing registry to separate standard patterns from genuine innovation
- Stuck on a specific decision: taxonomy, trust tiers, install UX, bundles, governance, ownership rotation

## How to run the procedure
- Present the user with the questions/pillars required to build the skill in the form of multi-option selections

## Core principle

Most of what a skill registry needs is the same as any other catalog of installable things: a list of items, metadata, search and browse, install, and ongoing upkeep. These patterns are well-understood. Copy them.

The real design work is in the decisions specific to the user's context: audience, how trust is signaled, how skills stay current, how people are pushed toward the registry. Focus there.

The biggest mistake in registry design is treating the registry as something you build once and finish. It needs ongoing work — things go out of date, skills stop being useful, owners leave. Plan for that, not just launch.

---

## Step 1: Capture intent

Before proposing anything, get clear answers to these five questions. Ask conversationally, not as a form. If any are already answered in the conversation, do not re-ask.

1. **Who is the audience?** Developers, non-technical business users, or mixed. This changes most downstream decisions.
2. **Internal or public?** Internal registries lean on organizational signals (ownership, endorsement). Public registries lean on community signals (stars, reviews, downloads).
3. **What platforms will the skills run on?** One or several. Multiple platforms require compatibility info per skill.
4. **Who publishes?** Anyone, a central team, or gated by review. This determines contribution flow and governance.
5. **What does success look like in six months?** Number of skills, adoption per team, skills retired per quarter. This shapes what you instrument.

Batch the questions into one turn. Do not interview one at a time.

---

## Step 2: Present the pillar framework

Once intent is clear, present the four pillars:

### The four pillars

**1. Discovery** — how users find skills
**2. Evaluation** — how users decide whether a skill is worth using
**3. Installation & Use** — how users install, run, and update skills
**4. Maintenance** — how the registry stays healthy over time

Every feature should map to one of these. If it does not map, it is either out of scope or a pillar is missing.

### Sub-components under each pillar

**Discovery:**
- Browse (categories, task-oriented entry points)
- Search and filter (by platform, team, tag)
- Trending / Featured / New
- Personalized defaults (by role or team)
- Bundles as discovery objects

**Evaluation:**
- Preview (what the skill does, at a glance)
- Try before install (playground, sample prompts)
- Trust signals (verification level, ownership, endorsement, last-updated)
- Reviews and ratings
- Security and review pipeline
- Curation levels as filters (e.g., Official, Team-Verified, Community, Experimental)

**Installation & Use:**
- Install flow (CLI, one-click, download-and-upload, multi-platform)
- Platform compatibility
- Updates and version management
- Team configuration (the current approved set of skills per team, not just per user)

**Maintenance:**
- Contribution flow (submit, review, publish)
- Ownership and freshness rules (each skill has an owner and a review cadence)
- Governance (review process, deprecation, sunset)
- Distribution (how the registry is pushed to users, not just waited on)
- Usage data (what gets used, by whom, what does not)

---

## Step 3: Work through each pillar

Present each pillar as its own multi-select turn, one pillar per turn, in order. Do not present all four at once. Do not write prose for pillar decisions — multi-select only, no paragraphs, no explanations before the user has selected.

If a pillar has multiple distinct concerns (e.g. Maintenance covers both freshness and distribution), split it into two multi-selects in sequence. Never split a pillar into prose Q&A — always multi-select, even when there are multiple questions.

For each multi-select:
- The question is the specific decision being made
- The options are the relevant sub-components for this user's context, drawn from the list below — pick the two or three most relevant based on Step 1 answers, plus "Something else"
- The helper text under the question flags the one trap most relevant to their situation — one sentence, not a paragraph
- After the user selects, confirm their choice in one line and immediately present the next multi-select

---

## Step 4: Internal versus public differences

If the registry is internal, these are the key differences from public registries:

- **Trust comes from ownership, not automation.** Inside a company, "Owned by Legal Ops" matters more than a security scan score. Build verification around who in the organization vouches for the skill.
- **Usage data should be team-specific.** "12 people on your team use this" is more useful than global install counts.
- **Deprecation needs to be planned.** Internal registries do not self-maintain. Every skill needs an owner, a review schedule, and a way to flag skills that have gone stale.
- **Distribution is push, not pull.** Users will not find an internal registry on their own. Build in onboarding integration, team announcements, and periodic updates per function.
- **You likely do not need a separate MCP server directory.** Users want capabilities. The skill-vs-MCP distinction is usually plumbing.
- **Pick one install method.** Multiple install paths create confusion. Pick one and make it the default.

---

## Step 5: Populate the registry

By the end of Steps 1–4 the schema is implicit in what was decided. Summarise it back to the user in one short block (field names only, e.g. name, description, owner, category, trust tier, platform, install method) and confirm before proceeding.

Then collect skill entries through conversation. Ask the user to go one by one or paste a list. For each entry, extract the fields from what they say — do not make the user fill in a form. If a field is unclear, ask; if it is not applicable, leave it blank.

Keep collecting until the user says they are done.

## Step 5.1: Real skills or examples?

Ask the user one question before building:

> "Are you deploying this registry now with your own skills, or would you like 2–3 example skills added so you can show the team what it would look like?"

- **Deploying now** — build with the entries collected. Skip to Step 6.
- **Show the team** — add 2–3 realistic example skills so the registry looks populated when presented. Generate them based on the audience and categories decided in Steps 1–3 (e.g. for a sales team: a cold email drafter, a discovery call prep skill, a proposal summariser). Mark them clearly as examples. Then proceed to Step 6 with the real entries plus the examples.

Do not add example skills without asking. Do not skip this step.

---

## Step 6: Build the registry website

Before generating, ask the user one question:

> "Do you want to use your own brand colours, or the default design?"

- **Default** — proceed with the built-in design.
- **Custom brand** — collect: primary colour (hex), secondary colour (hex, optional), preferred font (optional). Apply these to all buttons, accents, and highlights in the generated HTML.

Produce a single self-contained `registry.html` file.

The file must be fully self-contained: no external fonts, no CDN dependencies, no separate data files. Must work when opened directly in a browser with no server or build step. Shareable as-is via email, Slack, or any static host.

### Page structure

The file is a single HTML document with client-side section navigation (show/hide, no page reloads). It has five sections:

**Home**
- Hero with registry name, one-line description, and a prominent search bar
- Task-oriented entry points (e.g. "Prospecting", "Proposals", "Follow-ups") as large clickable tiles — not a flat category list
- Featured skill slot (the skill with `featured: true`)
- Trending row (most recently added or highest usage_count) — must use `id="trending"`
- Category chips below

**Browse / Catalog**
- Faceted search: filter by category, trust tier, owner, status simultaneously
- Results as cards, updating live as filters change
- Card shows: name, description, category, owner, last_updated, status badge, install button

**Skill Detail**
- Triggered when a card is clicked — replaces the grid, back button returns to Browse
- Full skill entry: name, description, category, owner, last_updated, status, all sample_prompts listed as copyable blocks, install button prominent

**Request a Skill**
- A simple form: skill name, what it should do, who needs it, which team
- On submit, generates a pre-filled email or Slack message the user can copy — no backend required

**About / Docs**
- How to install a skill (one-click flow explained)
- How skills are reviewed (quarterly cadence)
- How to flag a stale skill
- Who maintains the registry

### Data integrity check

Before generating the HTML, verify that the SKILLS data structure includes every field confirmed in Step 5. If any field is missing from an entry, flag it to the user before generating — do not silently drop fields.

---

## Verification: when the conversation is done

Do not wrap up until all six items are either done or the user has explicitly declined.

1. **Intent captured.** All five Step 1 questions answered or declined.
2. **All four pillars discussed.** Discovery, Evaluation, Installation & Use, Maintenance. None skipped without the user saying so.
3. **Concrete recommendation per pillar.** Not a list of sub-components — a specific suggestion.
4. **Internal vs public differences covered if internal.** Step 4 walked through. Skip only if the registry is confirmed public.
5. **Schema confirmed and entries collected.** At least one skill entry added; user has said they are done adding.
6. **`registry.html` produced.** Self-contained, opens in a browser, entries visible.

If the user wants to stop but an item is missing, name it: "We have not covered Maintenance yet — do it now or later?"
