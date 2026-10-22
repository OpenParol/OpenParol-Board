# Hardware Versioning and Release Guidelines

This document defines the versioning convention and release process for OpenParol hardware. Its purpose is to keep design files, fabricated boards, Git history, and released manufacturing assets consistent and traceable.

## Versioning Convention

Hardware revisions use the following project-specific format:

`v<MAJOR>.<MINOR>[-beta[.<REVISION>]]`

The `MAJOR.MINOR` part identifies the board revision. The `-beta` suffix identifies a prototype that is undergoing physical validation. The optional `.<REVISION>` number identifies a subsequent beta iteration created after a correction.

### Lifecycle and Naming

| Phase | Git reference | PCB silkscreen | Tag or release | Definition |
| :--- | :--- | :--- | :--- | :--- |
| **Development** | `dev` branch | `Rev v0.1` | None | The schematic and PCB are actively being developed. The design may change and is not yet ready for fabrication. |
| **Beta prototype** | `beta` branch or tag | `Rev v0.1-beta` | `v0.1-beta` | The design is frozen for a prototype manufacturing run and is awaiting assembly and laboratory testing. |
| **Beta revision** | `beta` branch or tag | `Rev v0.1-beta.1`, `Rev v0.1-beta.2`, ... | `v0.1-beta.1`, `v0.1-beta.2`, ... | A correction is made to the production files before the next prototype run or test cycle. |
| **Stable release** | Tag on `master` | `Rev v1.0` | `v1.0` | The physical board has passed the required electrical and functional tests and is ready for production use. |

## GitHub Release Artifacts

Every beta and stable GitHub release must include a manufacturing package containing the following assets:

```text
├── Gerber_<VERSION>.zip        # Production Gerbers & Drill files
├── Schematic_<VERSION>.pdf     # Standalone schematic sheet(s) in PDF format
└── 3D_Model_<VERSION>.step     # Step model for mechanical enclosure integration
```