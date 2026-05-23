# Site Playbooks

Per-site opt-out procedures for the 12 covered brokers, plus the network/sister-site map and the verification-window cheat sheet. Verified against current (2026) reputable privacy guides. The brokers themselves block automated fetchers (they return 403 to non-browser requests), so URLs and steps are confirmed via guides rather than live scrapes — **treat exact button labels and field layouts as "expected," and adapt to what the live page actually shows.**

## Contents

1. [Quick reference: verification & expiry windows](#quick-reference)
2. [Network & sister-site map](#networks)
3. TruePeopleSearch · 4. FastPeopleSearch · 5. Nuwber · 6. Radaris · 7. Whitepages · 8. Spokeo · 9. BeenVerified · 10. MyLife · 11. Intelius (PeopleConnect) · 12. PeopleFinders · 13. USPhonebook · 14. CheckPeople

---

<a name="quick-reference"></a>
## 1. Quick reference: verification & expiry windows

| Site | Opt-out URL | Find listing first? | Verification | Time-box | CAPTCHA |
|---|---|---|---|---|---|
| TruePeopleSearch | `/removal` | Yes (in-flow search) | Email link | — | Yes (1) |
| FastPeopleSearch | `/removal` | Yes (in-flow search) | Email link | — | Yes — **stacks/escalates** |
| Nuwber | `/removal/link` | Yes (paste profile URL) | Email link | — | Not reported |
| Radaris | `/control-privacy` | Yes (paste profile URL) | Email link | email may take 30+ min | **Two CAPTCHA gates** |
| Whitepages | `/suppression-requests` | Yes (paste profile URL) | **Automated phone call + on-screen code** | finish in one sitting | — |
| Spokeo | `/optout` | Yes (paste profile URL) | Email link | — | reCAPTCHA |
| BeenVerified | footer "Do Not Sell…" link | Yes (select from results) | Email link | **~48 h link** | "I am human" |
| MyLife | `/ccpa/index.pubview` | Yes (paste profile URL) | CAPTCHA + email | recheck ~15 days | reCAPTCHA-style |
| Intelius (PeopleConnect) | `suppression.peopleconnect.us` | No (it surfaces records) | **Email link (~15 min) + 2nd code (email/phone)** | **~15 min link** | Assume yes |
| PeopleFinders | `/opt-out` | No | Email link | **~24 h link** | **Two CAPTCHAs** |
| USPhonebook | `/opt-out` | Yes (in-flow search) | Email link | **~24 h link** | reCAPTCHA |
| CheckPeople | `/opt-out` | Yes (in-flow search) | Email link | — | **hCaptcha, twice** |

Every site is free, requires no real account (except Intelius' suppression login), and re-lists over time.

<a name="networks"></a>
## 2. Network & sister-site map

One opt-out does **not** equal full coverage. Key relationships:

- **PeopleConnect (one suppression covers all):** Intelius, TruthFinder, Instant Checkmate, US Search, ZabaSearch, Classmates.com, Addresses.com, PeopleLookup, DateCheck, PublicRecords.com. Do Intelius' suppression once → the family is covered.
- **TruePeopleSearch ↔ FastPeopleSearch:** same operator (per Krebs, 2024), but **separate opt-outs**. Also separate TLD copies: `truepeoplesearch.info` / `.net` / `.io` each need their own opt-out.
- **Radaris fleet (each separate):** Centeda, Trustoria, BizStanding, Homemetry, Rehold, Virtory, ClubSet, NewEnglandFacts, Pub360, HomeFlock, DiFive, ProjectLab. Radaris removal does not clear these; Centeda and Trustoria especially need their own.
- **BeenVerified / The Lifetime Value Co. (treat as separate until verified):** PeopleLooker, NeighborWho, Ownerly, NumberGuru, Bumper, PeopleSmart. Sources conflict on whether one opt-out cascades — opt out of each and verify.
- **Whitepages → 411.com:** same data, separate opt-out.
- **Spokeo:** no sister network, but creates **multiple profiles per person** (name variants, different emails/addresses) — each profile URL is its own opt-out.

---

## 3. TruePeopleSearch

- **Opt-out URL:** `https://www.truepeoplesearch.com/removal` (or footer → "Do Not Sell or Share My Personal Information").
- **Steps:**
  1. Open `/removal`. Enter **email**, tick the agreement box, pass the "I am human" check, click **Begin Removal**.
  2. A search opens — search by **first name, last name, city, state**.
  3. Find the listing, click **View Details**.
  4. Scroll the record, click **Remove This Record**.
  5. Open the confirmation email → click the verification link to finalize.
- **Required:** email; name; city; state. No DOB/phone/account.
- **Verification:** email link + one CAPTCHA on the first step.
- **Processing:** ~72 h best case, ~1–2 weeks realistic.
- **Gotchas:** multiple listings each need a separate submission (same email is fine). `.info`/`.net`/`.io` are separate sites. Relisting is common — recheck periodically.

## 4. FastPeopleSearch

- **Opt-out URL:** `https://www.fastpeoplesearch.com/removal`.
- **Steps:**
  1. Open `/removal`. Enter **email**, tick the terms box, complete CAPTCHA, click **Begin Removal Process**.
  2. Enter **full name, city, state** → **Free Search**.
  3. Find the listing → **View Free Details**.
  4. Click the red **Remove My Record**.
  5. Open the verification email → click the confirmation link.
- **Required:** email + name/city/state.
- **Verification:** email link. **CAPTCHA escalates** — Security.org reports up to half a dozen in one session; expect to hand off to the operator.
- **Processing:** 24–72 h after verification.
- **Gotchas:** sister of TruePeopleSearch (separate opt-out). Duplicate listings common.

## 5. Nuwber

- **Opt-out URL:** `https://nuwber.com/removal/link` (in-product: HELP → "Remove My Info").
- **Steps:**
  1. Search yourself on nuwber.com (name+location, phone, address, or email).
  2. Open your record, copy the **profile URL**.
  3. On `/removal/link`, paste the profile URL → **Opt Out**.
  4. Enter **email** → **Remove**.
  5. Open the email → **Confirm Request**.
- **Required:** Nuwber profile URL + email.
- **Verification:** email link (usually <1 min; check spam). No CAPTCHA reported.
- **Processing:** often <24 h, up to ~48 h.
- **Gotchas:** per-URL — common names/old addresses create multiple listings, each its own URL. Support: (844) 912-1292.

## 6. Radaris

- **Opt-out URL:** `https://radaris.com/control-privacy` (also `/data_privacy_center`; footer "Remove My Info").
- **Steps:**
  1. Search yourself, open your profile → **View Profile**, copy the **profile URL**.
  2. On control-privacy, enter **full name, city, state, profile URL** → **Next**.
  3. Confirm identity / **Start Removing**, click through the loading screens.
  4. Enter **email**, complete **CAPTCHA**, **Submit**.
  5. Click the **email confirmation link**.
  6. Return, pass a **second CAPTCHA**, **Submit** again for the confirmation message.
- **Required:** full name, city, state, profile URL, email.
- **Verification:** email link + **two CAPTCHA gates**. Email can take **30+ minutes**.
- **Processing:** ~24 h.
- **Gotchas:** heaviest friction of the free sites. Part of a large affiliated fleet (see network map) — those need separate opt-outs.

## 7. Whitepages

- **Opt-out URL:** `https://www.whitepages.com/suppression-requests`.
- **Steps:**
  1. Search name + city + state.
  2. Click **View Details** on your listing (use **View Full Report** for a Premium listing).
  3. Copy the **profile URL**.
  4. On the suppression page, paste the URL → **Next**.
  5. Confirm the details → **Remove Me**.
  6. Pick a removal reason from the required dropdown.
  7. Enter a **phone number**; the page shows a verification code.
  8. **Answer the automated phone call** and key in / confirm the on-screen code.
  9. See the submitted confirmation.
- **Required:** profile URL, removal reason, working phone number.
- **Verification:** **real-time automated phone call** with an on-screen code — **operator must do this** (you can't). No email path.
- **Processing:** ~24 h.
- **Gotchas:** standard opt-out does **not** remove **Premium** listings — handle those via "View Full Report." Each listing separate. **411.com** is a separate sister-site opt-out.

## 8. Spokeo

- **Opt-out URL:** `https://www.spokeo.com/optout` (or footer "Do Not Sell My Info").
- **Steps:**
  1. Search your name (then refine by email/phone/address), open the matching profile, copy its **URL**.
  2. On `/optout`, scroll to the form (oddly labeled "opt out your information").
  3. Paste the **profile URL** + **email**.
  4. Complete **reCAPTCHA** → **Opt Out**.
  5. Open the email → click the verification link.
  6. Recheck the saved URL after 24–72 h for "No Results Found."
- **Required:** profile URL + email.
- **Verification:** reCAPTCHA + email link.
- **Processing:** 24–72 h.
- **Gotchas:** multiple profiles per person — each URL is a separate opt-out. Re-lists every ~3–6 months. Use an alias email to dodge marketing.

## 9. BeenVerified

- **Opt-out URL:** reach via homepage footer **"Do Not Sell or Share My Personal Information"** (most reliable). Direct path is under `/app/optout/` but the exact URL varies — use the footer link.
- **Steps:**
  1. Open the opt-out search (via footer link).
  2. Search **full name + state**.
  3. Click **Opt Out / Proceed to Opt Out** next to your record.
  4. Enter **email**, complete the "I am human" check.
  5. Open the email (within ~5 min; **link expires ~48 h**) → click the green **Verify Opt-Out**.
- **Required:** full name, state, email. No profile-URL paste (you select from results).
- **Verification:** "I am human" + email link (**~48 h expiry**).
- **Processing:** 24–72 h (sometimes up to ~7 business days).
- **Gotchas:** **one opt-out per email address** — multiple listings may need emailing them directly. Sister brands (PeopleLooker, NeighborWho, Ownerly, etc.) likely need separate opt-outs.

## 10. MyLife

- **Opt-out URL:** `https://www.mylife.com/ccpa/index.pubview` (the CCPA form; buried at the footer / FAQ #11).
- **Steps:**
  1. Search your name, open your "Reputation Profile," copy the **profile URL**.
  2. On the CCPA form, fill required fields, paste the **profile URL**.
  3. Solve the **CAPTCHA** ("I'm not a robot").
  4. Submit; watch for a confirmation email (may take 24–48 h).
- **Required:** first/last name, state, profile URL, email; optional CA-resident checkbox.
- **Verification:** CAPTCHA + email confirmation (be ready for an email-link click).
- **Processing:** 1–2 weeks; recheck ~15 days. Re-appears often.
- **Gotchas:** the worst dark patterns — alarming "Reputation Scores"/criminal teasers funnel you toward **paid** subscriptions; the free CCPA path is intentionally obscured. Email fallback for reputation-profile removal: `membersupport@mylife.com`. Phone: (888) 704-1900. Use a disposable email.

## 11. Intelius (PeopleConnect Suppression Center)

- **Opt-out URL:** `https://suppression.peopleconnect.us/login` (Intelius footer → "Do Not Sell or Share My Personal Information" → "View Public Data Tools" → "Manage My Suppression Rules").
- **Steps:**
  1. From the footer, reach **Manage My Suppression Rules** (opens suppression.peopleconnect.us).
  2. Enter **email**, agree to terms.
  3. Open the verification email → **Verify Email** (**link expires ~15 min** — finish in one sitting).
  4. Enter **date of birth** (**cannot be changed later**).
  5. Enter your **complete legal name** (add aliases/maiden names).
  6. Select your record(s).
  7. Complete a **second verification** (code via email or phone).
  8. Set status to **Suppressed** and save.
- **Required:** email, DOB, full legal name, optional aliases, record selection, second code.
- **Verification:** email link (**~15 min**) + a second email/phone code.
- **Processing:** ~72 h, up to 10 business days across the family.
- **Gotchas (upside):** **one suppression covers the whole PeopleConnect family** (TruthFinder, Instant Checkmate, US Search, ZabaSearch, Classmates, etc.). The 15-minute window is tight — have the operator's inbox ready before starting.

## 12. PeopleFinders

- **Opt-out URL:** `https://www.peoplefinders.com/opt-out` (or footer "Do Not Sell My Personal Information"; related: `/remove-my-info`).
- **Steps:**
  1. Open `/opt-out`, choose **public record removal** → **Next**.
  2. Enter **name + email**, solve **CAPTCHA**, **Send Request**.
  3. Open the confirmation email → click the link (**expires ~24 h**).
  4. On the record form, fill the required (asterisked) fields to locate your profile.
  5. Solve **CAPTCHA again** → submit.
  6. Recheck after clearing cache.
- **Required:** name + email; then locating fields on the second form.
- **Verification:** email link (**~24 h**) + **two CAPTCHAs**.
- **Processing:** 3–7 days (up to ~15).
- **Gotchas:** independent (not PeopleConnect) — covers only peoplefinders.com.

## 13. USPhonebook

- **Opt-out URL:** `https://www.usphonebook.com/opt-out` (or footer "Do Not Sell My Personal Information").
- **Steps:**
  1. Open `/opt-out`, check both consent boxes, enter **email**.
  2. Complete **CAPTCHA**.
  3. Search by name + city/state (or phone/address).
  4. Open your listing → **Remove Record**.
  5. Open the email → click the removal link (**expires ~24 h**).
- **Required:** email + two consent checkboxes; name/city/state to locate.
- **Verification:** email link (**~24 h**) + reCAPTCHA.
- **Processing:** within 72 h (sometimes ~12 h).
- **Gotchas:** support (888) 747-4095. Often grouped with Spokeo but no confirmed shared opt-out — treat as separate.

## 14. CheckPeople

- **Opt-out URL:** `https://checkpeople.com/opt-out` (footer "Do Not Sell or Share My Personal Information" → `/do-not-sell-info` routes to the same flow).
- **Steps:**
  1. Open `/opt-out`. Enter **full name, city, state** (exactly as listed).
  2. Solve **CAPTCHA** → **Search**.
  3. Find your record → **Remove Record / Opt-Out**.
  4. Enter **name + email**, solve **CAPTCHA again** → **Submit Request**.
  5. Open the email (check spam) → click the verification link.
- **Required:** name/city/state to find; name + email to confirm.
- **Verification:** **hCaptcha twice** + email link.
- **Processing:** ~5–7 days.
- **Gotchas:** phone (800) 267-2122. Email fallback asks for full name, DOB, current/past addresses, and the profile URL. Independent — covers only checkpeople.com.
