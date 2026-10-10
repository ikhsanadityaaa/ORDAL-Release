# ORDAL Desktop Releases

This repository is the **artifact-only distribution endpoint** for desktop updates of [ORDAL](https://www.applywithordal.com/).

**Source code is NOT hosted here.** The application source remains in the private `ORDAL-App` repository. This public repository is used exclusively to publish reviewed binary release assets for existing desktop users.

## Release contract

ORDAL publishes one GitHub Release tagged `ordal-vMAJOR.MINOR.PATCH` for each completed version. Every release must include these six files:

| Platform | Full-runtime ZIP | Signature manifest |
| --- | --- | --- |
| Windows x64 | `ORDAL-runtime-VERSION-windows-x64.zip` | `ORDAL-runtime-VERSION-windows-x64.zip.manifest.json` |
| macOS Intel | `ORDAL-runtime-VERSION-macos-x64.zip` | `ORDAL-runtime-VERSION-macos-x64.zip.manifest.json` |
| macOS Apple Silicon | `ORDAL-runtime-VERSION-macos-arm64.zip` | `ORDAL-runtime-VERSION-macos-arm64.zip.manifest.json` |

Each manifest contains a SHA-256 checksum, exact file size, source revision and Ed25519 signature. The desktop application **pins the public verification key in its own installed bundle**; it must not trust an unverified key downloaded from a release.

Publication is performed by the **protected workflow in ORDAL-App** only. Builds run per platform, must pass tests and integrity checks, are first uploaded to a **draft** release, and only become publicly visible when **all three platforms** pass final read-back verification.

## Publication policy

- Do not upload source code, database dumps, user data, payment keys, environment files, access tokens or a **private signing key**.
- Never add the private signing key to this repository, Git history, GitHub release assets or issue comments.
- Never manually mark an incomplete draft release as published.
- If any artifact fails verification, keep the release as a draft and investigate.
- Official user-facing update offers only appear after a complete verified release is published.
- This repository should be **Public** before production releases are enabled so desktop clients can download releases without GitHub authentication.
- GitHub's public source visibility for this repository **does not** change the private source code repository's visibility.

## Current status

Infrastructure setup in progress. **No production update has been published or authorized.** Signing-key creation is explicitly deferred to the owner.

The repository name used by the clients and publishing workflow is:

`ikhsanadityaaa/ORDAL-Release`
