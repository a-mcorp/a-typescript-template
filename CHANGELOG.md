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

## [1.1.0] - 2026-11-21

### Added
- `docs/.gitkeep`, so the `docs/` folder for the README's screenshots exists in every copy of the template.

### Changed
- Licence changed from GPL-3.0-or-later to MIT No Attribution (MIT-0), so projects created from the template choose their own licence; `README.md`, `deno.jsonc` and the AppImage `appdata.xml` follow it, with the AppStream `metadata_license` set to CC0-1.0, since AppStream requires a permissive licence for metadata.
- `README.md` layout
  - Features and two example screenshots combined in one table: the features span the full width, with the screenshots side by side below (`{example-N-title}` and `{example-N-image}` placeholders, images in `docs/`).
  - Dependencies and Usage placed side by side in a two-column table, keeping their list formatting; the separate Example section was removed, and Repository structure became a level 3 heading.
- Links to the repositories point to the 'a-mcorp' organisation on GitHub.
- `README.md` repository structure: `src` and `deno.lock` are marked as created with the project.
- Comments no longer carry the "Auto-generated:" prefix, as they have been reviewed.
- `.github/pull_request_template.md` and `PULL_REQUEST_TEMPLATE/Default.md`: a checkbox in the Comments section marks when an assistant helped to write the changes.

## [1.0.0] - 2026-11-15

### Added
- Project setup
  - Windows (PowerShell) and Linux installation steps for a project-local `denoenv-{deno-version}` environment (Deno binary, `DENO_DIR` cache, `lefthook` and `appimagetool`), without install scripts.
  - Copy-paste installation commands (Bash one-liners, PowerShell blocks) with `deno` and `lefthook` version variables and automatic SHA-256 validation against the release checksums.
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
