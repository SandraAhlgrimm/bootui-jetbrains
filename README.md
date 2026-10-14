# BootUI JetBrains companion

An experimental Kotlin plugin that brings a running [BootUI](https://github.com/jdubois/boot-ui) application's
overview and panel availability into an IntelliJ tool window. It can also add a BootUI dependency to a Maven or Gradle
build file and run an existing IDE configuration.

The plugin is independent of BootUI's Maven reactor and releases. It is **not published on JetBrains Marketplace**.
Compatibility has been verified against IntelliJ IDEA 2025.3 (build 253); other IDE versions and JetBrains products
have not been verified.

## Install

Download the ZIP from the project's [GitHub Releases](https://github.com/SandraAhlgrimm/bootui-jetbrains/releases).
In IntelliJ, open **Settings > Plugins**, select **Install Plugin from Disk...** from the gear menu, choose the ZIP,
and restart if requested. Then open **View > Tool Windows > BootUI**.

## Features and safeguards

- Explicit **Connect** and **Refresh** actions read only the local application's overview and panel availability.
- **Open Console** opens the configured local BootUI UI when clicked.
- **Add BootUI dependency** previews the exact Maven/Gradle build-file edit and applies it only after confirmation.
  The edit is undoable and does not reload or build the project.
- **Run application** uses the run configuration selected in IntelliJ; it does not create or change configurations.
- **Copy AI context** copies a bounded, filtered JSON overview to the clipboard. It does not contact an AI provider.

The plugin does not start scans or runtime mutations, embed the browser console, or implement an AI chat or provider.
Network requests are limited to loopback hosts, require an explicit user action, bypass proxies, do not follow redirects,
and have bounded time and response size. Optional bearer tokens are stored in IntelliJ Password Safe.

See the [user guide](docs/JETBRAINS.md) for setup, dependency-editing limits, troubleshooting, and safety details.

## Build and test

Requires JDK 21 and network access to resolve Gradle and IntelliJ Platform dependencies. From the repository root:

```bash
./gradlew test
./gradlew buildPlugin
./gradlew verifyPluginStructure
./gradlew verifyPlugin
```

The wrapper pins Gradle 9.3.0. Kotlin Gradle Plugin 2.3.20 and IntelliJ Platform Gradle Plugin 2.19.0 are pinned in
`build.gradle.kts`. `buildPlugin` creates an installable ZIP in `build/distributions/`; `verifyPlugin` checks the
configured IntelliJ IDEA 2025.3 compatibility baseline. For contributor setup and CI details, see
[CONTRIBUTING.md](CONTRIBUTING.md).

## Provenance and license

This standalone project extracts the JetBrains plugin from the public
[BootUI repository](https://github.com/jdubois/boot-ui), source commit
[`13202560ce509ee395b96089de56c49efe707280`](https://github.com/jdubois/boot-ui/commit/13202560ce509ee395b96089de56c49efe707280).
The original integration proposal is [jdubois/boot-ui#1414](https://github.com/jdubois/boot-ui/pull/1414).
Plugin ID and Kotlin package names are retained from that source. This extraction is maintained independently and
does not imply that it is an official BootUI or JetBrains distribution.

Licensed under the [Apache License, Version 2.0](LICENSE). See [NOTICE](NOTICE) for attribution.
