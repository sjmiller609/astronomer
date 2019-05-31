#
# Copyright 2019 Astronomer Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM test_debian_reg:latest
LABEL maintainer="Astronomer <humans@astronomer.io>"

ARG BUILD_NUMBER=-1
LABEL io.astronomer.docker=true
LABEL io.astronomer.docker.build.number=$BUILD_NUMBER
LABEL io.astronomer.docker.airflow.onbuild=true

ONBUILD COPY packages.txt .
ONBUILD RUN sudo cat packages.txt | xargs sudo apt-get install -y --no-install-recommends
# Install python packages
ONBUILD COPY requirements.txt .
ONBUILD RUN sudo pip install --no-cache-dir -q -r requirements.txt
# Copy entire project directory
ONBUILD COPY . .
USER 100
