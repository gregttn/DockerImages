FROM ubuntu:15.10

RUN apt-get update -y
RUN apt-get install -y clang libicu-dev libpython2.7 libxml2 wget
# install extra tools
RUN apt-get install -y vim git curl screen 
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN wget -q -O - https://swift.org/keys/all-keys.asc | gpg --import - && \
    gpg --keyserver hkp://pool.sks-keyservers.net --refresh-keys Swift

ENV SWIFT_ARCHIVE=swift-2.2-RELEASE-ubuntu15.10
ENV SWIFT_URL=https://swift.org/builds/swift-2.2-release/ubuntu1510/swift-2.2-RELEASE/$SWIFT_ARCHIVE.tar.gz
ENV SWIFT_SIGNATURE=$SWIFT_URL.sig

# install Swift
RUN wget $SWIFT_URL && \
    wget $SWIFT_SIGNATURE && \
    gpg --verify $SWIFT_ARCHIVE.tar.gz.sig && \
    tar -xvzf $SWIFT_ARCHIVE.tar.gz -C / --strip 1 && \
    rm -rf $SWIFT_ARCHIVE* /tmp/* /var/tmp/*