# Maintainer notes

**Audience:** people changing the **`common-library`** build, source, or release process - not library integrators. Integrators should use **README.md**, published Javadoc, and **`pom.xml`** coordinates.

Paths are relative to the repository root (directory containing **`pom.xml`**).

## Versioning

The **first number** of **`<version>`** is the **Java SE** target of **this** library.

| Maven version | Java SE |
| ------------- | ------- |
| **8.0.0**     | **8**   |
| **11.0.0**    | **11**  |
| **17.0.0**    | **17**  |
| **21.0.0.1**  | **21**  |
| **24.0.0.1**  | **24**  |

**Documentation convention:** README, CONTRIBUTING, CHANGELOG, and integrator-facing text use **version numbers only** - never Git branch names.

| Version      | Java | XML APIs                                                        |
| ------------ | ---- | --------------------------------------------------------------- |
| **8.0.0**    | 8    | **`javax.xml.ws`**, **`javax.xml.bind`** (via `jaxws-rt` 2.3.7) |
| **11.0.0**   | 11   | **Jakarta** XML WS / Bind                                       |
| **17.0.0**   | 17   | **Jakarta** XML WS / Bind                                       |
| **21.0.0.1** | 21   | **Jakarta** XML WS / Bind                                       |
| **24.0.0.1** | 24   | **Jakarta** XML WS / Bind                                       |

**Git branch mapping (maintainers / checkout only - do not use in integrator docs):**

| Version      | Official Git branch |
| ------------ | ------------------- |
| **8.0.0**    | `java-8`            |
| **11.0.0**   | `java-11`           |
| **17.0.0**   | `java-17`           |
| **21.0.0.1** | `java-21`           |
| **24.0.0.1** | `java-24`           |

Artifact id stays **`common-library`**; the version distinguishes the Java SE line.

On a given branch, **do not change the first number** of **`<version>`**. Next GA on **`java-17`** is **`17.0.0.1`** (then **`17.0.1-SNAPSHOT`**), not a different first number. A new Java SE target is a **new branch**, not a bump on this one.

**This checkout (`17.0.0-SNAPSHOT`):** Java **17**, **Jakarta** XML APIs, **`jaxws-rt` 4.0.5**.

## Artifact

- **`au.gov.nehta:common-library`** - shared utility classes for CDA package operations, argument validation, and web-service helpers used by other ADHA/NEHTA libraries.

## Contributors vs release publisher (`pom.xml`)

**Contributors (PRs, ordinary commits):** Do not change **`<version>`** (stay on **`-SNAPSHOT`** unless the maintainer requests a bump), **`<scm><tag>`**, or **`distributionManagement`**. Leave **`maven-gpg-plugin`** **`skip`** **`true`** so default **`mvn verify`** does not require a signing key. Record user-visible work under **`CHANGELOG.md`** in the **`= <pom-version> =`** block that matches **`pom.xml`** **`<version>`**.

**Release publisher:** In the release change set: set **`<version>`** to the GA coordinate (no **`-SNAPSHOT`**); set **`<scm><tag>`** to the Git tag you will publish. Move **`CHANGELOG.md`** bullets from the snapshot section into a new **`= <GA-version> =`** section; add a fresh **`-SNAPSHOT`** block for the next development cycle. Deploy via Sonatype Central Portal (**`central-publishing-maven-plugin`**; copy **`settings.xml.example`** -> **`settings.xml`**, server id **`central`**). See **Release** below.

## Release

Publishing uses **`central-publishing-maven-plugin`** (Sonatype Central Portal). Copy **`settings.xml.example`** -> **`settings.xml`**, server id **`central`**.

| Branch        | Java         | `common-library` |
| ------------- | ------------ | ---------------- |
| **`java-8`**  | 8 / javax    | **8.0.0**        |
| **`java-11`** | 11 / Jakarta | **11.0.0**       |
| **`java-17`** | 17 / Jakarta | **17.0.0**       |
| **`java-21`** | 21 / Jakarta | **21.0.0.1**     |
| **`java-24`** | 24 / Jakarta | **24.0.0.1**     |

**`-DdevelopmentVersion`:** keep the same first number as **`-DreleaseVersion`** (example on this line: **`17.0.0`** then **`17.0.1-SNAPSHOT`**).

### SNAPSHOT or manual GA

1. Update **CHANGELOG.md** (and **`pom.xml`** / SCM **`<tag>`** for manual GA).
2. **`mvn -B "-Prelease" clean verify`**
3. **`mvn -B "-Prelease" deploy`**

Tags default to **`{artifactId}-{version}`** (e.g. **`common-library-17.0.0`**).

### Automated GA (`maven-release-plugin`)

Run on the **target branch** with a **clean** working tree.

```text
mvn -B "-Prelease" release:prepare release:perform -DreleaseVersion=17.0.0 -DdevelopmentVersion=17.0.1-SNAPSHOT -Dtag=common-library-17.0.0
```

**After success:** confirm **`common-library`** GA on Central before cutting downstream GAs.

## Changelog and releases

**`CHANGELOG.md`** uses **`= version =`** section headers. Match the snapshot header to **`pom.xml`** **`<version>`** until the publisher cuts GA.

## New Java SE line

When adding a line (e.g. Java **25**): create **`java-25`** in **this** repository from the nearest existing line; set **`<version>`** first number to **25** (e.g. **`25.0.0.1-SNAPSHOT`**); set **`maven.compiler.release`**, Jakarta coordinates, CI **`java-version`** / branch filter, and docs to that line. Do not retarget an existing branch.

## Build (`17.0.0` line)

- **`maven.compiler.release` 17**
- Runtime SOAP stack: **`com.sun.xml.ws:jaxws-rt` 4.0.5** in **consuming** applications
- Sibling **`au.gov.nehta:smi-common-utils`** and **`au.gov.nehta:smi-xsp`**: **`${project.version}`**
- **`maven-gpg-plugin`:** skipped unless **`-Dgpg.skip=false`**

## Copyright

Copyright 2011 NEHTA. Copyright 2021-2026 ADHA. Apache License 2.0 - see **LICENSE.txt**.
