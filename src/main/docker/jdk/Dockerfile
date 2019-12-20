#
# Copyright 2017-2020 Micro Focus or one of its affiliates.
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

FROM cafapi/opensuse-base:1

# Update the OS packages
RUN zypper -n refresh

# Install Java certificate installation script
ADD https://raw.githubusercontent.com/CAFapi/caf-common/v1.14.0/container-cert-script/install-ca-cert-java.sh \
    /startup/startup.d/
RUN chmod +x /startup/startup.d/install-ca-cert-java.sh

# Install OpenJDK 11 Development Kit
RUN zypper -n install java-11-openjdk-devel

# Set Java Home
ENV JAVA_HOME=/usr/lib64/jvm/java-11-openjdk-11

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
