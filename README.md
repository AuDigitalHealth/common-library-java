# Common Library

Maven artifact **`au.gov.nehta:common-library`** - shared Java utility classes for CDA package operations, argument validation, and web-service helpers used by other ADHA/NEHTA libraries.

## Dependency

Published releases are consumed from **[Maven Central](https://central.sonatype.com/)**. Use a **`<version>`** that matches your JDK (see **Versioning**).

```xml
<dependency>
  <groupId>au.gov.nehta</groupId>
  <artifactId>common-library</artifactId>
  <version>8.0.0</version>
</dependency>
```

**This line (`8.0.0`):** Java **8**, **`javax.xml.ws`** / **`javax.xml.bind`** via **`jaxws-rt` 2.3.7**.

---

## Versioning

The **first number** of the Maven version is the **Java SE** version that this library targets.

| Maven version | Java SE | XML stack |
| ------------- | ------- | --------- |
| **8.0.0** | **8** | **`javax.*`** / EE4J **`jaxws-rt` 2.3.x** at runtime in consumers |
| **11.0.0.1** | **11** | **Jakarta** / EE4J **`jaxws-rt` 4.0.x** at runtime in consumers |
| **17.0.0.1** | **17** | **Jakarta** / EE4J **`jaxws-rt` 4.0.x** at runtime in consumers |
| **21.0.0.1** | **21** | **Jakarta** / EE4J **`jaxws-rt` 4.0.x** at runtime in consumers |
| **24.0.0.1** | **24** | **Jakarta** / EE4J **`jaxws-rt` 4.0.x** at runtime in consumers |

Pick the coordinate that matches your JDK. All published versions are on **[Maven Central](https://central.sonatype.com/)**.

---

## Local development (SNAPSHOT)

This repository builds **`8.0.0-SNAPSHOT`**. Compile depends on **`au.gov.nehta:smi-xsp`** at **`${project.version}`** (**8.0.0** / **`8.0.0-SNAPSHOT`**). Install unpublished **`smi-xsp`** first when that coordinate is not on Central, then install this library:

```text
# smi-xsp-java (same Maven version as this pom.xml)
mvn -B "-Dgpg.skip=true" clean install

# common-library-java
mvn -B "-Dgpg.skip=true" clean install
```

If Maven warns that a **GA** POM is missing, clear stale **`au/gov/nehta/common-library`** or **`au/gov/nehta/smi-xsp`** entries in your local Maven repository (folders with only **`.lastUpdated`** files) and reinstall the SNAPSHOT.

## Building from source

**Audience:** contributors changing this repository - not integrators adding a Maven dependency.

Prerequisites: **JDK 8+**, **Maven 3.6+**.

```text
mvn -B "-Dgpg.skip=true" clean verify
```

See **`CONTRIBUTING.md`** for **`mvn install`** when testing unpublished snapshots locally.

## Related repositories

| Repository | Role |
| ---------- | ---- |
| [hi-b2b-client-java](https://github.com/AuDigitalHealth/hi-b2b-client-java) | HI facade clients (depends on this artifact) |
| [mhr-b2b-client-java](https://github.com/AuDigitalHealth/mhr-b2b-client-java) | MHR facades (depends on this artifact) |

## Documentation

| Document | Audience |
| -------- | -------- |
| **README.md** (this file) | Integrators |
| **CONTRIBUTING.md** | Contributors |
| **MAINTAINERS.md** | Releases and tooling |
| **SECURITY.md** | Secrets and credentials |
| **CHANGELOG.md** | Release history |
| **LICENSE.txt** | Apache License 2.0 + ADHA terms |

## License

Apache License 2.0. See **LICENSE.txt**.

## Copyright

Copyright 2012 NEHTA. Copyright 2021-2026 ADHA. Apache License 2.0 - see **LICENSE.txt**.
