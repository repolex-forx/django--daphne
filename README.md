# Repolex Knowledge Graph of django/daphne

RDF knowledge graph data for [django/daphne](https://github.com/django/daphne), parsed by [repolex](https://repolex.ai).

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
rlex download django/daphne
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d7a005258cce3ad7893a759274647f46331d782e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d7a005258cce3ad7893a759274647f46331d782e
│           └── chunk-001.nq.gz
├── blob
│   ├── 024479dac2a393a9f942428cc27c841611c4a2da.nq.gz
│   ├── 058ad7e894f73038e00811dd4779469794f68688.nq.gz
│   ├── 10357bdf782239dde7d271d35bb3d18c66d7a9dc.nq.gz
│   ├── 1cc02213e99ad993d37455cbc003b3858b3ff63c.nq.gz
│   ├── 2107b5dd8e97a9e4bf899dfb83df99cf65658499.nq.gz
│   ├── 220c1ef04f0042ad62e5c215822226fb6135dcaa.nq.gz
│   ├── 22f6480a30312cfe0e4aa6ec425bfa53b5b15178.nq.gz
│   ├── 27157166413411ed660c58b86bdaecd62b5f642e.nq.gz
│   ├── 2a8057cfc1258c107acbf581f3164947b91a0ead.nq.gz
│   ├── 2cf8f37eec60f272ea54889b1df762850303e01a.nq.gz
│   ├── 313a315482f77210d8e75066cb144d48a6a97c52.nq.gz
│   ├── 40fcedd5efdf928a3fb3221a5fbcf14a10f4d9e4.nq.gz
│   ├── 48b23bd90ad901cccd0e41ee2156661f028cac43.nq.gz
│   ├── 4a7cbf34b7f398d760c5d58cb2e40e8a4cb894fa.nq.gz
│   ├── 59f44e7d895f9e667039bc9e087f6e0659db0efa.nq.gz
│   ├── 5ba11df5f15de9a4ddf4e4e5b1ab3a99e490d1ba.nq.gz
│   ├── 5f4f225dd282aa7e4361ec3c2750bbbaaed8ab1f.nq.gz
│   ├── 8c7aade435b02ebc7015d36510be605d1fef3da9.nq.gz
│   ├── 9324c8450a4f79e155823ceece8b9cf509aab2fe.nq.gz
│   ├── a367f157bb1ad151d15129b3eedd39fc09cb5d82.nq.gz
│   ├── a754e57612808a3a38d6a403ba72fc1fa700633e.nq.gz
│   ├── b1e29c3b88685a44e7da94c32ce392a5f5557727.nq.gz
│   ├── b634cd03681f71e5c6d0b4b9dac4461ebaaa0e9c.nq.gz
│   ├── b6a377d44cf8723a9eabb643c6a583cd36e9cddc.nq.gz
│   ├── b8ef1e168e8aece623ae6c51633caa44c32fa7f2.nq.gz
│   ├── b97364f20319aff06fe7144affa67164db4347e0.nq.gz
│   ├── b987aed5c48732e1dabcb5350898868577cc464b.nq.gz
│   ├── be8772c846ec151084c795390e26f4b58cc42437.nq.gz
│   ├── bf385143ba0fba136b138ff514674403f98e6ee1.nq.gz
│   ├── c4abc06cdc6df93f210cd7b519a109af846c8c0d.nq.gz
│   ├── d60ef28bb79c6380d056303579ae104265f6cc3a.nq.gz
│   ├── de104db853965374bb956b4e7cb9daec9b3d447a.nq.gz
│   ├── e18138ada933c20eef971d94bc0988de4793f397.nq.gz
│   ├── e5903e0b83dc737c6590aed92cc76b85b8613929.nq.gz
│   ├── e5a80c217a12c0891c9c70a29ce39df7dd5cbd8b.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f0fe37653c2950eda27b17db3f845cd6bfac00e1.nq.gz
│   └── fa000b220e1a45ccef9b50efb6f2ad924bdb660c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d7a005258cce3ad7893a759274647f46331d782e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 46 files
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

[django/daphne](https://github.com/django/daphne)

---
*Parsed on 2026-10-19 by [repolex](https://repolex.ai)*
