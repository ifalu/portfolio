# Ian Falú — Solutions Architect & Full-Stack / AI Engineer

I design and ship production systems end to end — data platforms, integrations, and
security-conscious web apps — and I care about correctness, clear architecture, and shipping
things that survive real use.

This is a public portfolio of **case studies**. The source for these projects is private
(proprietary / client work); each write-up covers the architecture and engineering decisions
without exposing source or commercial IP. **Source available on request under NDA or via a live
walkthrough.**

## Selected case studies

### 📊 [Sales-Growth & Commission Platform](./sales-commission-platform.md)
A production web platform (Next.js + Postgres/Supabase, deployed on Vercel) that replaced a
manual Access + Excel process: it consolidates multi-source sales, computes instructor
commissions **reconciled to the cent against the legacy system**, runs the monthly payout flow,
and powers an instructor self-service portal — with RLS + IDOR-guarded auth, Zod-validated
ingestion, and an idempotent server-side sync built around real hosting constraints.

*Highlights:* to-the-cent reconciliation against a legacy system · ~12.5k transactions migrated ·
caught & fixed a real revenue double-counting bug · ~60 automated tests + type-check/build gates ·
secrets/PII handling and least-privilege access.

---

*More case studies coming. Reach me on [LinkedIn](https://www.linkedin.com/) — source and
deeper technical walkthroughs available on request.*
