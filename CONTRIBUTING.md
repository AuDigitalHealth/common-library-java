# Contributing

**Audience:** developers building or changing **this repository**. Integrators should use **README.md** and Maven Central coordinates. See **SECURITY.md** before committing.

## Prerequisites

- **JDK 8+** with **`JAVA_HOME`** set (see **`maven.compiler.release`** in **`pom.xml`**).
- **Maven 3.6+** on **`PATH`**.

Dependencies resolve from **[Maven Central](https://central.sonatype.com/)** unless you are installing a **local SNAPSHOT** (below). This POM has no sibling Maven modules.

## Versioning

The **first number** of **`au.gov.nehta:common-library`** is the **Java SE** version that this library targets. **8.0.0.1** targets Java **8** / **`javax`**; **11.0.0.1** and later use **Jakarta**. See **`README.md`**.

## Build

From the project root:

```text
mvn -B "-Dgpg.skip=true" clean verify
```

| Goal | Command |
| ---- | ------- |
| Compile + attach sources/Javadoc | `mvn -B "-Dgpg.skip=true" clean verify` |
| Skip tests | `mvn -B "-Dgpg.skip=true" clean verify "-DskipTests=true"` |
| Install SNAPSHOT to the local Maven repository | `mvn -B "-Dgpg.skip=true" clean install` |

GPG signing is skipped by default (**`-Dgpg.skip=true`**). Release builds: **`-Dgpg.skip=false`**.

## Dependencies

- Compile: **`com.sun.xml.ws:jaxws-rt`** **2.3.7**, **`au.gov.nehta:smi-xsp`**.
- Test: **`junit`**, **`org.apache.santuario:xmlsec`**, **`org.slf4j:slf4j-api`** / **`slf4j-simple`**.

## Local builds (unpublished artifacts)

**`mvn install`** makes the SNAPSHOT resolvable for any local consumer of **`au.gov.nehta:common-library`** at **`${project.version}`**. Integrators using GA versions from Maven Central do not need a source checkout.

Maintainer notes: **MAINTAINERS.md**.

## Repository hygiene

- **Do not commit** keystores, production endpoint URLs, populated **`settings.xml`** with release credentials, or generated build artefacts. See **SECURITY.md**.
- **Line endings:** the repository uses **LF** (see **`.gitattributes`** if present). On **Windows**, run **`git config core.autocrlf false`** in your clone before committing.

## Copyright

Copyright 2012 NEHTA. Copyright 2021-2026 ADHA. Apache License 2.0 - see **LICENSE.txt**.
