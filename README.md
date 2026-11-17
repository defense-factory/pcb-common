# pcb-common

PCB shared dependency BOM — consumers import it; fix CVEs here first, bump
version, tag `v<version>`, then bump consumers.

## Install

Use Java 17 and Maven:

```bash
mvn -B install
```

## Import in consumers

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>com.defensefactory</groupId>
            <artifactId>pcb-common</artifactId>
            <version>1.1.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

Declare `jackson-databind` and `snakeyaml` dependencies without versions.
Install the BOM locally before building a consumer; it is not published to Maven Central.

⚠️ This repo contains deliberately vulnerable dependencies for demo purposes —
do not deploy. Seeded findings include CVE-2022-42003 and CVE-2022-42004
(Jackson databind), and CVE-2022-1471 (SnakeYAML).
