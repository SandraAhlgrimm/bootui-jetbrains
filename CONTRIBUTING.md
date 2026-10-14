# Contributing

Contributions to the standalone JetBrains companion are welcome. Keep changes focused on this plugin; it is an
independently built project and does not inherit BootUI's Maven reactor or contributor conventions.

## Requirements

- JDK 21
- Network access for Gradle and IntelliJ Platform dependency resolution

The checked-in Gradle Wrapper pins Gradle 9.3.0. The Kotlin and IntelliJ Platform Gradle plugins are pinned in
`build.gradle.kts`.

## Local checks

Run from the repository root:

```bash
./gradlew test
./gradlew buildPlugin
./gradlew verifyPluginStructure
./gradlew verifyPlugin
```

`test` runs the Kotlin and IntelliJ platform tests. `buildPlugin` creates the installable ZIP in
`build/distributions/`. `verifyPluginStructure` checks the package structure, and `verifyPlugin` runs JetBrains Plugin
Verifier against the configured IntelliJ IDEA 2025.3 baseline. `./gradlew runIde` starts a disposable IDE sandbox.

GitHub Actions runs these same checks for pushes to `main` and pull requests. CI uploads the generated plugin ZIP as a
workflow artifact. A separate manually dispatched workflow publishes a GitHub Release only for an existing `vX.Y.Z`
tag whose version matches the Gradle project version and whose commit is reachable from `main`. Releases are not
published to JetBrains Marketplace.

## Scope and safety

Preserve the current plugin ID (`io.github.jdubois.bootui.jetbrains`) and Kotlin package names unless a separately
reviewed compatibility change is intended. Network access must remain explicit, loopback-only, bounded, and safely
redacted. Build-file edits must retain their preview-before-apply and undo behavior. AI-provider integrations,
Marketplace publishing, and unrelated BootUI server changes are outside the current standalone bootstrap.
