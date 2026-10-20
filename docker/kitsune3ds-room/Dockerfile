# This Dockerfile assumes that it is being built from the project root directory, e.g.:
# $ docker build -f docker/kitsune3ds-room/Dockerfile -t kitsune3ds-room .

# --- Builder ----------------
FROM opensauce04/azahar-build-environment:latest AS builder

RUN mkdir /var/kitsune3ds-src/
COPY ./ /var/kitsune3ds-src/

RUN mkdir ./builddir/
WORKDIR ./builddir/
RUN cmake /var/kitsune3ds-src -G Ninja \
                          -DENABLE_QT=OFF \
                          -DENABLE_GDBSTUB=OFF \
                          -DENABLE_TESTS=OFF \
                          -DENABLE_ROOM=ON \
                          -DENABLE_ROOM_STANDALONE=ON
RUN ninja
RUN mv ./bin/Release/kitsune3ds-room /usr/local/bin/

# --- Final ------------------
FROM debian:trixie AS final

RUN apt-get update && apt-get -y full-upgrade
RUN apt-get install -y iputils-ping net-tools

COPY --from=builder /usr/local/bin/kitsune3ds-room /usr/local/bin/kitsune3ds-room
