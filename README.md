# README

According to the [State of JS 2025 Front-end Frameworks survey](https://2025.stateofjs.com/en-US/libraries/front-end-frameworks/#front_end_frameworks_ratios), React appears as the most used front-end framework, followed by Vue and Angular.

Noticing the [MDN Navigation API documentation](https://developer.mozilla.org/en-US/docs/Web/API/Navigation_API) earlier this year also created an incentive to re-explore native web platform features, better document what I already know, and more broadly explore new territories beyond the web platform, mostly in .NET.

Note: redaction work is AI-assisted, but performed under strict directions and followed by manual validation checks.

## Table of Contents

- [Installation](#installation)
- [Tooling](#tooling)
- [.NET Framework Modernization ->](DOTNET_FRAMEWORK_MODERNIZATION.md) (same site, separate file)

## Installation

For package installation on Windows, use the [Windows Package Manager (winget)](https://learn.microsoft.com/en-us/windows/package-manager/).

If your everyday account is non-admin and you only use an admin account occasionally, prefer user-scope installs with `--scope user` for day-to-day tooling, and only use machine-scope installs when admin-level installation is required.

Examples:

```powershell
winget install --id Git.Git --scope user
winget install --id Microsoft.VisualStudioCode --scope user
```

To browse and discover available winget packages, use [winstall.app](https://winstall.app/).

### How to know if a package needs admin scope

1. Try user scope first:

```powershell
winget install --id <Package.Id> --scope user --exact
```

2. If the install fails with a user-scope limitation or asks for elevation, install it with machine scope from an admin session.

3. Check package metadata before installing:

```powershell
winget show --id <Package.Id> --exact
```

If only machine scope is supported, admin rights are required.

### Upgrading

Recommended cadence:

- User scope (`--scope user`): weekly
- Machine scope (`--scope machine`): monthly (or when you intentionally switch to an admin session)

Show available upgrades first:

```powershell
winget upgrade --scope user
winget upgrade --scope machine
```

Then apply upgrades:

```powershell
winget upgrade --all --scope user
winget upgrade --all --scope machine
```

When practical, prefer the app's built-in auto-update flow.

- For WSL, consider running `wsl --update`.
- For Visual Studio, use the Visual Studio Installer, which includes auto-update capabilities for installed components and workloads.

## Tooling

- [Visual Studio Code](https://code.visualstudio.com/)
- [Visual Studio](https://visualstudio.microsoft.com/) 2022 and now 2026 are still required for some legacy [.NET Framework](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-framework) codebases.
- [Install WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- [WSL Container public preview announcement](https://devblogs.microsoft.com/commandline/wsl-container-is-now-available-for-public-preview/)

While WSL container support is interesting, my current day-to-day setup uses [Podman for Windows](https://github.com/podman-container-tools/podman/blob/main/docs/tutorials/podman-for-windows.md).