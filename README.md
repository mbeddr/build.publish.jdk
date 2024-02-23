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

To change the JBR version for publishing, edit `gradle.properties` file.
