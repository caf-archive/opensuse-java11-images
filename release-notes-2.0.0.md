
#### Version Number
${version-number}

#### New Features
- **SCMOD-8481** - TLS/SSL cipher hardening  
Weaker TLS algorithms have been disabled to help to protect against vulnerabilities such as [Logjam](https://en.wikipedia.org/wiki/Logjam_(computer_security)).

#### Known Issues
- None

#### Breaking Changes
- **SCMOD-8481** - TLS/SSL cipher hardening.  
Weaker TLS algorithms are no longer supported by default.  See [here](src/main/docker/disableWeakTlsAlgorithms.patch) to view the list of algorithms which have been disabled.
