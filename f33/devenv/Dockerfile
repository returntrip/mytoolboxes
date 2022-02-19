FROM registry.fedoraproject.org/fedora-toolbox:33

ENV NAME=devenv-fedora-toolbox VERSION=33
LABEL name="$NAME"                                                    \
      version="$VERSION"                                              \
      usage="This image is meant to be used with the toolbox command" \
      summary="Developer environment toolbox image"                   \
      maintainer="Stefano Figura <stefano@figura.im>"

COPY extra-packages /
RUN dnf -y upgrade                       \
    && dnf copr enable -y atim/starship  \
    && dnf -y install $(<extra-packages) \
    && rm /extra-packages                \
    && dnf clean all
