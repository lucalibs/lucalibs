# Luca Laliberte

I build and ship agentic SaaS products end to end — data collection, LLM pipelines, scheduling, billing, and the infrastructure underneath.

Two products, both live, both with working Stripe billing:

### 🎯 [Trigger Agent](https://www.triggeragent.ca) — buying-signal detection
You describe the buying intent you care about. An agent searches public sources on your cadence, extracts structured signals with an LLM, and emails you a digest.

**Next.js 16 · TypeScript · Supabase/Postgres · Claude · Stripe · Kubernetes**
→ [Repository](https://github.com/lucalibs/trigger-agent)

### 📊 [IntelBrief](https://www.intelbrief.ca) — competitor monitoring
You list competitors and what to watch. It collects from Québec and Canadian open-data sources and sends a bilingual brief where **every fact carries a dated citation you can verify**.

**Python · FastAPI · SQLite/Postgres · Claude · Stripe · Docker**
→ [Repository](https://github.com/lucalibs/intelbrief)

---

## What I care about as an engineer

**LLMs should be constrained, not trusted.** In IntelBrief the cited body of every brief is rendered deterministically with no model in the path — the LLM's entire job is a labelled two-sentence overview sitting above it, so a bad generation costs you a paragraph the reader is told to verify, never a fake citation. In Trigger Agent, every piece of scraped content is sanitized and explicitly delimited as untrusted before it reaches the model.

**Policy belongs in the client, not in a convention.** IntelBrief routes every outbound fetch through one HTTP client that refuses ToS-restricted hosts *before opening a socket*, and fails closed on a missing host. You cannot write a non-compliant collector by accident.

**Correctness under concurrency is a design problem, not a retry.** Trigger Agent's cron dispatcher claims due work with a single `UPDATE … RETURNING`, so two overlapping ticks provably process disjoint sets. A double-fire would mean a duplicate customer email and doubled model spend.

**Ship the boring parts too.** Both products have real Stripe integration, entitlement enforcement, dunning grace, webhook idempotency, unsubscribe compliance, health/readiness endpoints, and Prometheus metrics.

---

## Stack

**Languages** TypeScript, Python, SQL
**Frontend** Next.js (App Router), React 19, Tailwind
**Backend** FastAPI, Next.js server actions/route handlers, Postgres, SQLite
**AI** Anthropic Claude — structured outputs, JSON-schema extraction, LLM-as-judge evaluation
**Payments** Stripe — Checkout, Billing Portal, webhooks, multi-product account namespacing
**Infra** Docker, Kubernetes (Helm), Terraform, Caddy, Vercel, GitHub Actions

---

📫 **Luca.cesart@outlook.com**
