# identity-eraser

A [Claude Code](https://claude.com/claude-code) skill that removes **your own** personal information from the major people-search sites and data brokers, then verifies it's gone — driving **your** authenticated browser so every request is made by you, about you.

It works in two phases:

1. **Discovery (read-only):** searches each broker for your listing and reports exactly what's exposed — name, addresses, phone numbers, relatives, age — as a table, *before* anything is changed.
2. **Scrub:** opens each site's official (free) opt-out form, fills and submits it one site at a time, and logs the status of each, handing back to you only when a human is genuinely required (an image CAPTCHA, an SMS code, a verification phone call).

## Sites covered

Whitepages · Spokeo · BeenVerified · TruePeopleSearch · Nuwber · Radaris · MyLife · Intelius (and the whole PeopleConnect family) · PeopleFinders · FastPeopleSearch · USPhonebook · CheckPeople — plus notes on their sister/network sites.

## How it's designed

- **Your data never leaves your machine.** The skill is a generic template: it asks *whoever runs it* for their info at runtime and uses it only inside the live browser session. No personal information is stored in this repo or transmitted anywhere except into the brokers' own removal forms.
- **It only ever removes the operator's own listing.** People-search results are full of namesakes and relatives; the skill confirms identity with at least two signals (DOB/age, a known address, a relative's name) before acting, and stops to ask if a match is uncertain. It never opts out anyone but you.
- **It runs in a real, authenticated browser** (via Claude-in-Chrome), because every one of these brokers blocks automated requests — and because acting in your own session is what makes this a legitimate self-service privacy action.

## Requirements

- Claude Code with the **Claude-in-Chrome** browser extension connected to your Chrome.
- You signed into your email in that browser (brokers send verification links there).
- You present during the run for SMS/phone/CAPTCHA steps.

## Install

Clone into your Claude Code skills directory:

```bash
# personal skills live in ~/.claude/skills/
git clone https://github.com/akcodez/identity-eraser.git ~/.claude/skills/identity-eraser
```

Then in Claude Code just say something like *"erase my personal info from the data brokers"* and the skill will trigger.

## Usage

Once it triggers, the skill will:

1. Ask you for the details it needs (name + variants, DOB, current/past addresses, phones, emails, relatives' first names for matching).
2. Run **Phase 1** and show you a discovery table — what each site exposes — and wait.
3. Run **Phase 2**, working each listed site to completion and logging `submitted` / `pending verification` / `needs manual step` / `blocked` / `removed-confirmed`.
4. Hand you a final report with your remaining to-dos (verification links, manual steps) and recommend a recheck in 3–6 months, since brokers re-list over time.

See [`SKILL.md`](./SKILL.md) for the full workflow and [`references/site-playbooks.md`](./references/site-playbooks.md) for the per-site opt-out procedures, verification windows, and network map.

## Notes & disclaimer

- **For your own data only.** This automates the same free opt-out forms these brokers are required to provide; it is not for removing information about other people.
- Opt-outs are free. If a site demands payment to remove a listing, that's an upsell funnel, not the official removal — the skill backs out of those.
- Removal isn't permanent: brokers re-scrape public records and re-list people over weeks to months. Re-run periodically.
- This is a privacy tool, not legal advice.

## License

MIT — see [`LICENSE`](./LICENSE).
