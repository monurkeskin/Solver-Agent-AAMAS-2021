# Method and evidence

Associated paper: [Solver Agent: Towards Emotional and Opponent-Aware Agent for Human-Robot Negotiation](https://www.ifaamas.org/Proceedings/aamas2021/pdfs/p1557.pdf).

## Scientific contract

Quadratic time target, recent reciprocal utility changes, categorical affect and opponent awareness.

The three-page paper does not provide a complete recoverable participant protocol. The fruit configuration is a method demonstration.

The machine-readable [paper map](paper-map.json) links selected manuscript labels,
source hashes and locations to implementation, independent tests, configurations
and result targets. Only the selected active LaTeX entry was used. Manuscript
working files, inactive drafts and reviewer correspondence are not redistributed.


## Scope of the short paper

Equation-level checks cover time/behavior composition, categorical affect and
awareness. The three-page source does not recover every historical adaptation,
selection or Nash-schedule detail. The maintained `solver-2021` preserves its
recorded legacy interpretation; the 2025 algorithm changes are not silently applied
to this strategy. The fruit scenario is an illustrative method setup.

## Utility, targets and game scores

A bid always states the human share. Agent utility uses the complementary allocation.
Utility is computed at full precision; rendering multiplies by 100 for display.
A target score is distinct from a reservation constraint. In the fruit papers,
a human agreement below 40 points is permitted but earns zero game points;
raw utility and game payoff remain separate logged fields. The Jennifer papers'
30-point goal is not silently turned into a prohibition on lower agreements.
The short Solver and Appearance examples do not claim those fruit reward rules.

## Remaining evidence gaps

- Exact historical experiment commit and full configuration.
- Original permitted participant records and analysis decisions.
- Original affect model and observation records.

Unknown inputs are not filled with simulated participants or invented historical
constants. The existing templates are inspectable, but their published-protocol
preflight prevents starting before required evidence is supplied and reviewed.
A custom study has its own declared configuration and cannot inherit a reproduction
claim merely by using the same strategy name.

## Relationship to the research series

Later Solver variants share concepts but do not establish implementation or experimental equivalence.

The common engine owns utility, lifecycle, logs, GUI, shared methods and device
contracts. This repository owns paper-specific profiles, protocol choices, analysis
rules, reproduction targets and tests. [framework.json](framework.json) pins the
engine; [NOTICE](NOTICE) preserves original source attribution.
