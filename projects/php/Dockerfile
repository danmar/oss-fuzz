# Copyright 2019 Google Inc.
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
################################################################################

FROM gcr.io/oss-fuzz-base/base-builder
MAINTAINER stas@php.net
RUN apt-get update && apt-get install -y make autoconf automake libtool bison re2c make ca-certificates curl \
	xz-utils dpkg-dev file libc-dev pkg-config libcurl4-openssl-dev libedit-dev libsqlite3-dev libssl-dev \
	zlib1g-dev libonig-dev chrpath
RUN git clone --depth 1 --branch master https://github.com/php/php-src.git php-src
RUN git clone --depth 1 https://github.com/php/php-fuzzing-sapi.git php-src/sapi/fuzzer
WORKDIR php-src
COPY build.sh *.options $SRC/
# This ideally will be gone eventually, right now used for more flexibility in tweaking Makefile options
# COPY Makefile.frag $SRC/php-src/sapi/fuzzer
