<p align="center"><img src="assets/overview.svg" alt="Trading System V3.0 engineering portfolio" width="100%" /></p>

# Trading System V3.0

**Making configuration changes measurable and comparisons reproducible.**

Evolved the configuration-driven research/reporting workflow and used audit evidence to reconcile position counts, wins, profit factor and modeled costs. The showcase preserves the corrected measurements rather than repeating an earlier summary.

| Project lens | Evidence type | Implementation | Public artifacts |
|---|---|---|---|
| Configuration and measurement engineering | Historical simulation and preserved audits | Private | Architecture, methods, aggregate results |

**Explore:** [System design](docs/ENGINEERING.md) · [Measurement methodology](docs/METHODOLOGY.md) · [Detailed results](docs/RESULTS.md) · [Machine-readable metrics](metrics.json)

## The engineering problem

A new version can change the opportunity set and reporting assumptions at the same time. Without a fixed snapshot and consistent definitions, a polished comparison can attribute an effect to the wrong change.

## System at a glance

The diagram is a conceptual view of the research workflow. It describes logical responsibilities, not a deployment topology or an executable trading specification.

```mermaid
flowchart LR
    A[Historical market inputs] --> B[Calendar and coverage checks]
    B --> C[Private decision component]
    C --> D[Historical execution model]
    D --> E[Chronological portfolio replay]
    E --> F[Whole-position accounting]
    E --> G[Adverse equity marks]
    F --> H[Aggregate report]
    G --> H
    I[Declared cost scenario] --> D
    J[Audit and sensitivity comparisons] --> H
    classDef private fill:#172338,color:#ffffff,stroke:#64748b
    class C private
```

## Engineering dimensions

| Dimension | What the project examines | Why it matters |
|---|---|---|
| Temporal integrity | Which information exists at each research step | Reduces future-information leakage |
| State evolution | How earlier events affect later eligibility and equity | Prevents treating dependent decisions as isolated observations |
| Execution assumptions | Costs, adverse marks and minute-bar limitations | Makes reported performance interpretable |
| Measurement | Consistent position counts, net results and drawdown definitions | Avoids misleading headline comparisons |
| Evidence discipline | Preserved snapshots, controls and explicit limitations | Separates reproducible output from unsupported claims |

## Historical evidence snapshot

**January 2–October 1, 2026 · minute-bar simulation · snapshot audited October 13, 2026.** These are inspected development results, not prospective performance.

| Scenario | Net P&L | Maximum drawdown* | Positions | Win rate | Profit factor |
|---|---:|---:|---:|---:|---:|
| Audited legacy replay | $7,341.36 | $1,528.08 | 95 | 53.68% | 1.81 |
| Causal-calendar sensitivity | $7,064.96 | $1,528.08 | 94 | 53.19% | 1.78 |
| Causal + execution stress | $6,796.96 | $1,596.08 | 94 | 53.19% | 1.74 |

\* Maximum drawdown uses the highest prior end-of-day equity minus adverse intraday marked equity, not the highest intraday equity. Net P&L is after the modeled costs described in [Methodology](docs/METHODOLOGY.md). No new replay was run for this presentation update.

![Aggregate historical simulation results](performance.png)

## A finding that changed the interpretation

A high partial-execution success rate can coexist with a lower whole-position win rate. The audited combined result is 51 profitable positions out of 95, or 53.68%.

## Evidence and boundaries

| Supported here | Not established by this showcase |
|---|---|
| Aggregate figures checked against preserved research artifacts | Future returns or independent out-of-sample effectiveness |
| Explicit historical cost and drawdown definitions | Tick-accurate fills, latency or queue priority |
| Separately labeled sensitivity scenarios | Complete operational reliability |
| High-level engineering responsibilities | A reproducible public trading policy |

The public material omits implementation details and decision logic. No prospective paper or live results are published. Research-period selection and model uncertainty remain material limitations.

## Reading guide

- **[Engineering](docs/ENGINEERING.md):** component responsibilities, logical data contracts, sequencing and assurance gaps.
- **[Methodology](docs/METHODOLOGY.md):** metric definitions, effective cost assumptions and interpretation limits.
- **[Results](docs/RESULTS.md):** complete preserved tables and derived comparisons.
- **[Metrics JSON](metrics.json):** compact, machine-readable aggregate values.

## Portfolio context

[Version 2.0](https://github.com/miahaa/trading-system-v2-showcase) · [Version 3.0](https://github.com/miahaa/trading-system-v3-showcase) · [Version 4.0](https://github.com/miahaa/trading-system-v4-showcase) · [Version 7.0](https://github.com/miahaa/trading-system-v7-showcase)

These projects use different configurations, datasets and research objectives. Their results are not a controlled version ranking. Historical simulation results do not predict future returns.
