#### Version Number
${version-number}

#### New Features
- **SCMOD-8516**: Extend the TLS/SSL cipher hardening of the Java base images to disallow TLSv1.1 and TLSv1.2

#### Known Issues

#### Breaking Changes
- **SCMOD-8516**: Extend the TLS/SSL cipher hardening of the Java base images to disallow TLSv1.1 and TLSv1.2  
Weaker TLS algorithms are no longer supported by default.  See [here](src/main/docker/disableWeakTlsAlgorithms.patch) to view the list of algorithms which have been disabled.
- **SCMOD-7700**:  Stops the docker container if the execution of any of the startup scripts fail instead of ignoring it.
