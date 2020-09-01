FROM registry.fedoraproject.org/f33/fedora-toolbox

ENV NAME=devenv-fedora-toolbox VERSION=33
LABEL name="$FGC/$NAME"                                               \
      version="$VERSION"                                              \
      usage="This image is meant to be used with the toolbox command" \
      summary="Developer environment toolbox image"                   \
      maintainer="Stefano Figura <stefano@figura.im>"

COPY extra-packages /
RUN dnf clean all                        \
    && dnf -y upgrade                    \
    && dnf -y install $(<extra-packages) \
    && rm /extra-packages                \
    && dnf clean all
