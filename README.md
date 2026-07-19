# build.publish.jdk

## artifacts.itemis.cloud

[![artifacts.itemis.cloud: jbr](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbr/maven-metadata.xml&label=jbr&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbr)
[![artifacts.itemis.cloud: jbr jcef](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbr_jcef/maven-metadata.xml&label=jbr_jcef&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbr_jcef)
[![artifacts.itemis.cloud: jbrsdk](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbrsdk/maven-metadata.xml&label=jbrsdk&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbrsdk)

## GitHub

[![Github pages](https://img.shields.io/badge/Github-pages-success)](https://github.com/orgs/mbeddr/packages?repo_name=build.publish.mps)

> JetBrains Runtime is a fork of OpenJDK available for Windows, Mac OS X, and Linux. It includes several enhancements in font rendering, HiDPI support, windowing/focus subsystems, performance improvements, and bug fixes.

This repository contains a script for publishing JetBrains Runtime (JBR and JBR SDK) as Maven artifacts to itemis Nexus so that it can be used in our platforms and other project builds:

- **jbr**: the JetBrains Runtime 
- **jbr_jcef** includes “Java Chromium Embedded Framework (JCEF)“. This distribution type is largely used by JetBrains IDEs these days.
- **jbr_nomod**:  “vanilla” JBR aka OpenJDK with JetBrains patches, much smaller because there is no JCEF but e.g. the markdown preview won’t work with this distribution.
- **jbrsdk**: full SDK of the JDK with tools for debugging etc. (You do not need this for your RCP! This is only useful for debugging problems in the JDK itself.)

For more information, visit the [JetBrains runtime](https://github.com/JetBrains/JetBrainsRuntime) repository and [https://github.com/JetBrains/JetBrainsRuntime/issues/40](https://github.com/JetBrains/JetBrainsRuntime/issues/40). Information about JCEF can be found in the [MPS platform docs](http://mbeddr.com/mps-platform-docs/mps_internal/jcef/).

The script for older MPS versions can be found in the mps/**X** branches where **X** is a major MPS version.

For publishing, trigger the parametrized build in CI and specify **either**:

- `jbrVersion` — the full JBR version to publish, e.g. `21.0.6-b895.109` (see the table below); or
- `mpsVersion` — an MPS release (e.g. `2025.1`) or pre-release build number (e.g. `261.25134.10210`). The matching JBR
  version is looked up automatically from the `com.jetbrains.mps:mps-jbr` marker POM (see below). For releases this works
  for MPS 2023.3.1 and later; for earlier MPS versions, pass `jbrVersion` directly.

Set only one of the two. The legacy `jdkVersion` + `jdkBuild` properties are still accepted but deprecated in favor of
`jbrVersion`.

## Looking up the JBR for an MPS version

Since MPS 2023.3.1, [build.publish.mps](https://github.com/mbeddr/build.publish.mps) publishes a marker artifact
`com.jetbrains.mps:mps-jbr` for each MPS release, and
[publish-mps-prereleases](https://github.com/mbeddr/publish-mps-prereleases) publishes the same marker for each MPS
pre-release build. It is a dependency-only POM whose single dependency is the exact `com.jetbrains.jdk:jbr_jcef` version
that MPS is built with (derived from `mps.runtimeBuild` in the distribution's `build.properties`).

Releases (in `maven-mps`) and pre-releases (in `maven-mps-prereleases`) use the same coordinates; this build picks the
repository from the shape of the version. This is the same lookup performed when you publish by `mpsVersion`.

## MPS - JBR table

The table below is a convenience snapshot. Since MPS 2023.3.1 the authoritative mapping is the `mps-jbr` marker artifact
described above.

| MPS Version | JDK Version | JDK Build | Full JBR string    |
|-------------|-------------|-----------|--------------------|
| 2020.2      | 11_0_9      | b944.49   | 11_0_9-b944.49     |
| 2020.3      | 11_0_10     | b1145.96  | 11_0_10-b1145.96   |
| 2021.1      | 11_0_11     | b1341.60  | 11_0_11-b1341.60   |
| 2021.2      | 11_0_12     | b1504.28  | 11.0.12-b1504.28   |
| 2021.3      | 11_0_14_1   | b1751.46  | 11.0.14.1-b1751.46 |
| 2022.2      | 17.0.6      | b469.82   | 17.0.6-b469.82     |
| 2022.3      | 17.0.6      | b653.34   | 17.0.6-b653.34     |
| 2023.2      | 17.0.12     | b1000.54  | 17.0.12-b1000.54   |
| 2023.3      | 17.0.12     | b1087.25  | 17.0.12-b1087.25   |
| 2023.3.1    | 17.0.9      | b1087.9   | 17.0.9-b1087.9     |
| 2024.1      | 17.0.11     | b1207.30  | 17.0.11-b1207.30   |
| 2024.3      | 21.0.5      | b631.16   | 21.0.5-b631.16     |
| 2025.1      | 21.0.6      | b895.109  | 21.0.6-b895.109    |
| 2025.2.1    | 21.0.8      | b1038.71  | 21.0.8-b1038.71    |
| 2025.3      | 21.0.8      | b1163.69  | 21.0.8-b1163.69    |
| 2026.1      | 25.0.3      | b329.124  | 25.0.3-b329.124    |
