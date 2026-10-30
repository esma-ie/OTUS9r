# OTUS9r: Open TIMES USA 9-Region Model

OTUS9r is an open energy-system model of the United States in nine
regions, for the IEA-ETSAP TIMES model generator. It is developed and
maintained by Energy Systems Modelling Analytics Ltd (ESMA), Galway,
Ireland, and published under an open licence (CC BY-SA 4.0).

> **Status: under redevelopment.** This repository holds the US EPA's
> EPAUS9rT_v20.4 as released (tag `epaus9rt-v20.4`) and its GAMS-ready
> export (`dd/`). ESMA's redevelopment follows as later commits.

## Not a US EPA model

OTUS9r is **not developed by, maintained by, reviewed by or endorsed by the
United States Environmental Protection Agency (US EPA).** It is an
independent redevelopment by ESMA.

The US EPA's 9-region TIMES database, **EPAUS9rT**, is the starting point
for that redevelopment. Everything published in this repository after that
starting point is ESMA's work, and the US EPA bears no responsibility for
it. Results produced with OTUS9r are not US EPA results and should not be
presented or cited as such. Nothing in this repository uses the US EPA's
name, seal or logo to suggest endorsement.

## Lineage and provenance

| | |
| --- | --- |
| Starting point | EPAUS9rT, the US EPA's 9-region database for the TIMES model generator, developed by the EPA Office of Research and Development (ORD) |
| EPAUS9rT version | EPAUS9rT_v20.4, published by EPA ORD on data.gov ([DOI 10.23719/1528539](https://doi.org/10.23719/1528539)); the archive's SHA-256 is recorded with its import |
| Status of the starting point | US EPA data are in the US public domain by default, "unless otherwise specified" ([EPA data licence](https://pasteur.epa.gov/license/sciencehub-license.html)) |
| Redevelopment | ESMA Ltd, from 2026 |

EPAUS9rT_v20.4 was released with Zalesak, Kittner, Loughlin and Kaplanakman
(2024), *Environmental Research: Energy* 1: 045018
([DOI 10.1088/2753-3751/ad958b](https://doi.org/10.1088/2753-3751/ad958b)).

How provenance is kept in this repository:

1. **The original first.** The first model commit holds the EPAUS9rT files
   exactly as released by the US EPA, unchanged. The commit message names
   the release and gives the SHA-256 checksum of the source archive, and the
   commit is tagged `epaus9rt-v20.4`. The import leaves out the archive's
   `Exported_files/` folder: 13 CSV result exports of the study the release
   accompanies (1.7 GB; nine are larger than GitHub's 100 MB file limit).
   They are outputs, not model inputs, and stay in the EPA archive; the
   import commit lists their names, sizes and SHA-256 checksums. Workbook
   properties and external links are as the US EPA released them.
2. **ESMA's changes after it.** Every change ESMA makes follows as later
   commits, so `git diff epaus9rt-v20.4` shows exactly how OTUS9r
   differs from the US EPA's original.
3. **GAMS-ready files with their origin.** Files exported from the Veda
   workbooks for GAMS are kept in `dd/<scenario>/`. `dd/README.md` records
   how each export was made: the source commit, the Veda version, the TIMES
   version targeted and the date.

## Licence

OTUS9r as distributed here, and ESMA's contributions to it, are licensed
under the Creative Commons Attribution-ShareAlike 4.0 International licence
([`LICENSE`](LICENSE), [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)).
Material that originates from the US EPA remains in the US public domain;
this licence does not restrict any use of public-domain material that the
law allows.

When you use or adapt OTUS9r:

- credit "OTUS9r, Energy Systems Modelling Analytics Ltd (ESMA)" and the
  original EPAUS9rT database by the US EPA Office of Research and
  Development;
- link to the CC BY-SA 4.0 licence and say whether you made changes;
- share your adaptations under the same licence (ShareAlike).

OTUS9r is provided as is, without warranties of any kind (section 5 of the
licence).

## Running the model

OTUS9r runs with the IEA-ETSAP TIMES model generator
([etsap-TIMES/TIMES_model](https://github.com/etsap-TIMES/TIMES_model),
GPL-3.0-or-later) under GAMS and an LP solver. The Veda workbooks can be
edited with Veda; the GAMS-ready files in `dd/` need only TIMES and GAMS.

OTUS9r is also one of the test models for TIMES.jl
([esma-ie/TIMESjl](https://github.com/esma-ie/TIMESjl)), an open
translation of TIMES to Julia/JuMP that is developed and tested only on
openly licensed models.
