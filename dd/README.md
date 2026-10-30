# OTUS9r: GAMS-ready files

`dd/<scenario>/` holds what the TIMES model generator needs to run a
scenario without Veda: `<scenario>.run`, the `*.dd` files it includes,
`cplex.opt` and `times2veda.vdd`. Nothing else from the Veda export is kept,
and nothing was edited by hand.

| | |
| --- | --- |
| Source workbooks | tag `epaus9rt-v20.4`: EPAUS9rT_v20.4 as released by the US EPA, unchanged |
| Exported with | Veda2 v4.3.2.1 (DD export of the Veda cases `reference` and `tax1_wo_mou`) |
| Exported | 28 Oct 2026, by ESMA |
| TIMES version targeted | v4.9.7 ([etsap-TIMES/TIMES_model](https://github.com/etsap-TIMES/TIMES_model) @ `d9a6a25`) |
| Scenarios | `reference`, `tax1_wo_mou` |
| Checksums | `manifest.json`: every file with its size and SHA-256 |

The files are byte-exact (`.gitattributes`: no line-ending conversion), so
the checksums in `manifest.json` hold on every platform. TIMES.jl's
reference harness pins this folder by the SHA-256 of `manifest.json`.
`manifest.json` is kept exactly as written at the export; its `from` and
`imported` fields record where the export was checked before it was added
here.

## Checks made before publication (28-30 Oct 2026)

- Every file is complete, and both cases compile and preprocess under TIMES
  v4.9.7 @ `d9a6a25`.
- Both cases solve with GAMS 52.1.0 and CPLEX with REDUCE off. For
  `tax1_wo_mou`, CPLEX reports the optimum with unscaled infeasibilities;
  the model's objective is of the order of 1e11, and its scaling is an item
  for the redevelopment.
- TIMES.jl, an open translation of TIMES to Julia/JuMP, reproduces the
  coefficient stage of GAMS on both cases at 1e-9
  ([esma-ie/TIMESjl](https://github.com/esma-ie/TIMESjl)).

## Running a scenario

With GAMS and the TIMES source (v4.9.7) on the include path, from
`dd/<scenario>/`:

    gams <scenario>.run idir1=<path to TIMES_model> lp=cplex

The run file uses REDUCE YES, as Veda wrote it. Any LP solver GAMS offers
can replace CPLEX.
