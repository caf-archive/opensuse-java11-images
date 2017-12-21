# openSUSE and Java 9 Runtime image

This project builds an openSUSE-based image which includes the OpenJDK 9 Runtime Environment. It can be used as a base image by projects which require Java 9.

### Tini
[Tini](https://github.com/krallin/tini) is pre-installed in the container.  If the image entrypoint is not overwritten then it will be automatically used.

### Startup Scripts
Any executable scripts added to the `/startup/startup.d/` directory will be automatically run each time the container is started (assuming the image entrypoint is not overwritten).

### Certificate Installation
The image comes pre-installed with several startup scripts which provide a mechanism to extend the CA certificates which should be trusted.

**NOTE - this is currently utilising an unstable java-9-openjdk package, therefore this base image is currently only intended to used for testing purposes and is not to be used for production.**
