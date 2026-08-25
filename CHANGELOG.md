# Change Log/Revision History

# = 11.0.0 =

- Maven **`au.gov.nehta:common-library`** **11.0.0** (Java **11** / **Jakarta**).
- POM: Jakarta XML APIs, **`jaxws-rt` 4.0.5**; declare bind/ws/soap APIs used by sources.
- **`smi-xsp`** at **`nehta.xsp.lib.version`** = **`${project.version}`** (**11.0.0**).
- `TimeUtility` uses `java.time` (`DateTimeFormatter` / `LocalDateTime`) instead of `SimpleDateFormat`.
- Drop unused test-only `xmlsec` / `slf4j` declarations (arrive via `smi-xsp` / runtime as needed).

# = 1.2.3-SNAPSHOT =

- Updated pom and deployed.

# = 1.1.1 =

- Converted to Maven.
- Changed dependencies to use Maven references.

# = 1.1.0 =

- Updated the supplied nehta-smi-xsp library to the 1.2.0 version which supports Java 1.7_21+.
- Deprecated use of `verifySignature(Document,CertificateVerifier)` in favour of `verifySignature(Document,CertificateValidator)`.
- Changed Logging handler implementation to avoid XML transformations.

# = 1.0.4 =

- Modified WebServiceClient to add both com.sun.xml and com.sun.xml.internal binding for SSL factory.
