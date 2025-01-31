# Container Scanning

Scan for known CVEs from online databases.

<!-- INDEX_START -->

- [Open Source](#open-source)
  - [Trivy](#trivy)
  - [Grype](#grype)
  - [Clair](#clair)
- [Proprietary](#proprietary)
  - [Aqua Security](#aqua-security)
  - [Twistlock](#twistlock)
  - [Tenable.io](#tenableio)
  - [CheckMarx](#checkmarx)
- [Container Scanning on Jenkins](#container-scanning-on-jenkins)

<!-- INDEX_END -->

## Open Source

### Trivy

<https://github.com/aquasecurity/trivy>

See [Trivy](trivy.md) doc.

### Grype

<https://github.com/anchore/grype>

### Clair

<https://github.com/coreos/clair>

Open source static analysis image vulnerability scanner by CoreOS.

Not as good quality, easy to use or reliable in my experience,
see [this issue](https://github.com/quay/clair/issues/1756)

See [Clair](clair.md) page.

## Proprietary

### Aqua Security

<https://www.aquasec.com/products/aqua-container-security-platform/>

Container security - wraps docker socket to control + kill container launches

### Twistlock

<https://www.twistlock.com/>

### Tenable.io

Scanner for docker images (company behind Nessus) - one client's tech hub had this. Scans happened 10-40 mins behind
  async because it's slow

<https://docs.tenable.com/vulnerability-management/Content/ContainerSecurity/CSScanner.htm>§

### CheckMarx

<https://checkmarx.com/resource/documents/en/34965-19110-container-scans.html>

## Container Scanning on Jenkins

![](https://raw.githubusercontent.com/nholuongut/Diagrams-as-Code/master/images/jenkins_kubernetes_cicd.svg)

**Ported from various private Knowledge Base pages 2018+**
