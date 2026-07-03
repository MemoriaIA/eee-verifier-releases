# EEE Verifier Releases - Public Byte Mirror

This repository is a public byte mirror for Alekore EEE verifier sidecar release artifacts.
It exists so authorized consuming builds can fetch the verifier sidecar anonymously, without GitHub tokens.

## Authority boundary

- This repository is not a trust root.
- This repository is not a source repository.
- This repository is not governance authority for MemoriaIA, Alekore EEE, or any product release.
- The consuming repository's repo-controlled pin manifest is the trust root for build verification.
- Mirror-hosted `.sha256` files are convenience metadata only. They must not be used as the authority by a consuming build.
- A consuming build must verify fetched bytes against its own pinned SHA-256 and exact byte size before staging any artifact.

## Current mirrored release

Tag:

```text
eee-verifier-sidecar-v0.1.1-internal-alpha
```

Source release tag:

```text
eee-verifier-sidecar-v0.1.1-internal-alpha
```

Source target commit:

```text
5b466b8070f9c2737438124026b3b136714b66ff
```

Published mirror assets:

| Asset | Required size | Required SHA-256 |
| --- | ---: | --- |
| `eee-verifier-sidecar.exe` | 87249920 | `7234c1c5e02c3679778c82982b9892e07ed453b0c7ed123e36a024840567217c` |
| `eee-verifier-sidecar.provenance.json` | 1150 | `72b345952db10dda33e93f6ad1653df156af570752b2bb9cfd91d82dc83f6c68` |
| `eee-verifier-sidecar.exe.sha256` | 91 | `e3207cd381f319593b085581fc68baf2b6d664ea993a5256eefd95353a54ae45` |

## Consumption rule

A build that consumes this mirror must fail closed if any of these conditions occurs:

- Anonymous fetch fails.
- The fetched executable size differs from the pinned size.
- The fetched executable SHA-256 differs from the pinned SHA-256.
- The hash tool fails or cannot read the staged artifact.
- A local cache is present but has not been verified against the repo-controlled pin manifest.

The build must not continue without the sidecar and must not fall back to unverified local bytes.

## Repository posture

- Public releases only.
- No source code.
- No secrets.
- No private keys.
- No signing keys.
- No Actions-based build authority.
- No issues, wiki, discussions, or projects as support or governance surfaces.

## Non-claims

These artifacts are internal-alpha verifier artifacts. This repository makes no product, production, installer, release-readiness, compliance, admissibility, legal sufficiency, court-readiness, government-attestation, or broad Gate closeout claim.