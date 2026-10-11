# README

According to the [State of JS 2025 Front-end Frameworks survey](https://2025.stateofjs.com/en-US/libraries/front-end-frameworks/#front_end_frameworks_ratios), React appears as the most used front-end framework, followed by Vue and Angular.

Noticing the [MDN Navigation API documentation](https://developer.mozilla.org/en-US/docs/Web/API/Navigation_API) earlier this year also created an incentive to re-explore native web platform features, better document what I already know, and more broadly explore new territories beyond the web platform, mostly in .NET.

Note: redaction work is AI-assisted, but performed under strict directions and followed by manual validation checks.

## Table of Contents

- [Installation](#installation)
- [Tooling](#tooling)
- [Web Platform APIs](#web-platform-apis)
- [Git Conventions](#git-conventions)
- [Data Metadata and Lineage](#data-metadata-and-lineage)
- [Open Cybersecurity Schema Framework](#open-cybersecurity-schema-framework)
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

## Web Platform APIs

The [MDN Web APIs index](https://developer.mozilla.org/en-US/docs/Web/API) is a useful entry point for browser capabilities covering areas such as the DOM, networking, storage, workers, media, graphics, and device integration.

Among them, the [Navigation API](https://developer.mozilla.org/en-US/docs/Web/API/Navigation_API) provides a centralized way to initiate, observe, and intercept navigation. It is particularly useful for same-document navigation in single-page applications and addresses limitations of combining the History API with separate link, form, and `popstate` handling. Check compatibility for target browsers and individual API features before adoption.

Other APIs worth investigating (to be continued):

- [View Transition API](https://developer.mozilla.org/en-US/docs/Web/API/View_Transition_API) for animated transitions between DOM states in single-page applications and between documents in multi-page applications.
- [WebGPU API](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API) for modern GPU-accelerated graphics and general-purpose computation.
- [`<dialog>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog) for native modal and non-modal dialogs, including focus management, Escape-to-close behavior, and form submission with `method="dialog"`.
- [Popover API](https://developer.mozilla.org/en-US/docs/Web/API/Popover_API) and the [`popover` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/popover) for lightweight, top-layer UI such as menus, tooltips, and command palettes. Use `popovertarget` and `popovertargetaction` on buttons for declarative show, hide, and toggle triggers.

## Git Conventions

- [Conventional Branch](https://conventionalbranch.org/) defines readable, purpose-driven branch names using the `<type>/<description>` structure, such as `feature/add-login` or `fix/header-layout`.
- [Conventional Commits](https://www.conventionalcommits.org/en/) defines structured commit messages such as `feat(api): add search endpoint`. The format communicates features, fixes, and breaking changes and can support automated changelogs and semantic versioning.
- As noted by the author of [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/), Gitflow was intended for explicitly versioned software, scheduled release cycles, or products that must support multiple versions in the wild; teams delivering frequently through continuous delivery may be better served by a simpler workflow.

## Data Metadata and Lineage

- [Apache Ossie (incubating)](https://ossie.apache.org/), formerly Open Semantic Interchange (OSI), defines a vendor-neutral specification for exchanging semantic metadata across analytics, AI, and business intelligence platforms.
- [OpenMetadata](https://open-metadata.org/) builds a metadata knowledge graph that connects data assets, documentation, organizational policies, and other context for discovery, governance, and use by people and AI agents.
- [OpenLineage](https://openlineage.io/) provides an open standard, API, libraries, and integrations for collecting lineage events about datasets, jobs, and runs. This helps trace failures and assess the downstream impact of changes.

## Open Cybersecurity Schema Framework

[OCSF](https://ocsf.io/) is an open-source, vendor-neutral framework for normalizing security data. Its common taxonomy, attribute dictionary, and data types help producers and consumers map different security event formats to a shared schema for ingestion, threat detection, and investigation.

The framework is independent of storage, collection, and ETL technologies. Its definitions and normative schema use JSON; the interactive [OCSF Schema Browser](https://schema.ocsf.io/) documents event classes, objects, attributes, profiles, and extensions.
