# Zscaler AI Work System — Task File

**last_updated:** 2026-03-24
**source:** Initial population from TRACKER_UPDATE_v18 — open tasks from BUILD_SEQUENCE + PARKING_LOT, open questions from OPEN_QUESTIONS. First task file produced this system; no prior task file exists to merge.

---

## open_tasks

| id | action | owner | status | blocked_by | source |
|----|--------|-------|--------|------------|--------|
| 20260324-002 | Tracker working memory cleanup — read current tracker, identify reference material, migrate or deprecate. Goal: lean working memory doc. Prerequisite to daily notes production build | self | pending | — | tracker BUILD_SEQUENCE item 23 |
| 20260324-003 | Build Worker GET endpoint — read-only GET /api/corpus?q=... on Cloudflare Worker, exposing AutoRAG query results as JSON. Enables Claude web_fetch access to corpus from claude.ai sessions. Small build: one route + CORS config | self | pending | — | tracker BUILD_SEQUENCE item 24 prereq |
| 20260324-004 | Build Zscaler quiz/upskilling tool — ZIA as first knowledge domain. Architecture: Cloudflare Workers + AutoRAG + R2 (4,353 docs) + D1. Worker GET endpoint (task 003) is prerequisite | self | pending | 20260324-003 | tracker PARKING_LOT quiz builder |
| 20260324-005 | Read Zscaler GenAI Policy in full (document on Exchange). Update data hygiene section of operating protocol. Unblocks Account Prep mode and seed docs | self | pending | — | tracker OPEN_QUESTIONS Q1 |
| 20260324-006 | Probe press content type — 382 records, JS-rendered listing. Confirm whether public access is possible or requires Playwright | self | pending | — | tracker BUILD_SEQUENCE item 9 phase 2 |
| 20260324-007 | Restore llms.txt / Zpedia scraping in phase 2 scraper — dropped between v1 and v6. URLs: zscaler.com/llms.txt and zscaler.com/llms-full.txt. High value | self | pending | — | tracker DECISIONS_MADE 2026-03-21 |
| 20260324-008 | Build automated internal document ingestion pipeline — PDF, DOCX, PPTX, TXT support. Current manual script handles markdown only | self | pending | — | tracker BUILD_SEQUENCE item 21 |
| 20260324-009 | Define documentation scaffolding / folder structure — AI Foundational is reserved for behavioral governance. Need structure for automation systems, data infrastructure, enablement content, client reference materials. Dedicated 30-min session | self | pending | — | tracker PARKING_LOT infrastructure |
| 20260324-010 | Build System Reference document (third doc type) — what has been built, how it works, how to operate it. Needs own pipeline token and folder. Blocked on item 009 | self | pending | 20260324-009 | tracker BUILD_SEQUENCE item 11 |
| 20260324-011 | Build daily notes production system — Drive-backed storage, Cloudflare Pages hosted, browser-accessible from work machine. Blocked on tracker cleanup (item 002) and Worker endpoint (item 003) | self | pending | 20260324-002 | tracker BUILD_SEQUENCE item 17 |
| 20260324-012 | Add graduation pass as procedural skill to skills file v3 — trigger phrases, two-track execution sequence, required output (task file artifact), drift guard constraint | self | pending | — | tracker BUILD_SEQUENCE item 26 |
| 20260324-013 | Build weekly automated corpus update workflow in n8n (digest/notification workflow separate from GitHub Actions sync) | self | pending | — | tracker infrastructure |
| 20260324-014 | Resolve inbox suppression for pipeline trigger emails — Gmail filter applies label but inbox suppression not configured | self | pending | — | tracker INFRASTRUCTURE |
| 20260324-015 | Reconcile 12-doc discrepancy in R2 — seeded count 4,357 vs actual 4,353. Likely silent upload failures. Reconcile when weekly pipeline is operational | self | pending | — | tracker BUILD_SEQUENCE item 9 |
| 20260324-016 | Design two-system interface layer — explicit interface between Zscaler work system and TL system. How field observations flow from call analysis into TL signal store; how shared corpus serves both systems without conflicting curation requirements | self | pending | — | tracker PARKING_LOT strategic |
| 20260324-017 | Unblock Account Prep mode — requires GenAI Policy read (item 005) and data hygiene rule full confirmation | self | pending | 20260324-005 | tracker BUILD_SEQUENCE item 15 |
| 20260324-018 | Begin ZIA upskilling sequence — interactive quiz model, verbal fluency goal. First in sequence: ZIA → ZPA → ZDX → Zero Trust Branch → Private Service Edge → competitive | self | pending | — | tracker PARKING_LOT upskilling |

---

## open_questions

| id | question | resolution_path | context | status |
|----|----------|-----------------|---------|--------|
| 20260324-Q01 | What does the Zscaler GenAI Policy say — specifically what customer data, account names, opportunity identifiers, or internal architecture details can be introduced into external AI sessions? | self | Unblocks Account Prep mode, seed docs, and finalizes data hygiene boundaries in operating protocol. Document is on Exchange | open |
| 20260324-Q02 | Is there an SE wiki, battle card library, objection handling guide, or competitive brief repository? Who owns it and how is access provisioned? | other | Determines what internal enablement content already exists before building anything new | open |
| 20260324-Q03 | What is the correct internal path field for Zscaler case study pages? The link field in API response routes to customer external sites, not Zscaler case study pages | self | Required for corpus scraper correctness — confirmed bug in current scraper | open |
| 20260324-Q04 | Does the quiz tool use AutoRAG (existing pipeline) or a new Vectorize index over zs-corpus? | self | Architectural decision for Worker build. AutoRAG simpler if already configured; Vectorize gives more query control | open |
| 20260324-Q05 | How do learnings graduated during graduation pass update the tracker Knowledge Map? No clean protocol yet — deferred to Worker GET endpoint build session | self | Knowledge Map is the gate on Content mode; needs a maintainable update flow | open |

---

## completed_since_last_pass

| id | action | completed | notes |
|----|--------|-----------|-------|
| 20260324-C01 | Decommission Cloudflare readiness tool — Worker, D1 (readiness-sessions), R2 bucket (readiness-corpus), AI Search index (readiness-index) all deleted | 2026-03-24 | Source code preserved at C:\Users\bashl\Documents\cloudflare-readiness-tool. Architecture pattern documented for quiz tool rebuild |
| 20260324-C02 | Fix GitHub Actions corpus_sync.yml — heredocs extracted to scripts/download_manifests.py and scripts/build_webhook_payload.py. Committed and pushed (commit 044f840) | 2026-03-24 | Deployed before Monday 6am UTC deadline |
| 20260324-C03 | Create zs-config-store public GitHub repo, push capture_schema.json (v1) and initial task file | 2026-03-24 | Repo: bashley8/zs-config-store. Raw GET endpoint established for Claude session access |
