# Changelog

All notable changes to this project are documented in this file.

This project is a fork of [mdlayher/apcupsd_exporter](https://github.com/mdlayher/apcupsd_exporter). The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- `Describe` now sends static metric descriptors without connecting to apcupsd, so registration no longer depends on NIS availability.
- Pin staticcheck to v0.8.2 in CI instead of `@latest`.

### Fixed

- Scrapes are now bounded by the 5-second timeout for the whole NIS status exchange, not just the dial, so a stalled apcupsd can no longer hang scrapes and leak connections ([#9](https://github.com/acaylor/apcupsd_exporter/issues/9)).
- CI now runs on pushes to branches containing slashes (e.g. `fix/foo`).
- The binary `.gitignore` rule no longer hides new files under `cmd/apcupsd_exporter/`.

## [0.1.1] - 2026-08-08

### Added

- Renovate configuration for automated dependency updates.

### Changed

- Upgrade `github.com/prometheus/client_golang` to v1.24.1, along with its indirect dependencies.
- Upgrade `actions/setup-go` and `actions/checkout` to v7 in CI.

### Removed

- Unused indirect dependencies `github.com/kr/text` and `go.yaml.in/yaml/v2`.

## [0.1.0] - 2026-02-28

### Changed

- Require Go 1.26; use [github.com/acaylor/apcupsd](https://github.com/acaylor/apcupsd) v0.1.0 instead of `github.com/mdlayher/apcupsd`.
- CI runs only on Go 1.26; upgraded `actions/setup-go` to v5 and `actions/checkout` to v4.

### Fixed

- Replace deprecated `io/ioutil` with `io` in tests (staticcheck SA1019).

[Unreleased]: https://github.com/acaylor/apcupsd_exporter/compare/v0.1.1...HEAD
[0.1.1]: https://github.com/acaylor/apcupsd_exporter/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/acaylor/apcupsd_exporter/compare/28b7412...v0.1.0
