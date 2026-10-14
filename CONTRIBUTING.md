# Contributing

This repository is an independent Gradle project for the BootUI JetBrains companion; it is not part of BootUI's Maven
reactor. Use JDK 21 and the checked-in Gradle wrapper. The first verified IDE baseline is IntelliJ IDEA 2025.3.

From the repository root:

```bash
./gradlew test
./gradlew buildPlugin
./gradlew verifyPluginStructure
./gradlew verifyPlugin
```

Before opening a pull request, run the complete set:

```bash
./gradlew test buildPlugin verifyPluginStructure verifyPlugin
```

`buildPlugin` writes the installable ZIP to `build/distributions/`. `verifyPlugin` runs JetBrains Plugin Verifier against
the configured IDE baseline. `./gradlew runIde` launches a disposable IDE sandbox for manual checks.

Keep changes focused on the standalone plugin. Preserve the existing plugin ID unless a deliberate compatibility
decision is made, keep application requests explicitly user-triggered and loopback-only, and do not add Marketplace
publishing or AI-provider integration without a separate decision. CI and release actions are pinned to full commit
SHAs; keep their permissions minimal and do not add release secrets.
