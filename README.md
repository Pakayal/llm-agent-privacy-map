# Privacy in LLM agents: coded corpus

Coded records for the systematic map *Privacy in LLM Agents: A Systematic Map of the Evidence* by Pakayal Edmond Boar.

The map covers primary studies of the privacy of data that an LLM agent reads, writes, or transmits while it acts. The search window is 1 January 2023 through 31 October 2026. Candidates were assembled from arXiv, the ACL Anthology, and DBLP.

## What is in this repository

- `data/studies.json` records 121 studies that were read in full. Each code is stored with a short passage from the full text. One hundred and nineteen studies are included. Two are excluded after reading, under the rule in `exclusion_rule`.
- `data/studies.csv` is the same classification without the passages.
- `data/not_obtained.json` lists the three candidates for which no open English full text was available. They are excluded and were not coded.
- `CODEBOOK.md` defines the fields.

The full texts are not in this repository. A passage is included only so that a code can be checked against the study. Passages are copied from the PDF text and may contain line-break artifacts from that extraction.

Authors are included when the source record had them. Fourteen included studies are identified by title, year, and an ACL Anthology key or a DOI.

## How to read a record

A study can have more than one value for the subject, the privacy notion, the surfaces, the channels, and the adversary. `surfaces_problem` is the locations the study's question depends on. `surfaces_evaluation` is the locations the experiment uses. The two lists are separate.

`database_memory_agent_path` is true only when the evaluation follows one fact from a database read, into a memory write, and then to another agent. It is false for every study in this release.

## Counts for the 119 included studies

| Item | Count |
| --- | ---: |
| Confidentiality | 110 |
| Data minimization | 49 |
| Contextual integrity | 45 |
| Consent | 18 |
| Purpose limitation | 11 |
| Formal privacy | 5 |
| Invoking person | 86 |
| Person named in a record | 55 |
| Organization | 19 |
| Another user of a shared system | 9 |
| Final answer inspected | 63 |
| Memory store in the evaluation | 43 |
| Memory write inspected | 8 |
| Utility assessed | 91 |
| Deletion assessed | 1 |
| Problem surface absent from the evaluation | 35 |
| One fact across a database, memory, and a second agent | 0 |
