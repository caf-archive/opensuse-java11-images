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

FROM cafapi/opensuse-tini:1.0

# Update the OS packages
RUN zypper -n refresh && \
    zypper -n update && \
    zypper -n install wget fontconfig libX11.so.6 libXext.so.6 libXi.so.6 libXrender.so.1 libXtst.so.6 libasound.so.2 libgif.so.6 \
        libjpeg.so.8 libjvm.so libpng16.so.16 libpulse.so.0 mozilla-nss jpackage-utils liblcms2.so.2

# Install Java certificate installation script
ADD https://raw.githubusercontent.com/CAFapi/caf-common/v1.14.0/container-cert-script/install-ca-cert-java.sh \
    /startup/startup.d/
RUN chmod +x /startup/startup.d/install-ca-cert-java.sh

RUN wget https://download.opensuse.org/repositories/Java:/Factory/openSUSE_Leap_42.3/x86_64/java-9-openjdk-headless-9.0.4.0-125.1.x86_64.rpm
RUN rpm -ivh --nodeps java-9-openjdk-headless-9.0.4.0-125.1.x86_64.rpm

RUN wget https://download.opensuse.org/repositories/Java:/Factory/openSUSE_Leap_42.3/x86_64/java-9-openjdk-9.0.4.0-125.1.x86_64.rpm
RUN rpm -ivh --nodeps java-9-openjdk-9.0.4.0-125.1.x86_64.rpm

RUN rm java-9-openjdk-headless-9.0.4.0-125.1.x86_64.rpm java-9-openjdk-9.0.4.0-125.1.x86_64.rpm

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
