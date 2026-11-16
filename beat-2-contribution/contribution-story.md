# Contribution: [Privacy/site map: add robots.txt (disallow) + noindex on authenticated app pages #276]

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Richard Gabelman
**GitHub Username:** RichardGabelman
**Issue:** [\[GitHub issue link\]](https://github.com/lolimmlost/aidj/issues/276)
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Write search strategy, iterate on issue-scout rubric**

Built a search-strategy which is composed of various GitHub issue queries, ranking filters, and grading quantity parameters. Most iterations on this were with regard to the GitHub issue queries as the terms I was looking for weren't necessarily constrained to my field of interest. Running the scan surfaced a few issues with my original rubric which needed fixing, especially with regard to label-only checks vs. hollistic checks, assignees vs. claimees, and feasability.


**Unit 6: Install voice guard and patch rubric**

Followed the voice guard install instructions. Added a few claim-specific voice rules. Added a local repo-memory file but didn't have to add much due to a well-formed existed CLAUDE.md file. Nothing broke or fell short, the voice guard worked when posting the draft comment and the new rubric changes executed as expected.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

**[Claim comment](https://github.com/lolimmlost/aidj/issues/276#issuecomment-6790098113)**

The search tool itself consistently seemed to find unrelated issues or otherwise poor issues, probably due to slight inaccuracies in various rubrics and instructions. I was hoping to prioritize an issue to work on based on the sector of tech the project was in. I wanted something to do with civictech or government tech, generally. I have had success in previous AI 301 iterations contributing to open-source government sites but it appears my tool did not discover any (or at least preferred others). 

I then moved to looking through the list of issues provided on the website. Here I instead prioritized languages and technologies I knew. I did a few initial passes looking for, again, repositories I thought would be in my area of interest. I found a few issues aligned with that (and even graded a few) before discovering that they required a bit of an extensive process to become a contributor (which I will gladly participate in but wouldn't be doable in the time-alotted). Finally, I did a few more passes, this time just looking for doable issues. I ran into a lot of really old issues and issues with unclear tasks, etc.... Finally, I found an issue from this repository. I was a bit skeptical given the repo appeared to be a one-man (+ Claude) operation but it seems really well organized.

I graded this issue and it approved it. The repo allows external contributions, it's a good first issue, the scope is managable, nobody else has claimed it, the repo is in use, etc....

**Toolkit**

- Tool: Issue scout was initially used to look for issues meeting the conditions in my search strategy. My search strategy was essentially a list of tiered GitHub queries that utilized key words I felt would indicate alignment with an area of interest + some ranking filters to order within a tier (essentially various indicators of issue + repo quality). The initial run of this functionality surfaced some issues with my search strategy and my rubric which were subsequently patched. Two additional runs of this functionality + iteration went better but did not surface any issue worth approaching. The other functionality was grading specific issues. After manually finding what I thought was a good fit, I ran this functionality on the issue and it passed.
- What it produced: The broader scan functionality surfaces a list of 5 issues ranked by best fit. A further json list of the issues goes further into detail on the specific checks and how each issue passed the checks. It also provided a few areas where it believed the search strategy and/or the rubric was faulty, with some recommendations on how to improve it. The specific issue scan just produces a singular json block with the info about how that specific block meets the checks of the rubric, with an overall grade of accept/reject (the one I chose passed). The final change to the rubric per the assignment added a further assessment of issue feasibility (which my chosen issue was determined to be straightforward).
- Difficulties: The full GitHub search strategy struggled as the keywords I chose happened to exist in domains completely unrelated to my expectations. My search strategy (and my rubric) also fell short in rejecting various low quality issues which required some further tuning of my rubric. Finally, the issue website seemed to contain a lot of poor quality issues as well (perhaps because I was late to it), with a bunch of issues being many years old. Finding this repository was actually rather difficult.
- What changed: I think the search strategy could perhaps be a bit more hollistic or perhaps there should be a further breakdown of searching for issues by good technical fit vs. interest fit. Trying to do both in one fell swoop seems difficult, especially with only keyword queries like I tried to employ.

---

## Understanding the Issue

**Problem Description**

The current website configuration allows web crawlers to visit and index every page, which doesn't make sense in an auth-gated application. Only non-auth gated pages (i.e. the landing page) should be indexed and thus reachable via a search engine. The proper way to communicate this to the search engines is with a robots.txt file and a meta noindex tag on authenticated routes. Care must be taken to preserve the existing "unfurl" behavior on share pages.

**Expected Behavior**

Web crawlers should not be attempting to index auth-gated pages.

**Current Behavior**

Web crawlers are attempting to index auth-gated pages. Once shareable links exist, an unguarded tokenized URL can end up indexed.

**Affected Components**

robots.txt typically lives in the root level public/ folder. The meta tag should be placed on the route heads in src/routes/__root.tsx.

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

The problem is more of an external problem requiring new files and additional changes to existing files. I can't really reproduce the problem of web crawlers going on pages we don't want them to without... making my own web crawler, I guess. I simply visually inspected for the possible existence of the files/changes called for to be added by the issue and confirmed they don't exist yet. No problems came up in my visual inspection.

Setting up the application is simple:
Prerequisites: Node.js 20+, PostgreSQL, and a Navidrome instance.
```bash
git clone https://github.com/lolimmlost/aidj.git
cd aidj
npm install
cp .env.example .env   # fill in DATABASE_URL, BETTER_AUTH_SECRET, Navidrome URL/credentials, …
npm run db             # generate + apply migrations
npm run dev            # http://localhost:3003
```

**Steps to Reproduce**

1. Visually observe the lack of a robots.txt file in `public/`.
2. Visually observe the lack of a meta robots tag with noIndex set in `src/routes/__root.tsx` and in `src/routes/music-identity/share.$token.tsx`.

**Reproduction Evidence**

- **Commit showing reproduction:** None
- **Screenshots/logs:** N/A
- **My findings:** No robots.txt exists. No noIndex tags exist on the specified routes.

**Toolkit**

- Tool: repro-check confirmed my existing claim comment passed and reviewd my draft repro-evidence against my voice guard and my repro-evidence rubric.
- What it produced: It produces a json block of the various repro-evidence rubric checks and how my draft repro comment fared against them. It provided tips on how to adjust the comment to match the repro rubric checks.
- Difficulties: No difficulties in utilizing it, it did surface some issues that were summarily addressed. I'd say not all issues need indepth reproduction, some, like this one, are simply obvious.
- What changed: Nothing.

---

## Solution Approach

**Analysis**

There is no robots.txt file in public/ which means web crawlers visiting the site have no guidance on what pages to visit and which to avoid.
There is no meta noIndex tag on all routes with overrides for specific pages that are ok to be indexed (or vice versa).

**Proposed Solution**

Adding robots.txt to public/ that disallows everything except the landing page.
<meta name="robots" content="noindex"> on authenticated routes (root head() in src/routes/__root.tsx, overridable per route).
Share pages: noindex by default, but keep OG/Twitter tags so link previews still unfurl.

**Implementation Plan**

1. Add robots.txt to public/ with a disallow on everything and an allow on the landing page.
2. Add <meta name="robots" content="noindex"> on the root head() in routes.
3. Keep OG/Twitter tags on share pages (music-identity/share.$token) with some sort of override.

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool: plan-check confirmed that my plan comment met repository conventions, contained the correct diagnosis of the issue, established an explicit scope of which files it would change (and how), and that I had a testing strategy to ensure the validity and completeness of my solution. 
- What it produced: When ran on a plan + plan comment, plan-check returns an overall verdict (accept/reject) based on the passing of various checks in its rubric. The specific checks are shown and how the comment addresses them, in both normal text form and in json form. It also includes some helpful tips on things to change/update, especially to get it passing if it was rejected.
- Difficulties: No difficulties with the tool, although it did identify a weakness in my existing plan and offered information on how to fix it.
- What changed: Nothing changed with the tool, but it did recommend the proper testing strategy for the changes outlined in my plan.

---

## Testing Strategy


I will run `curl localhost:3003/robots.txt` and ensure that the text received includes a disallow-all with an allow for / only.
I will ensure that the page source of an authenticated page such as /dashboard contains <meta name="robots" content="noindex">.
I will ensure that a share page has both noindex and the og:/twitter tags.
I will ensure existing tests continue to pass (npx vitest run, npm run lint, and npm run build).

**Toolkit**

- Tool: plan-check judged my existing testing strategy against my plan (and the issue). It first identified a lack of tests and provided ways to test this style of change. I incorporated those changes into my plan and will utilize the testing strategy provided to ensure the validity of my change.
- What it produced: With respect to testing, in its evaluation of my plan comment, one of the checks within my rubric dealt with the existence of a valid testing strategy. It was in this capacity that it first identified the problem with my testing strategy, by having the plan comment fail on that specific check (identified in both normal text and json form). It provided a few lines in normal text on what to do to get the testing strategy to meet the bar of the check.
- Difficulties: No difficulties with the tool. It identified an inadequacy and told me how to fix it.
- What changed: No changes to the tool. It provided guidance on what was wrong with my existing testing strategy and how to fix it which I incorporated into my plan.

---

## Implementation Notes


**[11-14-2026]**

I implemented the updated robots.txt per guidance from Claude. It recognized that my naive implementation of the file (based off of the issue guidance from the maintainer), would disrupt intended functionality (derived from some of the other objectives in the issue).

I added noindex to the root head of the routes, making all pages noindex by default. This slightly deviated from my understanding of the solution as I thought I'd be applying noindex to specific authenticated routes as an override but instead noindex is the default and we are overriding it on the landing page to allow indexing.

Finally, I added the index, follow override to the landing page to allow it to be indexed.


**Toolkit**

- Tool: Claude CLI identified some problems in the original plan which contributed to my better understanding, and thus, better implementation of the solution. I specifically asked it to verify my work against the plan (and against reasonable expectations) which highlighted the issues and their solutions.
- What it produced: Textual guidance.
- Difficulties: No difficulties with the tool.
- What changed: My plan changed from my original naive solution when given guidance from Claude. Nothing changed, tool-wise.

---

## Pull Request

**PR Link:** https://github.com/lolimmlost/aidj/pull/418

**PR Description:**

## What & why

Fixes #276

Adds `public/robots.txt` with rules disallowing everything but:
- the landing page (`/$`)
- `/assets/` (Google renders pages, and if it can't load these the landing page looks empty or broken to it)
- `/og-image.png` (for social previews)
- `/favicon.ico`, `/icons/`, `/manifest.json` (Favicon and PWA metadata that search results and browsers show next to the site)
- `/music-identity/share/` (public share links which need to be fetchable for link previews)
- `/playlists/join/` (same reasoning)
- `/invite` (same reasoning)

The exceptions were surfaced by AI. Looking into them, it seems to make sense to allow them given the expressed intent to have share links, etc.

Adds `noindex` to the root head.

Adds `index, follow` override to the landing page.

## How it was tested

I had AI devise suitable tests for a change like this and had it run it, producing this output:

### 1. `public/robots.txt` is served

`curl -si localhost:3004/robots.txt` → `HTTP/1.1 200 OK`, `Content-Type: text/plain`

```
User-agent: *
Allow: /$
Allow: /assets/
Allow: /og-image.png
Allow: /favicon.ico
Allow: /manifest.json
Allow: /icons/
Allow: /music-identity/share/
Allow: /playlists/join/
Allow: /invite
Disallow: /
```

### 2. Robots meta tags in SSR output

Command: `curl -s localhost:3005<path> | grep -oE '<meta [^>]*>' | grep -E 'robots|og:|twitter:'`

| Path | Status | robots meta | og:/twitter: tags |
|------|--------|-------------|-------------------|
| `/` | 200 | `index, follow` (only one robots tag — the route override replaces the root `noindex`) | present |
| `/login` | 200 | `noindex` | present |
| `/music-identity/share/abc123` | 200 | `noindex` | present (og:title, og:description, og:image, twitter:card, twitter:image, …) |
| `/invite` | 200 | `noindex` | present |
| `/dashboard` | 307 → `/login?redirect=%2Fdashboard` | n/a (unauthenticated) | n/a |
| `/playlists/join/abc123` | 307 → `/login?redirect=…` | n/a (unauthenticated) | n/a |

Example (`/music-identity/share/abc123`):

```html
<meta name="robots" content="noindex"/>
<meta property="og:title" content="AIDJ"/>
<meta property="og:description" content="AI-powered music discovery and smart playlists"/>
<meta property="og:image" content="http://localhost:3000/og-image.png"/>
<meta name="twitter:card" content="summary_large_image"/>
<meta name="twitter:image" content="http://localhost:3000/og-image.png"/>
```

The share route defines no `head()` of its own, so its tags come from the root route. A real share token would render the same `<head>` as the dummy token used here.

### 3. Existing checks

- `npx vitest run` → `Test Files 85 passed | 3 skipped (88)`, `Tests 1041 passed | 26 todo (1067)`
- `npm run lint` → `0 errors, 392 warnings`. The only warning in a changed file (`src/routes/__root.tsx:35`, `ensureQueryData` deprecated) is on a line this PR did not touch.
- `npm run build` → exit 0, `✓ built`

## Checklist
- [x] `npx vitest run` passes
- [x] `npm run lint` passes on touched files
- [x] `npm run build` succeeds (commit `src/routeTree.gen.ts` if routes changed)
- [x] Migrations included for schema changes
- [x] No unrelated dependency bumps (especially `better-auth`)

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** Awaiting Review

**Toolkit**

- Tool: ship-gate was used to judge a pr as worthy before actually creating it. It runs tests, applies various PR rubrics to the pr draft, checks the writing against a voice guard, and even judges the solution against the issue.
- What it produced: It produces an accept/reject verdict for the PR. It provides various tips and recommendations for changes.
- Difficulties: No difficulties using the tool.
- What changed: It changed a few formatting things to align my pr description with one of my voice guard rules. Nothing changed regarding the tool itself.

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
