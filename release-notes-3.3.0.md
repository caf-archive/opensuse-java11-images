!not-ready-for-release!

#### Version Number
${version-number}

#### New Features
- SCMOD-11949: The [gosu](https://github.com/tianon/gosu/) tool is now available in the base image.  
  This tool allows derived images to run commands as a specified user, rather than as the default user.  
  See the [README.md](https://github.com/CAFapi/opensuse-java11-images/blob/develop/README.md) for more details.
- SCMOD-12885: Allowed some TLS algorithms to meet the [Mozilla](https://wiki.mozilla.org/Security/Server_Side_TLS) Intermediate level.  
  The newly allowed algorithms are `TLS_DHE_RSA_WITH_AES_128_GCM_SHA256` and `TLS_DHE_RSA_WITH_AES_256_GCM_SHA384`.
  
#### Known Issues
- None
