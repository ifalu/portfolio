# Ian Falú — Solutions Architect & Full-Stack / AI Engineer

I design and ship production systems end to end — data platforms, AI pipelines, integrations, and
security-conscious web apps — and I care about correctness, clear architecture, and shipping things
that survive real use.

This is a public portfolio of **case studies**. The source for these projects is private
(proprietary / client work); each write-up covers the architecture and engineering decisions without
exposing source or commercial IP. **Source available on request under NDA or via a live
walkthrough.**

A recurring theme across this work: **applied AI with guardrails** — grounding, retrieval, and
validation so generated output is *traceable and reviewable*, not just plausible — backed by a
security-first habit (secret management, least-privilege access, input validation).

## Applied-AI case studies

### 🧩 [AI Course-Authoring Platform](./ai-course-authoring-platform.md)
A FastAPI backend that turns source material into a complete e-learning course through a **nine-stage,
grounded AI pipeline** (objectives → slides → assessments → narration → audio → SCORM), orchestrating
Claude, an image model, and two TTS providers behind one async API. Each stage is independently
re-runnable, and the assessment stage is grounded in source excerpts so it's reviewable.

### 📝 [Grounded Exam-Question Generator](./grounded-exam-generator.md)
A desktop app that generates multiple-choice question banks from source documents where **every
question is tied to a source excerpt**, scored against a 10-point validation rubric, and de-duplicated
(exact + Jaccard) — built so generated assessment content can survive a compliance review. GPT-4o with
a cheaper fallback model, runtime key entry, four export formats.

### 🖥️ [AI PowerPoint Generator & Deck Toolkit](./ai-powerpoint-generator.md)
Retrieval-grounded slide generation: source docs chunked, embedded (sentence-transformers) into a
**local FAISS index**, with each slide's bullets generated from retrieved chunks **and cited** — plus
a low-level OOXML toolkit for bulk note/audio surgery the standard libraries can't do cleanly.

### 🎙️ [Slide Narration Generator](./slide-narration-generator.md)
Writes instructor-voice narration for a whole deck using a **rolling context window** (4 prior + 2
upcoming slides) for continuity, a language-verification gate for multilingual courses, and a cleanup
pass that strips the tells of machine-written text.

### 🔊 [TTS Audio Production Pipeline](./tts-audio-production-pipeline.md)
Turns per-slide narration into voiced audio with a configurable neural TTS provider, splits long audio
on **detected silence**, and embeds each clip back into the slide deck — closing the loop from script
to a narrated presentation. (Also where a real hardcoded-key leak was caught and fixed during
portfolio prep.)

## Platform, data & integration case studies

### 📊 [Sales-Growth & Commission Platform](./sales-commission-platform.md)
A production web platform (Next.js + Postgres/Supabase on Vercel) that replaced a manual Access + Excel
process: consolidates multi-source sales, computes instructor commissions **reconciled to the cent
against the legacy system**, runs the monthly payout flow, and powers an instructor portal — with RLS +
IDOR-guarded auth, Zod-validated ingestion, and an idempotent server-side sync.

### 📄 [Document Version & Findings Tracker](./document-version-tracker.md)
A **multi-tenant**, security-hardened Flask app for controlled-document version history (immutable
audit trail), a client-facing defect workflow with **tokened sign-off**, and maintenance-hour billing —
bcrypt, CSRF, rate limiting, strict CSP, role-scoped data separation. Designed to also ingest findings
from an automated test harness.

### 🎓 [CE Transcript Automation System](./transcript-automation-system.md)
A deployed Flask + Selenium service that automates transcript retrieval from a regulator's **MFA-gated
portal** — solved via session reuse (not bypass), an admin-driven request queue, PDF email delivery,
and a store-integrated course recommendation. Honest about the single-worker constraint and the
semi-attended MFA step.

### 🛒 [Store & LMS Operations Toolkit](./store-operations-toolkit.md)
Internal staff tools integrating **Magento 2 (REST)** and **Moodle (web services)** plus SSH ops:
cart pre-building, student provisioning/enrollment, and safe store reindex/cache — each with an auth
model fitted to its blast radius, including a PIN + **encrypted-credential** design that lets non-admins
run server maintenance without holding server credentials.

### 🔎 [Regulatory-Data Intelligence for Renewals](./regulatory-data-intelligence.md)
Two Selenium tools that turn a licensing regulator's portal into **sales intelligence**: a renewal
worklist (who's expiring, sorted by urgency) and a competitive segmentation (loyal / lapsed / never) —
feeding the re-engagement side of the sales-growth platform above.

---

*Reach me on [LinkedIn](https://www.linkedin.com/in/slstech/) — source and deeper technical
walkthroughs available on request under NDA or via a live screen-share.*
