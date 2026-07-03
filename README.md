# EEE Verifier Releases - Public Byte Mirror

This repository is a world-readable byte mirror for Alekore EEE verifier sidecar release artifacts.
It exists so consuming builds can fetch mirror bytes anonymously, without GitHub tokens.

## Authority boundary

- This repository is not a trust root.
- This repository is not a source repository.
- This repository is not governance authority for MemoriaIA, Alekore EEE, or any product release.
- This repository does not enforce authorization. It is public by design.
- Authorization, trust, and acceptance are enforced only by the consuming repository's repo-controlled pin manifest and build gates.
- Mirror-hosted `.sha256` files are convenience metadata only. They must not be used as the authority by a consuming build.
- A consuming build must verify fetched bytes against its own pinned SHA-256 and exact byte size before staging any artifact.

## Current mirrored release

Tag:

```text
eee-verifier-sidecar-v0.1.1-internal-alpha
```

Published mirror assets:

| Asset | Required size | Required SHA-256 |
| --- | ---: | --- |
| `eee-verifier-sidecar.exe` | 87249920 | `7234c1c5e02c3679778c82982b9892e07ed453b0c7ed123e36a024840567217c` |
| `eee-verifier-sidecar.provenance.json` | 1150 | `72b345952db10dda33e93f6ad1653df156af570752b2bb9cfd91d82dc83f6c68` |
| `eee-verifier-sidecar.exe.sha256` | 91 | `e3207cd381f319593b085581fc68baf2b6d664ea993a5256eefd95353a54ae45` |

The table above is public orientation metadata. The consuming repository's pin manifest remains authoritative.

## Consumption rule

A build that consumes this mirror must fail closed if any of these conditions occurs:

- Anonymous fetch fails.
- The fetched executable size differs from the pinned size.
- The fetched executable SHA-256 differs from the pinned SHA-256.
- The hash tool fails or cannot read the staged artifact.
- A local cache is present but has not been verified against the repo-controlled pin manifest.

The build must not continue without the sidecar and must not fall back to unverified local bytes.

## Asset replacement policy

Release asset replacement is not an allowed operation for this mirror. Any byte change requires a new mirror tag, a new digest/size record, and a separate consuming repository pin update. Existing release assets are treated as append-only operational evidence and must not be overwritten in place.

## Repository posture

- Public releases only.
- No source code.
- No product support surface.
- No Actions-based build authority.
- No issues, wiki, discussions, or projects as support or governance surfaces.
- This public repository intentionally stores release mirror assets and README metadata only. It must not intentionally store source files, private keys, signing keys, or secrets.

## Non-claims

These artifacts are internal-alpha verifier artifacts. This repository makes no product, production, installer, release-readiness, compliance, admissibility, legal sufficiency, court-readiness, government-attestation, or broad Gate closeout claim.