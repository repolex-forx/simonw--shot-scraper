# Repolex Knowledge Graph of simonw/shot-scraper

RDF knowledge graph data for [simonw/shot-scraper](https://github.com/simonw/shot-scraper), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/shot-scraper
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 760c11449fd3ceb2132ca1e67c70a53bde32b56b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 760c11449fd3ceb2132ca1e67c70a53bde32b56b
│           └── chunk-001.nq.gz
├── blob
│   ├── 025211a18a0a0e8e15b21d47218bac1fa29b3faa.nq.gz
│   ├── 0432d5daad9dfeff0ec7fd6ea27de9cd4200ea8a.nq.gz
│   ├── 070a74ca59310ec0a4312957ef37077821808cb1.nq.gz
│   ├── 091663dde04a804bba225def19684a2543ec8cc1.nq.gz
│   ├── 2077478342b9f15b9292abc55ddbcba5b32f0ca6.nq.gz
│   ├── 24466d8697a34de12840ec39e6a5de441965cc36.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2f372ee93bfec5c370e522eae3e5e2be93fa8761.nq.gz
│   ├── 3c8693f2b2b35b2e19b0a9043223a9ebd4569846.nq.gz
│   ├── 4236e0e5a125ebe36dae146c17507ea6dbe4176b.nq.gz
│   ├── 519b4775dbe204994784bef5f0ec14cc793586b8.nq.gz
│   ├── 58428a910f5e73a6bb578dfadd2a5425a0928ac2.nq.gz
│   ├── 5d66383f68de826c507a8de969f554b7d33c6197.nq.gz
│   ├── 5e4131ff76dfb9d0887956504a7c59aaac52427d.nq.gz
│   ├── 5e69d48156100da14d9f016dbab020031e3f2798.nq.gz
│   ├── 6fcfc80d19fd162afc6e30177a4f8d489389c207.nq.gz
│   ├── 71974e9f666d0ce55cde8b503d21842b24a51807.nq.gz
│   ├── 76b5dc9822a26f227e58736844016defdae77626.nq.gz
│   ├── 7d80404aa995d53b459e4db2ed658c34e412ab04.nq.gz
│   ├── 802a705e2ec5f7c3b8a5bc41561b15790c83a891.nq.gz
│   ├── 8a78d612505bdb294e7016c74fd93b0c86e467bb.nq.gz
│   ├── 97ce818ecb9922d3810a86331fbdcc0fda956082.nq.gz
│   ├── 9e5a15cd75c5b7eee07ec78effdcee281e1a5e7f.nq.gz
│   ├── 9f20c88b8ca8835ee66cbc5b7206449d625fdcff.nq.gz
│   ├── a279768f126b210e024ba7e983a9ee2ccfd15118.nq.gz
│   ├── a4bc4ce15a6605dfa6c7f618ada75649ac4b5aed.nq.gz
│   ├── b2676eeea5afcc9fda5ee41fcb0657b08da0d025.nq.gz
│   ├── bd7708dbec7a39ca578648d905237526c01affa7.nq.gz
│   ├── c19b50dda553271a76b9c7dc913f4421d14a2894.nq.gz
│   ├── c31934822ae18d7cd29a73aa333a92901ecb5eb4.nq.gz
│   ├── c88c80737ec96d6114569589b3190b582bd7f3e1.nq.gz
│   ├── cc31c725dd69968db7b17e303fc2e28cd9ecf291.nq.gz
│   ├── e35d8850c9688b1ce82711694692cc574a799396.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f00d2b3d30e866eebd86a811304f1feeb9293d7e.nq.gz
│   └── f865f2a003e7bb3900f89c47537f1f0d72ce34e6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 760c11449fd3ceb2132ca1e67c70a53bde32b56b.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[simonw/shot-scraper](https://github.com/simonw/shot-scraper)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
