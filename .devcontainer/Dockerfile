FROM debian:stable

ARG DEBIAN_FRONTEND=noninteractive# Install Utils

WORKDIR /tmp
RUN \
apt-get update && \
apt-get install -y git curl make rlwrap wget xz-utils

# Install JAVA
ENV JAVA_VERSION=17
RUN apt-get install -y openjdk-$JAVA_VERSION-jdk

# Install Clojure - see https://github.com/Quantisan/docker-clojure/blob/master/target/openjdk-14-slim-buster/tools-deps/Dockerfile
ENV CLOJURE_VERSION=1.10.3.1087
RUN \
wget https://download.clojure.org/install/linux-install-$CLOJURE_VERSION.sh && \
chmod +x linux-install-$CLOJURE_VERSION.sh && \
./linux-install-$CLOJURE_VERSION.sh
RUN rm ./linux-install-$CLOJURE_VERSION.sh

# Install Lein
RUN \
wget https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein -O /bin/lein && \
chmod uog+x /bin/lein

# Install Nodejs
ENV NODE_VERSION=16.14.2
RUN \
wget https://nodejs.org/dist/v16.14.2/node-v$NODE_VERSION-linux-x64.tar.xz && \
tar -xvf node-v$NODE_VERSION-linux-x64.tar.xz && \
cp -r node-v$NODE_VERSION-linux-x64/bin /usr/ && \
cp -r node-v$NODE_VERSION-linux-x64/include /usr/ && \
cp -r node-v$NODE_VERSION-linux-x64/lib /usr/ && \
cp -r node-v$NODE_VERSION-linux-x64/share /usr/ && \
rm -rf node-v$NODE_VERSION-linux-x64

# Install Babashka
RUN wget https://raw.githubusercontent.com/babashka/babashka/master/install && \
bash install

