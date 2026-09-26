# Changelog

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Nothing released.

## [Unreleased]

### Added
- Repository scaffold, AGPL-3.0-or-later, scope statement.
- Distribution decision recorded: HTTPS-first, peer-to-peer as an optional accelerator
  (madde 25) - this removes private torrents, tracker operation and peer IP visibility from
  the first release.

### Changed
- Pinned toolchain moved from 1.83.0 to 1.98.1, matching the other Rust
  repositories. 1.83 is from November 2024 and predates edition 2024, which
  current dependency trees require. Nothing here builds yet, so this is only
  consistency -- but leaving it behind would break the first real build.

### Notes
- Implementation gated behind the Faz L1 checklist (madde 30).
