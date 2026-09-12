# Solver Agent: Towards Emotional and Opponent-Aware Agent for Human-Robot Negotiation — [AAMAS 2021]

Mehmet Onur Keskin · Umut Çakan · Reyhan Aydoğan

[Paper](https://www.ifaamas.org/Proceedings/aamas2021/pdfs/p1557.pdf) · [Explore the method](METHOD.md) · [Try the code](#try-it-yourself) · [Study guide](docs/protocol.md) · [Citation](#cite-the-paper)

[![Tests](https://github.com/monurkeskin/Solver-Agent-AAMAS-2021/actions/workflows/tests.yml/badge.svg)](https://github.com/monurkeskin/Solver-Agent-AAMAS-2021/actions/workflows/tests.yml)

How should a negotiating robot respond when a person looks frustrated, but keeps
making demanding offers? **Solver combines emotional feedback with evidence from
the negotiation itself.** It gives facial-expression feedback more influence
when the human's moves respond to changes in the agent's behavior.

## The idea: emotion, reciprocity and time

The AAMAS paper introduces the following behavior target (Equation 6):

$$
TU_{\mathrm{Behavior}} = U(O_j^{t-1}) + P_A^2 P_E - (1-P_A^2)\mu\Delta U
$$

The first term is the utility of the agent's previous offer. The other two terms
decide how far to move from it: emotional feedback contributes through $P_E$,
while recent concessions or demands contribute through $\Delta U$.

| Signal | Meaning in the paper | Effect on the next target |
| --- | --- | --- |
| $P_E$ | Weighted categorical facial-expression feedback | Negative feedback encourages concession; positive feedback permits a higher demand. |
| $P_A$ | How often the human changes move type when the agent changes its behavior | Its square weights emotion; the complementary weight controls reciprocity. |
| $\Delta U$ | Weighted utility changes over recent human offers, evaluated by the agent | A concession by the human tends to be reciprocated. |
| $\mu$ | Time-dependent degree of reciprocity | Scales the response to changes in offers. |

The behavior target is then combined with a time-based concession curve
(Equations 1–2):

$$
TU_{\mathrm{Hybrid}} = t^2 TU_{\mathrm{Times}} + (1-t^2)TU_{\mathrm{Behavior}}
$$

Early in a session, the interaction matters most. Near the deadline, the time
component gains weight. These are the paper's equations; the short paper contains
no research figures. [Equation sources](docs/paper/README.md).

## From the equation to a working agent

The [method example](reproduction/method.json) lets you follow the target calculation
with small, inspectable inputs. Change awareness or affect while keeping the offer
history fixed to see which term changes. [METHOD.md](METHOD.md) connects the
published equations to the maintained `solver-2021` preset and explains the
historical choices that the extended abstract leaves unspecified.

The three-page paper reports preliminary evidence of higher agent scores without
lower human scores, but does not supply a quantitative result table or a complete
experiment specification. The later [IVA 2025 paper](https://github.com/monurkeskin/An-Adaptive-Emotion-Aware-Strategy-IVA-2025)
develops the strategy and reports a fuller human–robot evaluation. Its results
belong to that later study.

## What you can explore

Work through the Solver equation, vary synthetic offer histories and inspect the resulting targets. The fruit example is a convenient demonstration domain; the short paper does not specify a complete original experiment configuration.

| Explore | Start with | What it shows |
| --- | --- | --- |
| Equation checks | [reproduction/method.json](reproduction/method.json) | Trace awareness, affect and reciprocal utility changes. |
| Example session | [configs/synthetic.json](configs/synthetic.json) | Inspect bids, decisions and a readable local report. |
| Historical scope | [METHOD.md](METHOD.md) | Separate the published equation from later implementation choices. |

The configurations, method checks and study guides are specific to this paper. The shared [NEGOTIATOR framework](https://github.com/monurkeskin/NEGOTIATOR-IJCAI-2024) runs the negotiation,
participant/conductor views and session analysis. Its exact **2.0.0** revision is
pinned in [framework.json](framework.json); installation brings it in automatically.

The maintained `solver-2021` preset implements the published categorical equation. Its opponent model, offer selection and handling of earlier implementation details are recorded in [METHOD.md](METHOD.md) and the engine's method guide. It is not a frozen snapshot of the 2021 experiment software.

## Try it yourself

Use Python 3.11 or 3.12 and Git. This first example runs locally without a robot,
camera or service account.

```bash
git clone https://github.com/monurkeskin/Solver-Agent-AAMAS-2021.git
cd Solver-Agent-AAMAS-2021
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python run.py --output demo-output
```

On Windows, create the environment with `py -3 -m venv .venv` and activate it with
`.venv\Scripts\Activate.ps1` in PowerShell.

Open **`demo-output/report/index.html`** to follow the example negotiation. The
output includes offers, utility trajectories, session records and exportable
figures. These are synthetic examples for exploring the software and method.
[Installation help](docs/compatibility.md).

### Read a calculation or open the study workspace

```bash
negotiator reproduce reproduction/method.json --output method-output
negotiator gui
```

In **New study → Import a paper or study configuration**, select
`configs/synthetic.json` for the demonstration, or `configs/protocol-template.json`
to inspect the paper's protocol template. The [study guide](docs/protocol.md)
explains the remaining protocol/asset requirements and device setup.

## Data and analysis

Participant records and recordings are not included. The examples use labeled
synthetic inputs so you can run the code and inspect its calculations. Recomputing
the human-study results requires authorized access to the original inputs and
the matching analysis procedure.

[Reproducibility guide](REPRODUCIBILITY.md) · [Paper-to-code map](paper-map.json) ·
[Analysis guide](docs/analysis.md)

## Build on the work

To change a paper condition, start with its configuration and add a small test
showing the intended behavior. Shared negotiation rules belong in NEGOTIATOR;
paper-specific profiles, protocols and result recipes belong here. The
[development guide](docs/development.md) walks through these boundaries and the
test-first workflow. [Contribution guide](CONTRIBUTING.md).

## Cite the paper

If you use this method or study design, please cite the associated paper:

```bibtex
@inproceedings{solveragent2021,
  title = {Solver Agent: Towards Emotional and Opponent-Aware Agent for Human-Robot Negotiation},
  author = {Keskin, Mehmet Onur and Çakan, Umut and Aydoğan, Reyhan},
  year = {2021},
  url = {https://www.ifaamas.org/Proceedings/aamas2021/pdfs/p1557.pdf}
}
```

The [citation file](CITATION.cff) provides the paper as the preferred citation.
For software provenance, also record the version and [archived 2.0.0 artifact](https://doi.org/10.5281/zenodo.22729008).
When using the shared engine in new research, cite the
[NEGOTIATOR framework paper](https://doi.org/10.24963/ijcai.2024/1012).
GPL-3.0-only; original contributors and sources are credited in [NOTICE](NOTICE).
