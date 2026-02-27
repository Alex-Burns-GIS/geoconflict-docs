# GeoConflict: Strategic Intelligence Platform

An advanced, offline-first strategic intelligence platform designed for exploring global conflict data, analyzing macro-level trends, and generating actionable operational briefs. Built as a high-performance monorepo, GeoConflict transforms raw event data into comprehensive, decision-ready intelligence.

---

## Project Overview & Aims

In a rapidly changing global security environment, analysts and strategic planners require immediate, reliable access to conflict data without depending on continuous cloud connectivity. 

**GeoConflict aims to solve this by providing:**
1. **Offline-First Resilience:** Analyze massive global datasets and render vector maps completely offline using pre-built intelligence packs.
2. **High-Performance Visualization:** Leverage WebGL-accelerated rendering capable of displaying hundreds of thousands of individual conflict events simultaneously without performance degradation.
3. **Automated Intelligence:** Reduce the time from data intake to operational briefing from days to seconds using automated insight generation and localized zone analysis.
4. **Comprehensive Macro Analysis:** Move beyond dots on a map by surfacing strategic networks, dyadic rivalries, escalation indicators, and infrastructure exposure risks.

---

## Key Capabilities

### Dynamic Conflict Visualization
Explore decades of conflict data with unparalleled fluidity. The platform supports seamless transitions between macro-level clustering and micro-level event markers, colored by severity, actor types, and fatalities.

**Event Accumulation & Clustering:**
![Event Clusters](docs/assets/Explore%20Page%201%20-%20Event%20Clusters.png)

**Fatality Intensity Mapping:**
![Fatalities Clusters](docs/assets/Explore%20Page%202%20-%20Fatalities%20Clusters.png)

**Tactical Event Markers:**
![Event Markers](docs/assets/Explore%20Page%205%20-%20Event%20Markers.png)

### Strategic Networks & Dyads
Understand the actors behind the violence. The platform maps out complex networks of state, non-state, and one-sided actors, using interactive global dyad arcs to visualize who is fighting whom, and where the conflict spans across borders.

![Dyad Arcs](docs/assets/Explore%20Page%203%20-%20Dyad%20Arcs.png)

### Regional Hotspots & Density Analysis
Quickly identify geographic concentrations of violence. Dynamic density indicators, such as H3 hexbin layers, provide instant visual cues for the most volatile regions, scaling effortlessly from local outbreaks to continental trends.

![Hotspot Analysis](docs/assets/Explore%20Page%204%20-%20Hotspot%20Analysis.png)

### Localized Intelligence & Zone Analysis
Draw custom polygons or select existing administrative boundaries to instantly generate localized threat assessments. The system isolates events within the perimeter to compute bespoke metrics for any operational area.

![Zone Analysis](docs/assets/Explore%20Page%206%20-%20Zone%20Analysis.png)

### Automated Brief Builder
Transform raw map analysis into polished, shareable intelligence products. The Brief Builder instantly structures lethality rates, deadliest actors, peak activity timelines, and severity distributions into a clear, executive-ready format.

![Brief Builder](docs/assets/Brief%20Builder%20(Beta).png)

### Infrastructure Exposure Risk
Bridge the gap between conflict data and critical physical assets. GeoConflict cross-references active hotspots with vital infrastructure—such as ports, airports, and hospitals—to surface highly exposed, at-risk facilities in a prioritized queue.

![Assets and Exposure](docs/assets/Assets%20and%20Exposure%201.png)

### Macro Analytics & Trends
Go beyond the map with deep statistical analysis, escalation indicators, and temporal trends. The Trends dashboard provides a battery of charts that track dyadic escalation, actor churn, inter-event timing, and geographic diffusion speeds over time.

**Escalation & Matrix Views:**
![Trends Analytics 1](docs/assets/Trends%201.png)

**Temporal Charts & League Tables:**
![Trends Analytics 2](docs/assets/Trends%202.png)

**Deep Dive Metrics:**
![Trends Analytics 3](docs/assets/Trends%203.png)

---

## Data: UCDP Georeferenced Event Dataset (GED)

GeoConflict’s core conflict-event layers and downstream analytics are built on the **Uppsala Conflict Data Program (UCDP) Georeferenced Event Dataset (GED)**, an event-level dataset on organized violence. GED’s unit of analysis is the **event**: an incident where armed force is used by an organized actor against another organized actor, or against civilians, producing **at least one direct death** at a specific location and date. :contentReference[oaicite:0]{index=0}

Key properties leveraged by GeoConflict:
- **Global coverage (post-1989)** with annual versioned releases (e.g., GED 25.1 covers 1989-01-01 to 2024-12-31). :contentReference[oaicite:1]{index=1}  
- **Fine-grained spatiotemporal resolution**, geocoded to specific coordinates with a best-case resolution at settlement level, and disaggregated to the day. :contentReference[oaicite:2]{index=2}  
- **Organized-violence typology** enabling consistent filtering and comparison across (1) state-based conflict, (2) non-state conflict, and (3) one-sided violence. :contentReference[oaicite:3]{index=3}  
- **Fatality uncertainty handling**, where GED provides multiple fatality estimates per event, allowing GeoConflict to support both conservative and upper-bound views in trend and hotspot analysis. :contentReference[oaicite:4]{index=4}  

If you use GeoConflict outputs in publications, please cite UCDP per their download-center guidance (including the GED reference article and the annual “organized violence” update). :contentReference[oaicite:5]{index=5}

---

## 🛠 Quickstart

```bash
pnpm install
pnpm dev
```

The viewer runs locally at `http://localhost:5173`.

### Start the API backend (recommended)

To enable all advanced filtering and analytical features:

```bash
pnpm install
pnpm --filter api dev
# or from the repository root: pnpm dev:api
```

> **Note:** Use `pnpm` for workspace installations. Running `npm run dev` inside `apps/api` may fail due to missing workspace-linked dependencies if the repository was not properly installed with `pnpm` at the root.

---

## 💻 Workspace Commands

```bash
# Build all workspace packages and applications
pnpm build

# Run comprehensive workspace test suites
pnpm test

# Prove core quality gates (typechecking, dependency boundaries, testing)
pnpm check
```

---

## 🏗 Monorepo Architecture

GeoConflict is structured as an integrated monorepo prioritizing shared models and clear dependency boundaries:

- **`apps/viewer`** — The primary high-performance React + Vite map viewer and intelligence dashboard.
- **`apps/api`** — The robust Node.js/TypeScript analytical backend and data server.
- **`packages/core`** — Shared manifest schemas, core types, and utility models (`@geoconflict/core`).
- **`packages/pack-builder`** — The CLI engine for the ingestion, tiling, building, and fetching of offline intelligence packs (`@geoconflict/pack-builder`).
- **`tools/`** — Operational data utilities and ingestion scripts for external datasets (UCDP, Overture).
- **`schema/`** — PostgreSQL/PostGIS bootstrap SQL and database migrations.
- **`docs/`** — Comprehensive architectural records, deployment guides, and pipeline runbooks.

---

## 📚 Documentation Directory

- **System Architecture:** `docs/ARCHITECTURE.md`
- **Baseline Refactor Plan (PR #1):** `docs/architecture/2026-02-baseline-and-plan.md`
- **ADR 0001 (Dependency Boundaries):** `docs/adr/0001-layered-boundary-direction.md`
- **Deployment Guide:** `docs/deployment.md`
- **Pipeline Runbook:** `docs/RUNNING_THE_PIPELINE.md`
- **GSD Operational Docs:** `docs/gsd/README.md`
