# Solver Agent: Towards Emotional and Opponent-Aware Agent for Human-Robot Negotiation

[![Software archive](https://zenodo.org/badge/DOI/10.5281/zenodo.22729008.svg)](https://doi.org/10.5281/zenodo.22729008)

**Independent research companion · maintained release 2.0.0**

[![Tests](https://github.com/monurkeskin/solver-agent-2021/actions/workflows/tests.yml/badge.svg)](https://github.com/monurkeskin/solver-agent-2021/actions/workflows/tests.yml)
[Paper](https://www.ifaamas.org/Proceedings/aamas2021/pdfs/p1557.pdf) · [Method](METHOD.md) · [Reproduce](REPRODUCIBILITY.md) · [Protocol](docs/protocol.md) · [Contribute](docs/development.md)

Quadratic time target, recent reciprocal utility changes, categorical affect and opponent awareness.

This package contains this paper's configurations, method requirements, independent
checks and analysis recipes. It uses a pinned [NEGOTIATOR](https://github.com/monurkeskin/NEGOTIATOR)
engine; no second engine checkout or robot is needed for the first example.

| Start here | What you will get |
| --- | --- |
| First-time user | A short generated negotiation, session records and a readable report |
| Researcher reading the paper | [Paper map](paper-map.json), exact point tables where recovered, equation checks and result availability |
| Contributor | [Module boundaries and test-first example](docs/development.md), extensible configs and reusable engine contracts |

## Run your first example

Use Python 3.11 or 3.12. Clone this repository, then run:

```bash
git clone https://github.com/monurkeskin/solver-agent-2021.git
cd solver-agent-2021
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python run.py --output demo-output
```

On Windows, create the environment with `py -3 -m venv .venv` and activate it
with `.venv\Scripts\Activate.ps1` in PowerShell. Git is required for the pinned
engine dependency. [Troubleshooting and compatibility](docs/compatibility.md).

Open `demo-output/report/index.html`. The output includes full-precision JSON/CSV,
a workbook, figures, immutable source records and a timing receipt. This is a
**synthetic functional example**; it does not reproduce human participants or an
emotional, gesture or embodiment benefit. Existing output directories are preserved.

![Protocol overview: configuration, isolated sessions, durable events and analysis.](docs/images/protocol.svg)

## Inspect the method and run the GUI

```bash
negotiator reproduce reproduction/method.json --output method-output
negotiator cite demo-output/records --format bibtex
negotiator gui
```

In **New study → Import a paper or study configuration**, choose
`configs/synthetic.json` to inspect the hardware-free demonstration, or
`configs/protocol-template.json` to inspect the published-protocol template and its missing
requirements. Participant and conductor use separate views. [Step-by-step protocol guide](docs/protocol.md).

## What can currently be reproduced?

| Target | Scope |
| --- | --- |
| `method.json` | Recompute and check against independent references |
| `paired-example.json` | Recompute and check against independent references |
| `published-results.json` | Unavailable original inputs; no numbers fabricated |

The three-page paper does not provide a complete recoverable participant protocol. The fruit configuration is a method demonstration.

Original human records and some historical settings/assets remain unavailable.
[REPRODUCIBILITY.md](REPRODUCIBILITY.md) explains every target and its limits;
[paper-map.json](paper-map.json) records full, partial and unverified requirements
separately. A passing synthetic test does not establish historical experiment parity.

## Cite this work

Cite the associated paper when using or studying its method. Also cite the engine
and record the exact software version used; `negotiator cite` extracts citations
from executed session records.

```bibtex
@inproceedings{solveragent2021,
  title = {Solver Agent: Towards Emotional and Opponent-Aware Agent for Human-Robot Negotiation},
  author = {Keskin, Mehmet Onur and Çakan, Umut and Aydoğan, Reyhan},
  year = {2021},
  url = {https://www.ifaamas.org/Proceedings/aamas2021/pdfs/p1557.pdf}
}
```

[CITATION.cff](CITATION.cff) offers the paper as the preferred citation.
[CodeMeta](codemeta.json), [source notices](NOTICE) and
[framework identity](framework.json) support versioned attribution. The software
is GPL-3.0-only. No paper working tree, participant recording or licensed robot
asset is bundled.
