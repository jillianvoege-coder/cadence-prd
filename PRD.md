# Product Requirements Document

## Product Name
**Cadence** — Strategic Content Automation Platform

## Problem Statement
Content teams at mid-market and enterprise companies face three converging challenges:

1. **Knowledge fragmentation**: Strategic insights live in internal docs, calls, and decks that never inform external content
2. **Channel proliferation**: Publishing expectations have grown 3x while teams remain flat
3. **Discovery shift**: LLMs now answer questions that previously drove search traffic; companies without AEO-optimized content become invisible

Existing tools address content creation or distribution but not the strategic intelligence layer connecting company knowledge to audience-ready content.

## Vision
Cadence continuously synthesizes internal knowledge and external signals to generate a strategic content drumbeat—publishing-ready assets that resonate with human audiences and are structured for LLM discoverability.

---

## Target Users

| Segment | Primary User | Buyer |
|---------|--------------|-------|
| Mid-market SaaS (200-1000 emp) | Content Ops Lead / Content Director | CMO / VP Marketing |
| Enterprise (1000+ emp) | Content Strategist | Head of Brand / Content |

---

## Core Capabilities

### 1. Knowledge Ingestion Engine
**What it does**: Connects to internal and external content sources, builds a continuously updated knowledge graph of company positioning, messaging, and domain expertise.

**Sources supported**:
- Internal: Google Drive, Notion, Confluence, Gong/Chorus call transcripts, Slack channels, strategy decks, product docs
- External: Published blog posts, social profiles, press releases, competitor content, industry publications

**Requirements**:
- Incremental sync (not batch); new content indexed within 15 minutes
- Entity extraction: people, products, features, customer segments, competitors
- Relationship mapping: what claims does the company make? What proof points exist?
- Staleness detection: flag outdated messaging or contradictory claims

### 2. Strategy Alignment Module
**What it does**: Allows users to define strategic priorities and messaging pillars; all generated content traces back to these.

**Requirements**:
- Input: quarterly themes, ICP definitions, competitive positioning, product launch calendar
- Output: weighted priority scores applied to content suggestions
- Constraint enforcement: generated content must map to at least one strategic pillar
- Drift alerts: notify when publishing patterns diverge from stated strategy

### 3. Audience Intelligence
**What it does**: Maintains dynamic profiles of three audience segments and their content preferences.

| Audience | Signals Tracked |
|----------|-----------------|
| Prospective customers | Search queries, competitor comparisons, buying stage indicators |
| Existing customers | Feature adoption, support tickets, expansion signals |
| LLM answer engines | Query patterns, citation sources, structured data preferences |

**Requirements**:
- Integration with CRM (Salesforce, HubSpot) for customer segmentation
- Search console and analytics integration for query intelligence
- LLM audit: weekly report on how major models (GPT, Claude, Gemini, Perplexity) describe the company and competitors

### 4. Content Generation Engine
**What it does**: Produces draft content assets optimized for specific channels and audiences.

**Content types (v1)**:
- Blog posts (long-form, short-form)
- LinkedIn posts (company page + executive ghostwriting)
- Email sequences (nurture, product updates)
- Customer case study frameworks
- FAQ/knowledge base articles (AEO-optimized)

**Requirements**:
- Every generated piece includes: source attribution (what internal knowledge informed it), strategic pillar mapping, target audience, suggested publish date
- AEO formatting: structured data markup suggestions, Q&A formatting, citation-friendly snippets
- Brand voice calibration: learns from approved content, flags deviations
- Human-in-the-loop: all content enters review queue; no auto-publish in v1

### 5. Drumbeat Orchestration
**What it does**: Maintains a rolling 90-day content calendar with intelligent scheduling.

**Requirements**:
- Cadence recommendations based on: channel best practices, audience engagement patterns, competitive publishing velocity
- Thematic clustering: groups related content into campaigns vs. isolated posts
- Gap detection: identifies topics the company should own but hasn't addressed
- Load balancing: distributes effort across team members based on capacity

### 6. AEO Optimization Suite
**What it does**: Ensures content is structured for LLM discoverability and accurate representation.

**Requirements**:
- Structured data generator: FAQ schema, HowTo schema, Organization schema
- Answer-target analysis: for key queries, what answer format would LLMs prefer?
- Citation optimization: identifies authoritative claims that should be made more quotable
- Competitive monitoring: alerts when competitors gain LLM citation share

---

## Success Metrics

| Metric | Target (6 months post-launch) |
|--------|-------------------------------|
| Content velocity | 2x output with same team size |
| Strategy alignment score | 90% of published content maps to active pillars |
| LLM citation share | 15% improvement in brand mentions in answer engine results |
| Time-to-publish | 50% reduction from idea to live |
| Content utilization | 80% of generated drafts reach publication (vs. typical 40%) |

---

## Non-Goals (v1)
- Automated publishing (human approval required)
- Video/podcast content generation
- Paid media copy
- Multi-language support
- Custom LLM fine-tuning

---

## Technical Architecture (High-Level)

```
┌─────────────────────────────────────────────────────────────┐
│                     Cadence Platform                        │
├─────────────────────────────────────────────────────────────┤
│  Ingestion Layer                                            │
│  ├── OAuth connectors (Drive, Notion, Slack, CRM)          │
│  ├── Web scrapers (company site, competitors)              │
│  └── API integrations (Gong, Search Console)               │
├─────────────────────────────────────────────────────────────┤
│  Intelligence Layer                                         │
│  ├── Knowledge graph (Neo4j or similar)                    │
│  ├── Embedding store (vector DB for semantic search)       │
│  └── Strategy rules engine                                  │
├─────────────────────────────────────────────────────────────┤
│  Generation Layer                                           │
│  ├── LLM orchestration (multi-model, cost-optimized)       │
│  ├── Brand voice model                                      │
│  └── AEO formatter                                          │
├─────────────────────────────────────────────────────────────┤
│  Orchestration Layer                                        │
│  ├── Calendar engine                                        │
│  ├── Workflow manager                                       │
│  └── Analytics/reporting                                    │
└─────────────────────────────────────────────────────────────┘
```

---

## Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| Generated content feels generic | Deep brand voice training; require source attribution to ground in real company knowledge |
| Integration complexity delays launch | Start with Google Workspace + Notion only; expand connectors post-launch |
| LLM landscape shifts rapidly | Abstract model layer; monitor for new AEO best practices quarterly |
| Privacy/security concerns with internal docs | SOC 2 compliance; granular permission controls; no training on customer data |

---

## Rollout Plan

- **Phase 1 (Months 1-3)**: Knowledge ingestion + manual strategy input + basic content generation
- **Phase 2 (Months 4-6)**: Drumbeat calendar + AEO optimization + LLM audit reports
- **Phase 3 (Months 7-9)**: Advanced personalization + expanded channel support + API for custom integrations
