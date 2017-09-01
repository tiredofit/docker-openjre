FROM tiredofit/alpine:3.6
MAINTAINER Dave Conroy <daveconroy@selfdesign.org>

ENV LANG=C.UTF-8 \
    JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk/jre \
    PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/jre/bin:/usr/lib/jvm/java-1.8-openjdk/bin \
    JAVA_VERSION=8u131 \
    JAVA_ALPINE_VERSION=8.131.11-r2

# add a simple script that can auto-detect the appropriate JAVA_HOME value
# based on whether the JDK or only the JRE is installed
   RUN echo '#!/bin/sh'; >> /usr/local/bin/docker-java-home && \
       echo 'set -e'; >> /usr/local/bin/docker-java-home && \
       echo '' >> /usr/local/bin/docker-java-home && \
       echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"' >> /usr/local/bin/docker-java-home && \
       chmod +x /usr/local/bin/docker-java-home && \

       set -x && \
       apk add --no-cache \
	   openjdk8-jre="$JAVA_ALPINE_VERSION" && \
       [ "$JAVA_HOME" = "$(docker-java-home)" ]

