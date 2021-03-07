FROM registry.fedoraproject.org/fedora-toolbox:32

ENV NAME=devenv-fedora-toolbox VERSION=32
LABEL name="$NAME"                                               \
      version="$VERSION"                                              \
      usage="This image is meant to be used with the toolbox command" \
      summary="Developer environment toolbox image"                   \
      maintainer="Stefano Figura <stefano@figura.im>"

COPY extra-packages /
RUN dnf -y upgrade                       \
    && dnf -y install $(<extra-packages) \
    && rm /extra-packages                \
    && dnf clean all
