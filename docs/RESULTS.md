# Results and sensitivity analysis

## Historical results

Period: **January 2–October 1, 2026**. These are preserved audit results for the version snapshot reviewed on October 13, 2026. They are development-sample simulations, not live performance or untouched holdout tests. The three rows are alternative replays of the same period and must not be added together.

| Replay | Net P&L | Maximum drawdown* | Trades | Win rate | Profit factor |
|---|---:|---:|---:|---:|---:|
| Audited legacy replay | $7,341.36 | $1,528.08 | 95 | 53.68% | 1.81 |
| Causal-calendar sensitivity | $7,064.96 | $1,528.08 | 94 | 53.19% | 1.78 |
| Causal + execution stress | $6,796.96 | $1,596.08 | 94 | 53.19% | 1.74 |

![Aggregate historical results](../performance.png)

## Measurement and assumptions

- Net P&L is the sum of whole-position results after modeled transaction costs. A win requires positive whole-position net P&L; profitable partial executions alone do not constitute a win. Profit factor is total positive net P&L divided by the absolute sum of negative net P&L.
- **Maximum drawdown*** is the largest decline from the highest previously completed end-of-day equity to adverse intraday marked equity. It is not a drawdown measured from the highest intraday equity. The legacy replay also records end-of-day peak-to-trough drawdown of $1,408.56.
- Legacy replay costs: micro gold commission $1.92 per contract round trip with two ticks of modeled exit slippage; micro index commission $1.40 per contract round trip with zero modeled stop slippage. Costs in the preserved implementation differ from some configuration documentation; these are the effective replay assumptions.
- The causal-calendar sensitivity selects the micro index contract using the prior completed session rather than the current full day. The final row additionally applies micro index commission of $1.90 per contract round trip, two stop/market slippage ticks, one-tick entry trade-through, and session-end flattening at the open. Gold assumptions remain unchanged. This is a partial execution sensitivity, not a fully stressed portfolio.
- Minute bars do not establish intrabar event order, queue priority, latency or executable fills. The legacy row contains a known future-information issue in contract selection. The alternate rows address that calendar issue but do not remove all simulation limitations.
- Model selection used the inspected period. Preserved arithmetic is checked against the audit artifacts; a new market-data replay was not run for this showcase. No prospective paper or live performance is published.

## Engineering focus

- Unified portfolio accounting across two market streams.
- Reproducible configuration and regression checks.
- Cost-aware reporting with explicit drawdown definitions.
- Audits that distinguish documentation errors, simulation assumptions and integration limitations.

## Derived comparisons

These values are arithmetic derived from the published aggregate rows, not additional experiments. Each scenario reruns the same research period; the rows are not additive.

| Comparison | Net P&L change | Drawdown change | Position-count change |
|---|---:|---:|---:|
| Causal-calendar sensitivity minus legacy replay | -$276.40 | $0.00 | -1 |
| Causal + execution stress minus legacy replay | -$544.40 | $68.00 | -1 |

| Scenario | Mean net P&L per closed position |
|---|---:|
| Audited legacy replay | $77.28 |
| Causal-calendar sensitivity | $75.16 |
| Causal + execution stress | $72.31 |

Mean net P&L is net P&L divided by the number of closed positions. It is descriptive, not an expected future payoff. Drawdown changes can move differently from final net P&L because the path and event sequence matter.

[Project overview](../README.md) · [Engineering](ENGINEERING.md) · [Methodology](METHODOLOGY.md)
