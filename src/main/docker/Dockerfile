#
# Copyright 2015-2017 EntIT Software LLC, a Micro Focus company.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

#
# Preliminary image that install java9 prerequisites
#
FROM cafapi/opensuse-tini:1.0 AS builder

RUN export JAVA_HOME=/usr/lib64/jvm/jre-1.8.0-openjdk && \
    export PATH=$JAVA_HOME/bin:$PATH && \
    export OBF_JAVA8_HOME=/usr/lib64/jvm/jre-1.8.0-openjdk

# Update the OS packages and install prerequsites
RUN zypper -n refresh && \
    zypper -n update && \
    zypper -n install git-core mercurial zip bzip2 unzip tar && \
    zypper -n install ccache make gcc gcc-c++ ca-certificates-cacert ca-certificates-mozilla && \
    zypper -n install libstdc++-devel alsa-devel cups-devel xorg-x11-devel libjpeg62-devel giflib-devel && \
    zypper -n install rpm-build gpg && \
    zypper -n install java-1_8_0-openjdk-devel

# Prepare environemt for openjdk9 build
RUN mkdir ~/openjdkathome && \
    cd ~/openjdkathome && \
    git clone https://github.com/hgomez/obuildfactory.git

# Build openjdk9 rpm package
RUN cd ~/openjdkathome && \
    XPACKAGE=true XCLEAN=true XUSE_NEW_BUILD_SYSTEM=true XBUILD=true ./obuildfactory/openjdk9/linux/standalone-job.sh

#
# The actual image definition
#
FROM cafapi/opensuse-tini:1.0

# Update the OS packages
RUN zypper -n refresh && \
    zypper -n update

# Install Java certificate installation script
ADD https://raw.githubusercontent.com/CAFapi/caf-common/v1.14.0/container-cert-script/install-ca-cert-java.sh \
    /startup/startup.d/
RUN chmod +x /startup/startup.d/install-ca-cert-java.sh

# Install openjdk9
COPY --from=builder OBF_DROP_DIR/openjdk9/ /usr/lib64/jvm/jre-1.9.0-openjdk/

ADD /usr/lib64/jvm/jre-1.9.0-openjdk/openjdk9_1.9.0-b94_amd64.rpm /openjdk9_1.9.0-b94_amd64.rpm
RUN rpm -i openjdk9_1.9.0-b94_amd64.rpm

# Tag the image
ARG BUILD_NUMBER
ARG BUILD_DATE
ARG GIT_REPO
ARG GIT_BRANCH
ARG GIT_COMMIT

LABEL Build.Number="$BUILD_NUMBER" \
      Build.Date="$BUILD_DATE" \
      Git.Repo="$GIT_REPO" \
      Git.Branch="$GIT_BRANCH" \
      Git.Commit="$GIT_COMMIT"
