# build.publish.jdk

Contains script for publishing JetBrains Runtime (JBR and JBR SDK) as Maven artifacts to itemis Nexus, so it can be used in platform and customer projects builds.

To download these artifacts to your project, use the following dependencies:

| groupId             | artifactId        | version               |
|:--------------------|:------------------|:----------------------|
| `com.jetbrains.jdk` | `jbr` or `jbrsdk` | e.g. `11_0_4-b304.78` |

To change JBR version for publishing, edit `gradle.properties` file.
