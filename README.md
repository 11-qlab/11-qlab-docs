# 11-qlab

Post-CMOS computing research: eight physics paths, one honest answer.

## The thesis

Every alternative computing technology wins against **digital CMOS**
(the deployed baseline) and loses against **room-temperature adiabatic
CMOS** (the theoretical floor). Seven measured packages and one
theoretical estimate prove this from eight different physics
directions.

## The packages

| # | Package | Physics | Tests | vs adiabatic | vs digital |
|---|---|---|---|---|---|
| 1 | [adiabatic-sim](https://github.com/11-qlab/adiabatic-sim) | CMOS / adiabatic / Landauer | 9 | 1× (floor) | 100× better |
| 2 | [sfq-sim](https://github.com/11-qlab/sfq-sim) | Josephson junction, 4K cooling | 9 | 126× worse | ~2× better |
| 3 | [rfl-sim](https://github.com/11-qlab/rfl-sim) | Sine-Gordon fluxons, reversible | 9 | 7.6× worse | ~14× better |
| 4 | [photonic-sim](https://github.com/11-qlab/photonic-sim) | MZI mesh, transceiver | 9 | 2053× worse | ~1000× better |
| 5 | [spintronics-sim](https://github.com/11-qlab/spintronics-sim) | LLG + STT, CoFeB pMTJ | 7 | 816× worse | memory, not logic |
| 6 | [memristor-sim](https://github.com/11-qlab/memristor-sim) | Crossbar VMM | 8 | 12× worse | 3300× better |
| 7 | [neuromorphic-spinnaker](https://github.com/11-qlab/neuromorphic-spinnaker) | LIF neurons + crossbar | 10 | 540× worse | 173× better |
| 8 | [system-energy](https://github.com/11-qlab/system-energy) | Overhead model | — | 1× (reference) | — |
| — | [qca-sim](https://github.com/11-qlab/qca-sim) | Molecular QCA (theoretical) | 22 | unmeasured | unmeasured |

## The system-level verdict

When control, memory, and I/O overhead are added to the device-level
energies, the ordering is unchanged: **adiabatic CMOS still wins**.

The system-level model shows:
- Device-level ratios 7.6× – 2053× narrow to 5× – 85× at the system level
- Why: adiabatic also pays control + memory overhead (4.5× multiplier)
- But no alternative narrows the gap to less than 5×

## The honest answer

| Question | Answer |
|---|---|
| Which alternative is best for logic? | RFL (5× worse than adiabatic) |
| Which is best for AI acceleration? | Memristor (11× worse than adiabatic) |
| Which is best against deployed digital? | Photonic (1000× better) |
| Which has the best theoretical potential? | QCA (never built) |
| Which actually wins? | **Room-temperature adiabatic CMOS** |

## Why the industry builds alternatives anyway

Every alternative beats **digital CMOS**, which is what's deployed:

| Technology | vs digital CMOS |
|---|---|
| Adiabatic | 100× better |
| SFQ | 2× better |
| RFL | 14× better |
| Photonic | 1000× better |
| Memristor | 3300× better |
| Neuromorphic | 173× better |

The industry funds what beats the deployed baseline, not what beats
the theoretical floor. That's why neuromorphic hardware gets $100M
rounds while adiabatic CMOS gets a few papers per year.

## The corollary

**The only way to reduce computing energy is to do fewer operations,
not faster ones.** Memristor and neuromorphic hardware win by
eliminating data movement. SFQ, RFL, and photonic lose by trying to
make individual operations faster (and paying cooling or transceiver
overhead).

Adiabatic CMOS embodies this principle at the technology level: slow
down by 100×, reduce energy by 100×, keep everything at room
temperature. It's not exciting. It's just the winner.

## Repositories

All packages are Apache 2.0, installable from PyPI, and backed by
tests:

```bash
pip install adiabatic-sim sfq-sim rfl-sim photonic-sim \
            spintronics-sim memristor-sim neuromorphic-spinnaker \
            system-energy
```

Or clone everything:

```bash
for pkg in adiabatic-sim sfq-sim rfl-sim photonic-sim \
           spintronics-sim memristor-sim neuromorphic-spinnaker \
           system-energy qca-sim qca-compiler; do
    git clone git@github.com:11-qlab/$pkg.git
done
```

License

Apache 2.0 for all packages and documentation.
