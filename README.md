# BootUI JetBrains

An independent Kotlin companion for the BootUI developer console. It adds a native IntelliJ tool window for explicitly
connecting to a local BootUI-enabled application, reviewing its overview and panel availability, adding a BootUI
dependency to supported Maven or Gradle build files, and running an existing IDE configuration.

This is an experimental, independently versioned plugin. It is not published on JetBrains Marketplace and does not
replace BootUI's browser console or the BootUI dependency in your application. Compatibility is verified against
IntelliJ IDEA 2025.3 (build 253); other IDE versions and JetBrains products are not verified.

## Build and install

Requirements: JDK 21 and network access to download Gradle and IntelliJ dependencies.

```bash
./gradlew test buildPlugin verifyPluginStructure verifyPlugin
```

Install `build/distributions/bootui-jetbrains-0.1.0.zip` using **Settings > Plugins > Install Plugin from Disk...**,
then open **View > Tool Windows > BootUI**. The plugin version is independent of BootUI's application/library
versions. There is no Marketplace release at this time.

See the [JetBrains companion guide](docs/JETBRAINS.md) for connection setup, supported dependency edits, safety limits,
and troubleshooting. Contributors can use [CONTRIBUTING.md](CONTRIBUTING.md).

## License and provenance

Distributed under the [Apache License 2.0](LICENSE). This standalone repository extracts the JetBrains companion
originally developed in [jdubois/boot-ui](https://github.com/jdubois/boot-ui), from source commit
[`13202560ce509ee395b96089de56c49efe707280`](https://github.com/jdubois/boot-ui/commit/13202560ce509ee395b96089de56c49efe707280)
and its [original pull request](https://github.com/jdubois/boot-ui/pull/1414). The existing plugin ID is preserved;
this repository does not claim to be an official JetBrains Marketplace publisher.
