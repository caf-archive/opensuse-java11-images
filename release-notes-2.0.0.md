
#### Version Number
${version-number}

#### New Features
- **SCMOD-8481** - Disabled weaker SSL algorithms.  
This will help to prevent against vulnerabilities, for example [Logjam](https://en.wikipedia.org/wiki/Logjam_(computer_security))

#### Known Issues
- None

#### Breaking Changes
- **SCMOD-8481** - Disabled weaker SSL algorithms.  
A number of weaker SSL algorithms have been disabled, you can find the list of disabled algorithms [here](src/main/docker/disableWeakTlsAlgorithms.patch).
