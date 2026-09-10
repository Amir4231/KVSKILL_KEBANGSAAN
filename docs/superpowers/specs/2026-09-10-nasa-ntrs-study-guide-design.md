# KV Skills 2026 Module C Study Guide — NTRS Redesign (Approach A)

Date: 2026-09-10
Status: Design approved (5/5 sections)
Approach: A — Single static document, NTRS typesetting

## 1. Document architecture

- Single file replacing current guide: `index.html` at repo root for Vercel static hosting.
- Inline `<style>` in head; ~60 lines vanilla JS at end of body. No frameworks, webfonts, or CDN.
- Type stacks: serif `Georgia, 'Times New Roman', serif` for body; mono `ui-monospace, Consolas, monospace` for data/code; system sans for small labels (figure captions) only.
- Front matter order: cover block (program line, title, Module C identifier, date) → Abstract (4 sentences) → Table of Contents (numbered) → Nomenclature (role 0/1, status 0/1, key routes, credentials) → body §1–§7 → Appendix → References (Module C PDF 12pp + Complete Guide 847 lines as cited sources).
- Degradation: full content readable with JS disabled; TOC anchors degrade to plain text if an ID is missing.

## 2. Typesetting and figure system

- Measure ~68ch, left-aligned, line-height 1.55. Ink near-black `#111`; single accent navy `#1b2a6b` for headings, table rules, figure numbers only.
- Banned: gradients, shadows, rounded cards, emojis, glow, progress bars, badges.
- Headings numbered (1.0, 1.1); horizontal rules between major sections.
- Tables: top/bottom rules only, right-aligned numeric columns (marks, counts).
- Figures keep PDF labels `Figure C2–C13`; data tables numbered sequentially `Table 1–N` in the new document; terse caption + requirement list under each.
- Code: spec table visible; full file inside `<details><summary>` showing filename + line count. Never dump code inline.
- Mobile: measure full-width; wide tables get horizontal scroll with sticky first column; no other layout change.

## 3. Content mapping (formal NTRS sections, same facts)

1. Mission & Scope — 8 screens + route map.
2. Marking Scheme C1–C10 — ranked table with plain % column and priority note (no weight bars). Total 50.00.
3. Environment & Setup — XAMPP, `kvskill` DB (`utf8mb4_unicode_ci`, root/blank), `.env` 7 lines, `key:generate`, `public/uploads`.
4. Database Design — 4 tables; `status` anomaly flagged as Note (0=public, 1=private, default 0); migrations / seeder (`Admin`/`Alice`/`Bob` + `password`) / models in `<details>`.
5. System Design — layout contract (header/nav/main/footer + 3 nav states); Auth C3 (verbatim strings, role redirects); One Page C4 + Slide C5 (public+non-empty, first-photo thumb, Prev/Next/count, no reload); My Reports C6 (grey empty, X delete, + modal → `/manage/{newId}`); Manage C7+C8 (top form, AJAX upload, drag-drop highlight, 600×600 GD resize, fullscreen, delete); Users C9 (aggregate counts, cascade delete).
6. Routes master table — all `routes/web.php` entries verbatim.
7. Verification — judge protocol checklist (16 items) + 6-hour battle plan as plain timetable.
- Appendix: pitfalls (10 rules) + file map (~17 files). References: PDF + guide.
- Invariant: every validation string, redirect, and credential stays verbatim from sources.

## 4. Quiet study tools

1. Section filter: plain text input filtering sections by heading text. No animation/highlight.
2. `<details>` disclosure + per-block Copy button (`navigator.clipboard`; fallback: select text).
3. Verification checklist: native checkboxes persisted to `localStorage` + text counter (`n / 16`). No bars/scores.
4. Print stylesheet: strips filter input + copy buttons; page margins; figure/table numbering continuity.
- No timer, scroll progress, badges. JS-off: everything except filter/persistence works.

## 5. Constraints, Vercel, verification

- Single `index.html` ≤150KB; zero external requests (offline + CSP clean).
- Responsive via fluid measure + in-table horizontal scroll only.
- Print: `@page` margins; `break-inside: avoid` on figures.
- Vercel: static deploy, no config, served as `/`.
- Acceptance checks: (a) JS disabled → all spec readable; (b) 360px viewport → no page-level horizontal scroll; (c) print-to-PDF → checklist + code print expanded; (d) verbatim spot-check — `Username and password not matched.`, `600`, `CompetitorID_Module_C` each present verbatim in the spec body.

## Out of scope

- No timer, progress gamification, theming, or multi-page routing.
- No B (split CSS/JS files) or C (Next.js/MDX) work.
- No new study content beyond the two sources; no PDF figure image extraction.
