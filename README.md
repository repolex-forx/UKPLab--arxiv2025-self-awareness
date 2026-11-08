# Repolex Knowledge Graph of UKPLab/arxiv2025-self-awareness

RDF knowledge graph data for [UKPLab/arxiv2025-self-awareness](https://github.com/UKPLab/arxiv2025-self-awareness), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download UKPLab/arxiv2025-self-awareness
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e95f07908f0c4051baa53fc84b8661b7710a2354
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e95f07908f0c4051baa53fc84b8661b7710a2354
│           └── chunk-001.nq.gz
├── blob
│   ├── 02ed7e8af8d9dc3ce7b945fa1f63640615159338.nq.gz
│   ├── 040b59079acfd6d6dcd06e931c3933f2453588b1.nq.gz
│   ├── 0b0e1ff6decc8c06895bd405a92531d9f73aacd9.nq.gz
│   ├── 0ba3bdbf8eca9e0f9e97debef44706d24f6980f7.nq.gz
│   ├── 159362485cad3814c6c8e2dda50c854318df271b.nq.gz
│   ├── 1ce9ade87c0065fe56ad22254e19126c4b02030c.nq.gz
│   ├── 1d74e6649b6a7c8ac205281d35a2c68b8b5e5688.nq.gz
│   ├── 1f752e1104ba4a515b553fc3ddd04f3b1f42def5.nq.gz
│   ├── 1fc0845f68093efe97477249f5211af4867775b5.nq.gz
│   ├── 2a1bc791eb97159fc917c6fdc281416570543f78.nq.gz
│   ├── 2b15b128e5af23d003722bf3a091ee42a986f6ad.nq.gz
│   ├── 2c0b25620e79bf22c05f10e2396852993c14b1f9.nq.gz
│   ├── 33e3cdb8f0309da2adcf4440e35dc26b393ab9a6.nq.gz
│   ├── 353ca180b3f4b91bb1f85e2e6fe63a36d288a3da.nq.gz
│   ├── 369d29ef13217e9d49ac9309327f3be3e4f6bb1f.nq.gz
│   ├── 54b429143ad1853c21d27345cee6582dd770dc71.nq.gz
│   ├── 60a91557aea3457d2950c212e325d9a7500d84c0.nq.gz
│   ├── 79a9f10a2f157f5f398d498f2327ef4c2d89dd80.nq.gz
│   ├── 7d0ccf59ffd1b76b0580608d29659235e106395d.nq.gz
│   ├── 7faebddf7a6b33036fbfd1804183addb421ae215.nq.gz
│   ├── 84448de2cfe22f5f263d2d2018b7ab92e82bc485.nq.gz
│   ├── 8a9ecc2ea99d607e92feae1656ddbf6fdd82a2c1.nq.gz
│   ├── 9050e2149c3ab5d12ca0a0ab7e1831a969ddef1d.nq.gz
│   ├── 96bae7114b4d6eaf65d96176a16ddd0bb959fc83.nq.gz
│   ├── 9c7a2caf4b36b1b22b2ed5db35aebde297dbdf9a.nq.gz
│   ├── b74bcdb7883b789a941d76116385870903859dd8.nq.gz
│   ├── cbe8e61179854f64eef9a3ec70c331bb24d2da9e.nq.gz
│   ├── d01a3d2f9b419ae3232619b179699c05e7d09523.nq.gz
│   ├── db82c6789aa2b17700557df37279bf7d7d444fb9.nq.gz
│   ├── e3e7d6084bb90681e5f1b11cafb5e366c3a835c7.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f080a586ba30795abf47ef0c2794ba9f709c4ba9.nq.gz
│   ├── f49a4e16e68b128803cc2dcea614603632b04eac.nq.gz
│   ├── fd8f39385eff8db7ca8892a7282fabce3db910d2.nq.gz
│   └── fe2c333dcb01213dd8133026bc316804da91c522.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e95f07908f0c4051baa53fc84b8661b7710a2354.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 42 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[UKPLab/arxiv2025-self-awareness](https://github.com/UKPLab/arxiv2025-self-awareness)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
