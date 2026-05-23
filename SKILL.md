---
name: identity-eraser
description: >-
  Erase a person's personal information from people-search sites and data brokers, and confirm it's gone.
  Drives the operator's OWN authenticated browser (via Claude-in-Chrome) to (1) discover which brokers expose
  their name, address, phone, age, and relatives, then (2) submit each site's official opt-out / removal
  request one at a time, logging status and handing off to the operator only for verification codes.
  Covers Whitepages, Spokeo, BeenVerified, TruePeopleSearch, Nuwber, Radaris, MyLife, Intelius, PeopleFinders,
  FastPeopleSearch, USPhonebook, CheckPeople and similar sites. Use this whenever the user wants to remove,
  delete, scrub, suppress, hide, or opt out their personal info / PII from the internet, data brokers, or
  people-search sites; reduce doxxing, stalking, or harassment exposure; "get my information taken down"; or
  protect their online privacy — even if they don't name a specific site.
---

# Identity Eraser

A workflow for removing one person's personal information from the major people-search sites and data brokers, then verifying the removals. It runs in the operator's own browser through Claude-in-Chrome, so every request is made *as the operator*, by the operator, about the operator.

## What this does, in one breath

For each target broker: find out whether the operator is listed and what's exposed (Phase 1, read-only), show them the picture, then walk the official opt-out form on each site where they're listed and submit it (Phase 2), pausing only when a human is genuinely required — a CAPTCHA image challenge, an SMS code, a phone call. Everything is logged so the operator ends with a clear record of what was submitted and what still needs follow-up.

## The one rule that matters most: scope

**Only ever act on the data of the person running this skill — the "subject" — who is the operator of this browser.** This is a self-service privacy tool: a person removing their *own* information using their *own* authenticated session. That framing is the entire justification for the skill, so protect it:

- Never submit a removal, suppression, or opt-out for anyone who is not the subject. People-search results are full of namesakes and relatives; removing the wrong person's listing is both wrong and, for the subject, useless.
- Before you act on any listing, **confirm it's actually the subject** using at least two corroborating signals — date of birth/age, a known current or past address, or a known relative's name. If the match is ambiguous, **stop and ask the operator** rather than guessing.
- Relatives' names are collected for *matching only*. They are how you tell the subject's record apart from a stranger's. They are never themselves a target.
- Everything is free. If a site tries to charge to remove a listing, that's a funnel, not the opt-out — back out and find the official (free) suppression form, or log the site as "needs manual review."

If you ever feel the task drifting toward acting on someone other than the subject, treat that as a hard stop and check in.

## Authorization & autonomy

Invoking this skill *is* the operator authorizing action on their own behalf — they are removing their own data from their own browser session. So **run autonomously**: don't stop to ask "should I click submit?", "should I opt out of this one?", or "is it OK to proceed?" for the routine discovery and opt-out steps. Acting on those is the whole point.

Pause and hand off **only** when a human is genuinely, mechanically required:

- an image CAPTCHA / hCaptcha / escalating challenge you can't clear,
- an SMS code or a live verification phone call,
- an email confirmation link you cannot reach in the browser.

For everything else — filling forms with the subject's info, clicking "Remove," "Opt Out," "Submit," accepting a site's opt-out terms, declining cookies — proceed. The scope rule above (act only on the subject's own records, confirm identity first) is the real guardrail; per-step confirmation is not, and asking for it just stalls a task the operator already greenlit.

## Prerequisites

1. **Claude-in-Chrome connected**, pointed at the operator's own Chrome where they are signed into their email (the brokers send verification links there). The browser tools are MCP tools that must be loaded before use — load them with `ToolSearch` (`select:mcp__claude-in-chrome__tabs_context_mcp`, `...navigate`, `...get_page_text`, `...read_page`, `...find`, `...form_input`, `...computer`, `...gif_creator`, `...browser_batch`) at the start of a run.
2. **Browser actions enabled.** In the Claude-in-Chrome extension, allow Claude to act on these sites (allowlist them or set "always allow") so the run isn't interrupted by per-action prompts.
3. **The operator is present** during the run, because some sites can only be finished by a human (SMS codes, phone-call verification, image CAPTCHAs).
4. Confirm the live browser state first with `tabs_context_mcp`, then open a fresh tab to work in. Never reuse a tab from another session.

## Step 0 — Collect the subject's profile

Ask the operator for the information below. Explain that it's used only inside this session to find and submit *their* removals, and that it must **never be written into the skill files or committed anywhere** — keep it in conversation, or in a scratch log stored outside any git repository.

Collect:

- **Full legal name**, plus every variant: maiden/former names, common misspellings, nicknames, suffix (Jr./Sr./III). Brokers index all of these separately.
- **Date of birth (or age).** This is the single best disambiguator against namesakes.
- **Current address** (street, city, state, ZIP).
- **Previous addresses**, especially the last ~10 years. Brokers feature old addresses heavily, and several forms ask you to confirm them.
- **Phone number(s)** — cell and any landline.
- **Email address(es)** to scrub, plus **one email the operator can check right now** for confirmation links.
- **Close relatives' first names** (parents, siblings, spouse) — for matching only.

Start a **status log** (see "Logging") and record these as the search inputs.

## Phase 1 — Discovery (read-only, safe)

Walk the target sites (see the list and per-site search tips in `references/site-playbooks.md`). For each one:

1. Open the site's people search and query the subject's **name + city + state**; widen with previous cities if nothing matches.
2. In the results, identify the listing(s) that are actually the subject by cross-checking **age/DOB, an address, or a relative's name**. Note when there are several listings — common names, name variants, and old addresses each spawn their own record, and **each is a separate removal later**.
3. Capture, for the log: whether the subject is listed, **what's exposed** (full name, current/past addresses, phone numbers, relatives, age/DOB, anything sensitive), and the **exact profile URL(s)** — most opt-out forms need the URL.

Then **present the discovery table to the operator before scrubbing anything** — this is a deliberate checkpoint, not a formality. Use this shape:

```
| Site | Listed? | Exposed (name / address / phone / relatives / age) | Profile URL(s) | Notes |
```

## Phase 2 — Scrub (one site at a time)

Read `references/site-playbooks.md` first — it has the verified opt-out URL, exact steps, required fields, verification method, expiry windows, and network/sister-site notes for each site. Then, for every site where the subject is listed, work it to completion before moving on (doing them one at a time keeps the log honest and avoids half-finished submissions):

1. Open the site's **official opt-out page** from the playbook.
2. Fill the form with the subject's info. Where the form wants a profile URL, use the one captured in Phase 1.
3. Submit, then handle whatever gate appears (see the handoff protocol below).
4. **Log the outcome** with one of these statuses, plus the timestamp and the next action:
   - `submitted` — request sent, no further action expected.
   - `pending verification` — an email link / SMS code is required to finalize (note the expiry window!).
   - `needs manual step` — a human-only step blocks completion (image CAPTCHA, phone call, account creation, paid funnel).
   - `blocked` — the site won't load or actively refused; note the symptom.
   - `removed-confirmed` — re-checked and the listing is gone.
5. Move to the next site.

### Verification & CAPTCHA handoff protocol

The operator should only have to step in when a human genuinely must:

- **Simple "I'm not a robot" checkbox:** attempt it yourself.
- **Image challenge / hCaptcha / escalating CAPTCHAs** (FastPeopleSearch is notorious for stacking these): pause, ask the operator to solve it in the browser, then continue.
- **Email confirmation link:** the operator is signed into their email in this very browser, so open their webmail in a tab and click the link yourself when possible; only ask the operator if you can't locate it. **Mind the expiry windows** — Intelius ~15 min, PeopleFinders/USPhonebook ~24 h, BeenVerified ~48 h — so don't queue these; finish each as it arrives.
- **SMS code or live phone call** (e.g., Whitepages' automated call): you cannot do this — hand off to the operator, tell them exactly what code/page to expect, and wait.

Never trigger a JavaScript `alert`/`confirm`/`prompt` dialog; it freezes the browser tools. If a page has a "Delete"/confirm dialog, warn the operator before interacting.

### Browser tactics

- Begin with `tabs_context_mcp`; open a new tab with `tabs_create_mcp`.
- Read pages with `get_page_text` / `read_page`; locate fields with `find`; type with `form_input`; click via `computer` when needed.
- These sites hard-block non-browser fetchers (they 403 automated requests) — that's expected and is why we're in a real browser. If a *page* still won't load or throws bot walls repeatedly, don't hammer it: log `blocked` and tell the operator.
- Optionally record each scrub with `gif_creator` so the operator has a visual receipt (capture a few frames before and after each action for smooth playback). Name files per site, e.g. `truepeoplesearch_removal.gif`.
- If browser calls fail 2–3 times or the extension stops responding, stop and ask the operator rather than looping.

## Logging & final report

Maintain a running status log throughout (a Markdown table is fine), and finish with a report the operator can act on:

```
| Site | Listed? | Action taken | Status | Verification needed | Next step / recheck date |
```

Call out anything in `pending verification` or `needs manual step` at the top — those are the operator's to-dos.

## After the run: monitoring & re-listing

Removal is not permanent. Brokers re-scrape public records and re-list people over weeks to months, so recommend re-running this every **3–6 months**. Also flag **network/sister sites**: one opt-out sometimes clears a whole family (a single PeopleConnect suppression covers Intelius, TruthFinder, Instant Checkmate, US Search, ZabaSearch, and more), while other networks need each property done separately (Radaris's affiliated fleet; BeenVerified's sister brands; Whitepages' 411.com; the TruePeopleSearch/FastPeopleSearch pair and their `.info`/`.net`/`.io` variants). The playbook notes which is which.
