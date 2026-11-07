# HOM-261 — Outpost Coder review of terms-license.html (DRAFT v0.1-draft, db51860)

Reviewer: Outpost Coder. Scope: technical-consistency + publish-readiness.
This is NOT legal advice and NOT owner sign-off. Owner (Packet / Coldblooded
Games) must approve the legal text before it is linked from Play Console or
promoted as final.

## Blocking inconsistencies found in db51860 (fix before publish)

1. **Footer link contradicts draft banner.** terms-license.html says
   "Footer links from the home page are hidden in draft state", but
   index.html:128 links it live: `<a href="terms-license.html">Terms / License</a>`.
   As committed, the draft is publicly reachable from the home page.
   Fix (pick one, owner to confirm): (a) remove/comment the footer link until
   sign-off — preferred, matches banner + README "do not link until approved";
   or (b) keep link and remove banner — not recommended pre-sign-off.
   Noindex: add `<meta name="robots" content="noindex">` to the draft page
   in the meantime so search engines do not index draft legal copy.

2. **Privacy Policy contact says two places.** privacy-policy.html (v1.0,
   ship-ready) says "or through the support email listed on the Google Play
   Store listing" — implies a second channel. Keep contact consistent:
   support@coldbloodedgames.com only (Terms already does this). Also
   privacy-policy.html and docs/store/privacy-policy.html in crown-outpost
   are byte-identical — keep them in sync (single source; diff before push).

3. **No governing law / jurisdiction / limitation-of-liability cap.**
   Section 4 ("No warranty") says "to the maximum extent permitted by law"
   but the draft names no jurisdiction, no liability cap, no indemnity,
   no termination, no assignment/severability, and no age/children clause.
   Whether any of these are needed is a legal call for the owner/advisor,
   not for Outpost Coder to invent. Flagged here so sign-off is informed;
   do not publish Play-Console-linked terms with a blank effective date.

4. **Effective date still "[PENDING OWNER SIGN-OFF]".** Correct for a draft,
   but the page must not be linked from Play Console until a real date +
   version bump (suggest v1.0) replaces the placeholder.

## Non-blocking polish (optional, pre-sign-off)

- Terms §5 "collects no personal data" matches Privacy Policy v1.0 + Data
  Safety draft (HOM-249) + shipped build (no INTERNET permission, no SDKs) —
  consistent, good. Keep the two pages' claims worded identically.
- Terms §3 copyright year 2026 Coldblooded Games matches home footer — good.
- §2 "shipped binaries or assets" ban is broader than typical consumer EULAs
  (modding/UGC carve-outs are a policy choice — owner decision).
- Missing in-app-purchase/ads statement in Terms is fine while the game has
  none; if monetization is ever added, Terms §6 "Changes" requires a date
  bump — consider adding an explicit "no IAP/ads" line now for symmetry
  with the Privacy Policy. Optional.
- HTML validity: both pages are clean, single-file, no JS, all asset refs
  in index.html resolve (9/9 present). Deploy workflow (.github/workflows/
  deploy.yml) uploads repo root to Pages — will publish terms-license.html
  as soon as the repo is public. That is intended for review; see (1).

## Repo push (follow-up 2) — not done by agent, owner-only

- `gh api repos/c01db100ded-org/coldbloodedgames-pages` -> 404: repo does not
  exist yet. Agent PAT cannot create repos (per issue). Owner/org-admin must:
  1. Create public repo `c01db100ded-org/coldbloodedgames-pages`.
  2. Add empty-repo remote, push local main (db51860) — this repo has no
     remote configured yet (`.git/config` has no [remote] section).
     Suggested: `git -C /home/ubuntu/coldbloodedgames-pages remote add
     origin https://github.com/c01db100ded-org/coldbloodedgames-pages.git`
     then push with owner credentials.
  3. Enable Pages: Settings > Pages > Source: GitHub Actions (deploy.yml
     already present), optionally custom domain www.coldbloodedgames.com
     per README (HOM-255 §5 Squarespace checklist is owner-only).
  4. Verify https://c01db100ded-org.github.io/coldbloodedgames-pages/
     renders, and remove the footer Terms link (or apply fix 1a) before
     any Play Console submission.
- No DNS/Console changes made by this review. No files changed in db51860
  by this review (notes only, intentionally uncommitted on agent disk).

## Update — HOM-261 fix commit 069d9c5 (2026-11-07)
Applied the blocking fix locally: commented out the live Terms footer link
in index.html (now an HTML comment with restore instructions) and added
`<meta name="robots" content="noindex">` to terms-license.html. The fix is
committed locally as 069d9c5; it travels with the owner push (repo still
404 / no remote — push is owner-only).
Remaining owner-owned: legal sign-off (governing law, liability cap,
indemnity/termination/assignment/severability, age clause, effective date),
repo creation + push, Pages verification, Play Console linkage.
