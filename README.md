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
Deno environment (the binary, cache and tools stay inside `denoenv-{deno-version}`):
  - Windows (PowerShell)
    - set the versions (per shell session)
      ```powershell
      cd {path}\{project-name}; $denoVersion = "{deno-version}"; $lefthookVersion = "{lefthook-version}"
      ```
    - download, validate and unpack Deno
      ```powershell
      Invoke-WebRequest -OutFile deno.zip "https://github.com/denoland/deno/releases/download/v$denoVersion/deno-x86_64-pc-windows-msvc.zip"
      Invoke-WebRequest -OutFile deno.zip.sha256sum "https://github.com/denoland/deno/releases/download/v$denoVersion/deno-x86_64-pc-windows-msvc.zip.sha256sum"
      $expected = [regex]::Match((Get-Content -Raw deno.zip.sha256sum), '[0-9A-Fa-f]{64}').Value
      if ((Get-FileHash deno.zip).Hash -eq $expected) { Expand-Archive deno.zip -DestinationPath "denoenv-$denoVersion\bin" } else { Write-Error "Checksum mismatch: deno.zip" }
      Remove-Item deno.zip, deno.zip.sha256sum
      ```
    - download and validate lefthook
      ```powershell
      Invoke-WebRequest -OutFile "denoenv-$denoVersion\bin\lefthook.exe" "https://github.com/evilmartians/lefthook/releases/download/v$lefthookVersion/lefthook_${lefthookVersion}_Windows_x86_64.exe"
      Invoke-WebRequest -OutFile lefthook_checksums.txt "https://github.com/evilmartians/lefthook/releases/download/v$lefthookVersion/lefthook_checksums.txt"
      $expected = (Get-Content lefthook_checksums.txt | Where-Object { $_ -like "* lefthook_${lefthookVersion}_Windows_x86_64.exe" }) -replace ' .*'
      if ((Get-FileHash "denoenv-$denoVersion\bin\lefthook.exe").Hash -ne $expected) { Remove-Item "denoenv-$denoVersion\bin\lefthook.exe"; Write-Error "Checksum mismatch: lefthook.exe" }
      Remove-Item lefthook_checksums.txt
      ```
    - activate (per shell session)
      ```powershell
      $env:Path = "$PWD\denoenv-$denoVersion\bin;$env:Path"; $env:DENO_DIR = "$PWD\denoenv-$denoVersion\cache"; $env:DENO_INSTALL_ROOT = "$PWD\denoenv-$denoVersion"
      ```
    - everything below
  - Linux
    - set the versions (per shell session)
      ```bash
      cd {path}/{project-name} && deno_version="{deno-version}" && lefthook_version="{lefthook-version}"
      ```
    - download, validate and unpack Deno
      ```bash
      mkdir -p "denoenv-$deno_version/bin" && curl -fLo deno.zip "https://github.com/denoland/deno/releases/download/v$deno_version/deno-x86_64-unknown-linux-gnu.zip" && echo "$(curl -fsL "https://github.com/denoland/deno/releases/download/v$deno_version/deno-x86_64-unknown-linux-gnu.zip.sha256sum" | grep -oiE '[0-9a-f]{64}' | tr A-F a-f)  deno.zip" | sha256sum -c - && unzip deno.zip -d "denoenv-$deno_version/bin" && rm deno.zip
      ```
    - download and validate lefthook
      ```bash
      curl -fLo "denoenv-$deno_version/bin/lefthook" "https://github.com/evilmartians/lefthook/releases/download/v$lefthook_version/lefthook_${lefthook_version}_Linux_x86_64" && echo "$(curl -fsL "https://github.com/evilmartians/lefthook/releases/download/v$lefthook_version/lefthook_checksums.txt" | grep " lefthook_${lefthook_version}_Linux_x86_64\$" | cut -d' ' -f1)  denoenv-$deno_version/bin/lefthook" | sha256sum -c - && chmod +x "denoenv-$deno_version/bin/lefthook"
      ```
    - activate (per shell session)
      ```bash
      export PATH="$PWD/denoenv-$deno_version/bin:$PATH" DENO_DIR="$PWD/denoenv-$deno_version/cache" DENO_INSTALL_ROOT="$PWD/denoenv-$deno_version"
      ```
    - everything below
  1. `deno install` (installs the dependencies from `deno.jsonc` and `deno.lock` into `DENO_DIR`)
  2. double check with `which deno` (Linux) or `Get-Command deno` (Windows), and `deno info` (shows the `DENO_DIR` location)

### Usage
  - project
    - `deno task start`
  - local tests
    - `deno task test`
  - local CI
    - `lefthook run check`
      - Files must be first added by `git add` for `lefthook run` to detect.
      - The commands use the `deno` from the activated `denoenv-{deno-version}`.
      - Do not run `lefthook install`, as it would install git hooks.
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
