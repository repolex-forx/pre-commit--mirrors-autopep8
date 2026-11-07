# Repolex Knowledge Graph of pre-commit/mirrors-autopep8

RDF knowledge graph data for [pre-commit/mirrors-autopep8](https://github.com/pre-commit/mirrors-autopep8), parsed by [repolex](https://repolex.ai).

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
rlex download pre-commit/mirrors-autopep8
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ff31678cfc7e06898ba918005b1f6f3099b46a66
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── ff31678cfc7e06898ba918005b1f6f3099b46a66
│           └── chunk-001.nq.gz
├── blob
│   ├── 2165f8f9b6a830a9d8dd3d2857d7fb86eba1d250.nq.gz
│   ├── 96c6b0a32c279d6fef926d161d9e36c6f30242cd.nq.gz
│   ├── b0b392d4485f339c17c8117ddeb03ba4cc0d636f.nq.gz
│   ├── c4832d03ddbe605e61f9cf46e60bc5b1cc7f2e62.nq.gz
│   ├── d86d9ea06347dbd79c04079484155ea94fa2c3ed.nq.gz
│   └── f6daed45d0378dbb6e7a0519781317a2453f3d1b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ff31678cfc7e06898ba918005b1f6f3099b46a66.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 13 files
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

[pre-commit/mirrors-autopep8](https://github.com/pre-commit/mirrors-autopep8)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
