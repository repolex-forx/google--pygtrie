# Repolex Knowledge Graph of google/pygtrie

RDF knowledge graph data for [google/pygtrie](https://github.com/google/pygtrie), parsed by [repolex](https://repolex.ai).

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
rlex download google/pygtrie
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 64ee0836f41a59919ecf8a59b0c7e2f7f1b8c5ba
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 64ee0836f41a59919ecf8a59b0c7e2f7f1b8c5ba
│           └── chunk-001.nq.gz
├── blob
│   ├── 0c41e055a35dbb615688151505456cc305140a9e.nq.gz
│   ├── 2516142770acdcec615fda5c4c9c822e68d3095e.nq.gz
│   ├── 2ce1750a713d2513c662f059b18857d13adff3b8.nq.gz
│   ├── 3143b59f4e6408498dc8d875ab7f4e7e13bf4e01.nq.gz
│   ├── 3f647ce0075762b7ffbd31b4cf324bfab2546916.nq.gz
│   ├── 59634df3074136f42f315223a07d89dabc1f61e1.nq.gz
│   ├── 77ab0d21f97bc56fdb619805e0ac199dd7a7f0dd.nq.gz
│   ├── 95b16395732cd28ba6cca752eb0f9cee8413b8a6.nq.gz
│   ├── a1e780cb4bd9306d02eb4c66fd93c794bff16afa.nq.gz
│   ├── d2a58dc73dbe73e7601f8ac32e3b34902d7384b1.nq.gz
│   ├── d645695673349e3947e8e5ae42332d0ac3164cd7.nq.gz
│   ├── e22535a015f4ec757318f1001bf64012f1ee38f9.nq.gz
│   ├── edb0592bfc5d173cb0740827bbdc8bf79c3c23f5.nq.gz
│   └── f698a01d9580006f8cd4d9cff4861388d1734e8d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 64ee0836f41a59919ecf8a59b0c7e2f7f1b8c5ba.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[google/pygtrie](https://github.com/google/pygtrie)

---
*Parsed on 2026-10-18 by [repolex](https://repolex.ai)*
