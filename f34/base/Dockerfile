FROM registry.fedoraproject.org/f34/fedora-toolbox:34

ENV NAME=base-fedora-toolbox VERSION=34
LABEL name="$FGC/$NAME"                                                     \
      version="$VERSION"                                                    \
      usage="This image is meant to be used with the toolbox command"       \
      summary="Base system toolbox image. Use to install system wide tools" \
      maintainer="Stefano Figura <stefano@figura.im>"

COPY extra-packages /
RUN dnf -y upgrade                                                                                                    \
    && dnf -y install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
    https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm             \
    && dnf -y install $(<extra-packages)                                                                              \
    && rm /extra-packages                                                                                             \
    && dnf clean all
