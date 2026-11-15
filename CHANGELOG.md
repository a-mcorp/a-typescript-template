# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

<!--
Template
## [{project-version}] - {YYYY-MM-DD}

### Added
### Changed
### Deprecated
### Removed
### Fixed
### Security
-->

## [Unreleased] - 2026-11-15

### Added
- Project setup
  - Converted from 'a-python-template' to TypeScript on the Deno runtime.
  - Windows (PowerShell) and Linux installation steps for a project-local `denoenv-{deno-version}` environment (Deno binary, `DENO_DIR` cache, `lefthook` and `appimagetool`) in place of a `venv`, without install scripts.
  - `deno.jsonc` with placeholder project metadata, tasks (`start`, `test`, `check`, `compile`, `compile-appimage`) and an empty import map.
  - Deno and TypeScript `.gitignore`, covering Node.js compatibility, coverage, bundlers, web frameworks, hosting platforms and AppImage outputs.
  - `LICENSE` (GPL-3.0).
- Code quality (local CI)
  - `lefthook.yml` with a `check` bundle of `deno fmt`, `deno lint` and `deno check`, run manually with `lefthook run check` and without git hooks.
  - Strict TypeScript compiler options, lint rules (including `camelcase` and explicit return types) and formatter settings in `deno.jsonc`.
- Packaging (local CD)
  - AppImage recipe in `AppImage/Recipe` laid out as an `appimagetool` AppDir: `AppRun`, desktop entry with `X-AppImage-Version`, AppStream metadata in `usr/share/metainfo` and icon.
  - `AppImage/README.md` build guide based on `deno compile` and `appimagetool`, with Windows (PowerShell) and Linux steps.
- Documentation
  - `README.md` with Metadata, Features, Setup (Dependencies, Installation, Usage, Repository structure), Example and a commented-out Troubleshooting section.
  - `CHANGELOG.md` and its template `.github/CHANGELOG_TEMPLATE/CHANGELOG.md`, based on Keep a Changelog.
  - `TO-DO.md`.
- GitHub repository templates
  - Default pull request template `.github/pull_request_template.md` and `.github/PULL_REQUEST_TEMPLATE/Default.md`.
  - `.github/CODEOWNERS`, its template `.github/CODEOWNERS_TEMPLATE/CODEOWNERS` and the GitHub sample `.github/CODEOWNERS_TEMPLATE/CODEOWNERS_SCHEMA`.
- Template conventions
  - Standardised kebab-case placeholder names (`{project-*}`, `{author-*}`, `{dependency-N-*}`, `{deno-*}`, `{issue-*}`) across all template files.
  - Compatibility with 'a-skills'.
