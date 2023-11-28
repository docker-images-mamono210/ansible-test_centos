FROM quay.io/centos/centos:stream9

# Install requirements
RUN dnf clean all \
  && dnf update -y \
  && dnf install -y sudo \
  && dnf -y install systemd

# Create `ansible` user with sudo permissions
ENV ANSIBLE_USER=circleci SUDO_GROUP=wheel
RUN set -xe \
  && groupadd -r ${ANSIBLE_USER} \
  && useradd -m -g ${ANSIBLE_USER} ${ANSIBLE_USER} \
  && usermod -aG ${SUDO_GROUP} ${ANSIBLE_USER} \
  && sed -i "/^%${SUDO_GROUP}/s/ALL\$/NOPASSWD:ALL/g" /etc/sudoers
