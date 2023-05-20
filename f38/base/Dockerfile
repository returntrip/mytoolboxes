FROM registry.fedoraproject.org/fedora-toolbox:38

ENV NAME=base-fedora-toolbox VERSION=38
LABEL name="$NAME"                                                          \
      version="$VERSION"                                                    \
      usage="This image is meant to be used with the toolbox command"       \
      summary="Base system toolbox image. Use to install system wide tools" \
      maintainer="Stefano Figura <stefano@figura.im>"

COPY extra-packages /
RUN dnf -y upgrade                                                                                                    \
    && dnf copr enable -y atim/starship                                                                               \
    && dnf -y install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
    https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm             \
    && dnf -y install $(<extra-packages)                                                                              \
    && rm /extra-packages                                                                                             \
    && dnf clean all
