# Repository guidance

- Use JDK 21 and the checked-in Gradle wrapper; run `./gradlew test buildPlugin verifyPluginStructure verifyPlugin`
  before proposing changes that affect the plugin.
- Preserve the existing plugin ID and keep network requests user-triggered and restricted to loopback.
- Keep the standalone repository's CI and tagged GitHub ZIP release separate from BootUI's Maven release and JetBrains
  Marketplace publishing.
