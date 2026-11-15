<sup>This project has been generated using ['A-TypeScript-Template' (ATT)](https://github.com/a-matthew/a-typescript-template).</sup>

# {project-name}

## Metadata
<!-- - Author: {author-name}/{author-alias}. -->
- Name: '{project-name}'.
- Purpose: {project-summary}.
- Format: {project-format}.
- License:
  - This project's license: [GNU General Public License v3.0](LICENSE)
  <!-- - Dependency-1: [{dependency-1-name}]({dependency-1-license}) -->
  <!-- - Dependency-2: [{dependency-2-name}]({dependency-2-license}) -->

## Features
- {feature-1}
- {feature-2}

## Setup
### Dependencies
  - Language: [__TypeScript__](https://www.typescriptlang.org/) (strict)
  - Runtime: [__Deno__](https://github.com/denoland/deno) __{deno-version}__
  - Manager: [__deno__](https://docs.deno.com/runtime/fundamentals/modules/) (built-in, [JSR](https://jsr.io/) and `npm:` packages)
  - Toolset:
    - [deno.jsonc](https://docs.deno.com/runtime/fundamentals/configuration/)
    - [lefthook](https://github.com/evilmartians/lefthook) (local CI bundle, no git hooks)
      - [deno fmt](https://docs.deno.com/runtime/reference/cli/fmt/)
      - [deno lint](https://docs.deno.com/runtime/reference/cli/lint/)
      - [deno check](https://docs.deno.com/runtime/reference/cli/check/)

### Installation
{...}
<!-- Deno environment (the binary, cache and tools stay inside `denoenv-{deno-version}`) -->
  <!-- - Windows (PowerShell)
    - `cd {path}\{project-name}`
    - `Invoke-WebRequest -OutFile deno.zip https://github.com/denoland/deno/releases/download/v{deno-version}/deno-x86_64-pc-windows-msvc.zip`
    - `(Get-FileHash deno.zip).Hash` and compare it with the `deno-x86_64-pc-windows-msvc.zip.sha256sum` file on the [release](https://github.com/denoland/deno/releases) page
    - `Expand-Archive deno.zip -DestinationPath denoenv-{deno-version}\bin; Remove-Item deno.zip` <sub>suggested</sub>
    - `Invoke-WebRequest -OutFile denoenv-{deno-version}\bin\lefthook.exe https://github.com/evilmartians/lefthook/releases/download/v{lefthook-version}/lefthook_{lefthook-version}_Windows_x86_64.exe`
    - `(Get-FileHash denoenv-{deno-version}\bin\lefthook.exe).Hash` and compare it with `lefthook_checksums.txt` on the [release](https://github.com/evilmartians/lefthook/releases) page
    - activate (per shell session):
      - `$env:Path = "$PWD\denoenv-{deno-version}\bin;$env:Path"`
      - `$env:DENO_DIR = "$PWD\denoenv-{deno-version}\cache"`
      - `$env:DENO_INSTALL_ROOT = "$PWD\denoenv-{deno-version}"`
    - everything below
  - Linux
    - `cd {path}/{project-name}`
    - `curl -fLo deno.zip https://github.com/denoland/deno/releases/download/v{deno-version}/deno-x86_64-unknown-linux-gnu.zip`
    - `sha256sum deno.zip` and compare it with the `deno-x86_64-unknown-linux-gnu.zip.sha256sum` file on the [release](https://github.com/denoland/deno/releases) page
    - `unzip deno.zip -d denoenv-{deno-version}/bin && rm deno.zip` <sub>suggested</sub>
    - `curl -fLo denoenv-{deno-version}/bin/lefthook https://github.com/evilmartians/lefthook/releases/download/v{lefthook-version}/lefthook_{lefthook-version}_Linux_x86_64`
    - `sha256sum denoenv-{deno-version}/bin/lefthook` and compare it with `lefthook_checksums.txt` on the [release](https://github.com/evilmartians/lefthook/releases) page
    - `chmod +x denoenv-{deno-version}/bin/lefthook`
    - activate (per shell session):
      - `export PATH="$PWD/denoenv-{deno-version}/bin:$PATH"`
      - `export DENO_DIR="$PWD/denoenv-{deno-version}/cache"`
      - `export DENO_INSTALL_ROOT="$PWD/denoenv-{deno-version}"`
    - everything below
  1. `deno install` (installs the dependencies from `deno.jsonc` and `deno.lock` into `DENO_DIR`)
  2. double check with `which deno` (Linux) or `Get-Command deno` (Windows), and `deno info` (shows the `DENO_DIR` location) -->

### Usage
  - project
    - {...}
    <!-- - `deno task start` -->
  - local tests
    - {...}
    <!-- - `deno task test` -->
  - local CI
    <!-- - `lefthook run check` -->
    <!-- - - Files must be first added by `git add` for `lefthook run` to detect. -->
    <!-- - - The commands use the `deno` from the activated `denoenv-{deno-version}`. -->
    <!-- - - Do not run `lefthook install`, as it would install git hooks. -->
    <!-- - `deno task check` (the code checks, without lefthook) -->
  - local CD
    - AppImage deployment
      - See [AppImage/README.md](AppImage/README.md)

#### Repository structure
```
.
├── .github
│   ├── CHANGELOG_TEMPLATE         # Template for CHANGELOG.md
│   ├── CODEOWNERS_TEMPLATE        # Template for CODEOWNERS
│   ├── PULL_REQUEST_TEMPLATE      # Additional pull request templates
│   ├── CODEOWNERS                 # Code owners
│   └── pull_request_template.md   # Default pull request template
├── AppImage                       # AppImage recipe (AppDir) and build guide
├── docs                           # Documentation assets
├── src                            # Project source code
├── CHANGELOG.md                   # Project changelog
├── deno.jsonc                     # Project metadata and tool configuration
├── deno.lock                      # Pinned dependency versions
├── lefthook.yml                   # Formatters and linters bundle (local CI)
├── LICENSE                        # Project license
└── README.md                      # Project documentation
```

## Example
### {example-1-title}
{...}

<!-- 
## Troubleshooting
-->
