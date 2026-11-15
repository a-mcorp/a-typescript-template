<sup>This project has been generated using ['A-JavaScript-Template' (AJT)](https://github.com/a-matthew/a-javascript-template).</sup>

## Metadata
Lots of information regarding the AppImage building process and specifications can be found under the AppImage project's [GitHub Wiki](https://github.com/AppImage/AppImageKit/wiki).
- for AppImage recipes refer to: [Wiki/AppImages](https://github.com/AppImage/AppImageKit/wiki/AppImages) (not maintained)

A detailed comparison of `AppImage types` is available at the official [AppImageSpec](https://github.com/AppImage/AppImageSpec/blob/master/draft.md#appdir) repository.
- for `type1` (?) refer to: [AppImageKit](https://github.com/AppImage/AppImageKit)
- for `type2` refer to: [AppImageTool](https://github.com/AppImage/appimagetool)

## Setup
### Dependencies
  - AppImage version: __type2__ <!--Type1--> <!--Type2-->
  - AppImage tool: [__appimagetool__](https://github.com/AppImage/appimagetool)
  - Binary builder: [__deno compile__](https://docs.deno.com/runtime/reference/cli/compile/)

> 🚧
> `deno compile` bundles the Deno runtime and the project into one self-contained binary, so the AppImage needs no runtime and no dependencies.

> 🚧
> `"Fuse is not supported on Windows Subsystem for Linux v1 (WSL1)"`, which prevents the direct execution of AppImages. The contents can still be extracted with `--appimage-extract`.

### AppDir
The AppDir directory description can be found at the AppImage project's [documentation](https://docs.appimage.org/reference/appdir.html).

The `AppImage/Recipe` directory is the AppDir itself, as expected by `appimagetool`:
- AppRun
  - it defines the main executable to run within the AppImage
- usr/bin/{project-acronym}
  - the compiled binary, created by `deno task compile-appimage` (ignored by `git`)
- usr/share/metainfo/{project-acronym}.appdata.xml (static file, not compiled)
  - this file can be generated with the [AppStream generator](https://docs.appimage.org/packaging-guide/optional/appstream.html) from AppImage's official documentation. <br>It defines the basic metadata.
- {project-acronym}.desktop
  - AppImage integration details and keywords can be found in the official FreeDesktop project's [specification](https://specifications.freedesktop.org/desktop-entry/latest/recognized-keys.html)
- {project-acronym}.svg

#### AppImage Artifact
The final package can be extracted for debugging purposes using the `./{project-acronym}-x86_64.AppImage --appimage-extract` command in the CLI.

The artifact's internal directory structure should resemble the following:
- AppRun
  - the entrypoint
- usr/bin
  - the compiled binary
- other files
  - assets and other files

### Installation
<!-- Deno environment -->
Create and activate the project's Deno environment (`denoenv-{deno-version}`), as described in [README.md](../README.md#installation). `appimagetool` is downloaded into the same environment.

> 🚧
> `appimagetool` runs on Linux only. On Windows, the same commands run inside [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install) by prefixing them with `wsl`, which starts in the current project directory.

  - Windows (PowerShell)
    1. `cd {path}\{project-name}`
    2. `deno install`
    3. Update files in the `AppImage/Recipe` directory
    4. `deno task compile-appimage` (cross-compiles the Linux binary)
    5. `wsl curl -fL --create-dirs -o denoenv-{deno-version}/bin/appimagetool https://github.com/AppImage/appimagetool/releases/download/{appimagetool-version}/appimagetool-x86_64.AppImage`
    6. `wsl chmod +x denoenv-{deno-version}/bin/appimagetool`
    7. `wsl env ARCH=x86_64 APPIMAGE_EXTRACT_AND_RUN=1 denoenv-{deno-version}/bin/appimagetool AppImage/Recipe {project-acronym}-x86_64.AppImage` <sub>`APPIMAGE_EXTRACT_AND_RUN` avoids the need for FUSE in WSL2</sub>
  - Linux
    1. `cd {path}/{project-name}`
    2. `deno install`
    3. Update files in the `AppImage/Recipe` directory
    4. `deno task compile-appimage`
    5. `curl -fL --create-dirs -o denoenv-{deno-version}/bin/appimagetool https://github.com/AppImage/appimagetool/releases/download/{appimagetool-version}/appimagetool-x86_64.AppImage`
    6. `chmod +x denoenv-{deno-version}/bin/appimagetool`
    7. `ARCH=x86_64 appimagetool AppImage/Recipe {project-acronym}-x86_64.AppImage`

The `{appimagetool-version}` values are listed on the [releases](https://github.com/AppImage/appimagetool/releases) page. It is important that all dependencies of the app are within one folder. Best practices are covered by the AppImage project's [documentation](https://docs.appimage.org/reference/best-practices.html).

## Example
### CD Build
{...}
