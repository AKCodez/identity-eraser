<div align="center">

# 🫥 Identity Eraser

### Wipe your personal info off the internet — automatically.

*Your name, home address, phone number, age, and relatives are sitting on dozens of "people-search" sites right now. Anyone can look you up in seconds. This erases you from them.*

<br>

![Runs in your own browser](https://img.shields.io/badge/runs_in-your_own_browser-6c5ce7?style=for-the-badge)
![Your data stays on your machine](https://img.shields.io/badge/your_data-never_leaves_your_machine-00b894?style=for-the-badge)
![Free opt-outs only](https://img.shields.io/badge/cost-100%25_free-0984e3?style=for-the-badge)
![License MIT](https://img.shields.io/badge/license-MIT-636e72?style=for-the-badge)

</div>

---

## 😨 The problem

Type your own name into Google and you'll find sites like **Spokeo, Whitepages, and BeenVerified** showing:

- 🏠 Your current and past home addresses
- 📞 Your phone numbers
- 🎂 Your age and birthday
- 👨‍👩‍👧 Your family members' names

They scraped it from public records and now they sell it — to anyone. Stalkers, scammers, and creeps use these sites every day. You can opt out of each one by hand… but there are dozens, every form is different, and they re-list you every few months. Nobody has time for that.

**Identity Eraser does it for you.**

---

## ✨ How it works

It runs as a [Claude Code](https://claude.com/claude-code) skill inside **your own browser**, in two simple phases:

```
   PHASE 1 — SEE IT                    PHASE 2 — ERASE IT
   ┌────────────────────┐              ┌────────────────────┐
   │  🔍 Scans every     │              │  🧹 Opens each      │
   │     data broker     │   ────────▶  │     opt-out form    │
   │     for your name   │              │     and submits it  │
   │                     │              │     for you         │
   │  Shows you exactly  │              │                     │
   │  what's exposed     │              │  Logs what's done   │
   └────────────────────┘              └────────────────────┘
        (read-only —                       (you only step in
      changes nothing yet)               for the occasional code)
```

> **Phase 1 — Discovery:** It searches each site and hands you a clean table: *here's what Spokeo has on you, here's what Whitepages has on you.* Nothing is changed yet — you just see the damage.
>
> **Phase 2 — Erase:** It opens each site's official removal form, fills in your details, and submits it — one site at a time — keeping a running log. It only pauses to tap you on the shoulder when a human is truly required (an image CAPTCHA, a text message code, a verification call).

---

## 🔒 Is this safe? (Yes — here's why)

This is the part that matters most, so read it:

| ✅ | What that means for you |
|----|--------------------------|
| **Your data never leaves your computer** | The skill asks for your info *while it's running* and uses it only inside your live browser. Nothing is saved, uploaded, or stored anywhere — except typed into the brokers' own removal forms. |
| **It only ever removes _you_** | People-search sites are full of strangers with your name. The skill confirms it's really you (using your age + an address + a relative's name) before touching anything. If it's not sure, it stops and asks. |
| **It runs as _you_, in _your_ browser** | Every request comes from your own signed-in session — which is exactly what makes this a legitimate "remove my own info" request, not hacking. |
| **It's completely free** | Real opt-outs are always free. If a site tries to charge you to be removed, that's a scam funnel — the skill backs out and flags it. |

---

## 🧰 What you need

- [ ] **Claude Code** with the **Claude-in-Chrome** extension connected to your Chrome
- [ ] You're **signed into your email** in that browser (the sites email you verification links)
- [ ] You're **around during the run** to tap in codes / solve the odd CAPTCHA

That's it. No coding, no accounts, no payment.

---

## 📥 Install

Paste this into your terminal:

```bash
git clone https://github.com/akcodez/identity-eraser.git ~/.claude/skills/identity-eraser
```

Then open Claude Code and just say:

> **"Erase my personal info from the data brokers."**

The skill takes it from there.

---

## ▶️ How to use it

1. **It asks for your details** — name (and any old/maiden names), age, current + past addresses, phone, and your relatives' first names (used *only* to tell your record apart from strangers').
2. **It shows you the damage** — a table of what each site is exposing. Take a breath.
3. **It erases you** — works through every site that listed you, marking each one: `submitted` · `pending your verification` · `needs a manual step` · `removed`.
4. **It hands you a report** — anything left for you to finish (a link to click, a code to enter), plus a reminder to re-run in 3–6 months.

---

## 🌐 What it covers

> Whitepages · Spokeo · BeenVerified · TruePeopleSearch · Nuwber · Radaris · MyLife · Intelius *(and the whole PeopleConnect family)* · PeopleFinders · FastPeopleSearch · USPhonebook · CheckPeople — plus their sister sites.

The full per-site playbook lives in [`references/site-playbooks.md`](./references/site-playbooks.md), and the complete workflow is in [`SKILL.md`](./SKILL.md).

---

## 💡 Good to know

- **This is for _your own_ info only.** It automates the same free removal forms the law requires these sites to offer. It is not for looking up or removing anyone else.
- **Removal isn't forever.** These sites re-scrape public records and quietly re-list you over the following months. Re-run it a few times a year to stay invisible.
- **Some steps need you.** CAPTCHAs and text-message codes are designed to stop robots — so the skill hands those to you and keeps going after. That's by design.
- **This is a privacy tool, not legal advice.**

---

<div align="center">

**Built for everyone who never agreed to be this easy to find.**

MIT licensed · See [`LICENSE`](./LICENSE)

</div>
