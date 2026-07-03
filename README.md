# EEE Verifier Releases — Public Byte Mirror

This repository is a **public byte mirror only** for Alekore EEE verifier
sidecar release binaries. It exists so that consuming builds can fetch the
sidecar executable anonymously, without tokens.

## Trust rule

- This mirror is **NOT a trust root**.
- The consuming repository's **repo-controlled pin manifest** (MemoriaIA) is
  the only build trust root: fetched bytes are verified there against a pinned
  SHA-256 and exact byte size.
- The `.sha256` files hosted here are **convenience metadata only**. They are
  never used as a verification authority by any consuming build.

## Contents

- Releases only. No source code. No issues, wiki, discussions, or workflows.
- Each release mirrors, byte-identical, a source release from the private
  `alekore-execution-evidence-engine` repository, using the identical tag.

## Non-claims

Internal alpha artifacts. No product, production, installer, compliance,
admissibility, or legal claim of any kind.
