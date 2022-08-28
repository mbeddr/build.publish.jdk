# build.publish.jdk

## artifacts.itemis.cloud

[![artifacts.itemis.cloud: jbr](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbr/maven-metadata.xml&label=jbr&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbr)
[![artifacts.itemis.cloud: jbr jcef](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbr_jcef/maven-metadata.xml&label=jbr_jcef&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbr_jcef)
[![artifacts.itemis.cloud: jbr nomod](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbr_nomod/maven-metadata.xml&label=jbr_nomod&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbr_nomod)
[![artifacts.itemis.cloud: jbrsdk](https://img.shields.io/badge/dynamic/xml?url=https://artifacts.itemis.cloud/repository/maven-mps/com/jetbrains/jdk/jbrsdk/maven-metadata.xml&label=jbrsdk&color=success&query=.//versioning/latest)](https://artifacts.itemis.cloud/#browse/browse:maven-mps:com%2Fjetbrains%2Fjdk%2Fjbrsdk)

## Github

[![Github pages](https://img.shields.io/badge/Github-pages-success)](https://github.com/orgs/mbeddr/packages?repo_name=build.publish.mps)

## projects.itemis.de (deprecated)

[![projects.itemis.de: jbr](https://img.shields.io/badge/dynamic/xml?url=https://projects.itemis.de/nexus/content/repositories/mbeddr/com/jetbrains/jdk/jbr/maven-metadata.xml&label=jbr&color=inactive&query=.//versioning/latest)](https://projects.itemis.de/nexus/#nexus-search;gav~com.jetbrains.jdk~jbr~~~)
[![projects.itemis.de: jbr jcef](https://img.shields.io/badge/dynamic/xml?url=https://projects.itemis.de/nexus/content/repositories/mbeddr/com/jetbrains/jdk/jbr_jcef/maven-metadata.xml&label=jbr_jcef&color=inactive&query=.//versioning/latest)](https://projects.itemis.de/nexus/#nexus-search;gav~com.jetbrains.jdk~jbr_jcef~~~)
[![projects.itemis.de: jbr nomod](https://img.shields.io/badge/dynamic/xml?url=https://projects.itemis.de/nexus/content/repositories/mbeddr/com/jetbrains/jdk/jbr_nomod/maven-metadata.xml&label=jbr_nomod&color=inactive&query=.//versioning/latest)](hhttps://projects.itemis.de/nexus/#nexus-search;gav~com.jetbrains.jdk~jbr_nomod~~~)
[![projects.itemis.de: jbrsdk](https://img.shields.io/badge/dynamic/xml?url=https://projects.itemis.de/nexus/content/repositories/mbeddr/com/jetbrains/jdk/jbrsdk/maven-metadata.xml&label=jbrsdk&color=inactive&query=.//versioning/latest)](https://projects.itemis.de/nexus/#nexus-search;gav~com.jetbrains.jdk~jbrsdk~~~)

> JetBrains Runtime is a fork of OpenJDK available for Windows, Mac OS X, and Linux. It includes a number of enhancements in font rendering, HiDPI support, windowing/focus subsystems, performance improvements and bugfixes.

This repository contains a script for publishing JetBrains Runtime (JBR and JBR SDK) as Maven artifacts to itemis Nexus, so it can be used in our platforms and other projects builds:

- **jbr**: the JetBrains Runtime 
- **jbr_jcef** includes “Java Chromium Embedded Framework (JCEF)“. This distribution type is largely used by JetBrains IDEs these days.
- **jbr_nomod**:  “vanilla” JBR aka openJDK with JetBrains patches, much smaller because no JCEF but e.g. the markdown preview won’t work with this distribution.
- **jbrsdk**: full SDK of the JDK with tools for debugging etc. (You do not need this for your RCP! This is only useful for debugging problems in the JDK itself.)

For more information, visit the [JetBrains runtime](https://github.com/JetBrains/JetBrainsRuntime) repository and [https://github.com/JetBrains/JetBrainsRuntime/issues/40](https://github.com/JetBrains/JetBrainsRuntime/issues/40). Information about JCEF can be found in the [MPS platform docs](http://mbeddr.com/mps-platform-docs/mps_internal/jcef/).

The script for older MPS versions can be found in the mps/**X** branches where **X** is a major MPS version.

To change JBR version for publishing, edit `gradle.properties` file.
