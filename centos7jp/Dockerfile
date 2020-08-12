FROM centos:7

# Install requirements
RUN yum clean all \
  && yum update -y \
  && yum install -y sudo

# Install Japanese locale settings
RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8

# Create `ansible` user with sudo permissions
ENV ANSIBLE_USER=ansible SUDO_GROUP=wheel
RUN set -xe \
  && groupadd -r ${ANSIBLE_USER} \
  && useradd -m -g ${ANSIBLE_USER} ${ANSIBLE_USER} \
  && usermod -aG ${SUDO_GROUP} ${ANSIBLE_USER} \
  && sed -i "/^%${SUDO_GROUP}/s/ALL\$/NOPASSWD:ALL/g" /etc/sudoers
