# Change Log/Revision History

= 8.0.0.1 =
=======
- Maven **`au.gov.nehta:common-library`** **8.0.0.1** (Java **8** / **`javax`**). The first number of the Maven version is the targeted Java SE version.
- POM: Eclipse EE4J stack alignment - **`jaxws-rt` 2.3.7**; **`maven-enforcer-plugin`** bans legacy Metro **`webservices-*`** bundles.
- Build plugins and dependency versions updated to latest Java **8**-compatible releases.
- Version aligned with the HI/MHR client release lines (`8.0.0.1`).

= 1.2.3-SNAPSHOT =
=======
- Updated pom and deployed.

= 1.1.1 =
=========
- Converted to Maven.
- Changed dependencies to use Maven references.

= 1.1.0 =
=========
- Updated the supplied nehta-smi-xsp library to the 1.2.0 version which supports Java 1.7_21+.
- Deprecated use of `verifySignature(Document,CertificateVerifier)` in favour of `verifySignature(Document,CertificateValidator)`.
- Changed Logging handler implementation to avoid XML transformations.

= 1.0.4 =
=========
- Modified WebServiceClient to add both com.sun.xml and com.sun.xml.internal binding for SSL factory.

## Copyright

Copyright 2012 NEHTA. Copyright 2021-2026 ADHA. Apache License 2.0 - see **LICENSE.txt**.
