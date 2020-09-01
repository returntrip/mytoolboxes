FROM registry.fedoraproject.org/34/fedora-toolbox

ENV NAME=base-fedora-toolbox VERSION=34
LABEL name="$FGC/$NAME"                                                     \
      version="$VERSION"                                                    \
      usage="This image is meant to be used with the toolbox command"       \
      summary="Base system toolbox image. Use to install system wide tools" \
      maintainer="Stefano Figura <stefano@figura.im>"

COPY extra-packages /
RUN dnf -y upgrade                                                                                                    \
    && dnf -y install $(<extra-packages)                                                                              \
    && rm /extra-packages                                                                                             \
    && dnf clean all
